---
title: Création d’un InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: c23640b69d1e71a343e2bef2c6b3f8ffe19826d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855685"
---
# <a name="creating-an-initialsessionstate"></a>Création d’un InitialSessionState

Commandes de Windows PowerShell s’exécutent dans une instance d’exécution. Pour héberger Windows PowerShell dans votre application, vous devez créer un [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objet. Chaque instance d’exécution a une [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objet associé. Le [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) spécifie les caractéristiques de l’instance d’exécution, tels que les commandes, les variables et les modules sont disponibles pour cette instance d’exécution.

## <a name="create-a-default-initialsessionstate"></a>Créer une valeur par défaut InitialSessionState

 Le [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)et [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) méthodes peuvent être utilisées. Pour créer [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objets. [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) crée un InitialSessionState avec toutes les commandes intégrées chargé lors de la [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) charge uniquement les commandes nécessaires à l’hôte Windows PowerShell (les commandes à partir du module Microsoft.PowerShell.Core.

 Si vous souhaitez limiter davantage les commandes disponibles dans votre application hôte, vous devez créer une instance d’exécution contrainte. Pour plus d’informations, consultez Création d’une instance d’exécution contrainte.

 Le code suivant montre comment créer un InitialSessionState, affectez-le à une instance d’exécution, ajouter des commandes vers le pipeline dans cette instance d’exécution et appeler les commandes. Pour plus d’informations sur l’ajout et l’appel des commandes, consultez Ajout et l’appel des commandes.

```csharp

namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitailSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
        foreach (PSObject result in ps.Invoke())
        {
          Console.WriteLine("{0,-20}{1}",
                  result.Members["Name"].Value,
                  result.Members["Value"].Value);
        } // End foreach.

        // Close the runspace to free resources.
        rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a>Voir aussi

 [Création d’une instance d’exécution contrainte](./creating-a-constrained-runspace.md)