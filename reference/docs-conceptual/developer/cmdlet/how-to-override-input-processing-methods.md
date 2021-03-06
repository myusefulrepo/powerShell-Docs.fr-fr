---
title: Comment substituer les méthodes de traitement d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364468"
---
# <a name="how-to-override-input-processing-methods"></a>Guide pratique pour remplacer des méthodes de traitement des entrées

Ces exemples montrent comment remplacer les méthodes de traitement d’entrée au sein d’une applet de commande. Ces méthodes sont utilisées pour effectuer les opérations suivantes :

- La méthode [System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) est utilisée pour effectuer des opérations de démarrage à usage unique qui sont valides pour tous les objets traités par l’applet de commande. Le runtime Windows PowerShell appelle cette méthode une seule fois.

- La méthode [System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) est utilisée pour traiter les objets passés à l’applet de commande. Le runtime Windows PowerShell appelle cette méthode pour chaque objet passé à l’applet de commande.

- La méthode [System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) est utilisée pour effectuer des opérations de validation unique. Le runtime Windows PowerShell appelle cette méthode une seule fois.

## <a name="to-override-the-beginprocessing-method"></a>Pour substituer la méthode BeginProcessing

- Déclarez une substitution protégée de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) de commande. BeginProcessing.

La classe suivante affiche un exemple de message. Pour utiliser cette classe, modifiez le verbe et le nom dans l’attribut de l’applet de commande, modifiez le nom de la classe pour refléter le nouveau verbe et le nom, puis ajoutez la fonctionnalité dont vous avez besoin à la substitution de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) de commande. BeginProcessing.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>Pour substituer la méthode ProcessRecord

- Déclarez une substitution protégée de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) de commande. ProcessRecord.

La classe suivante affiche un exemple de message. Pour utiliser cette classe, modifiez le verbe et le nom dans l’attribut de l’applet de commande, modifiez le nom de la classe pour refléter le nouveau verbe et le nom, puis ajoutez la fonctionnalité dont vous avez besoin à la substitution de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) de commande. ProcessRecord.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>Pour substituer la méthode EndProcessing

- Déclarez une substitution protégée de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) de commande. EndProcessing.

La classe suivante imprime un exemple. Pour utiliser cette classe, modifiez le verbe et le nom dans l’attribut de l’applet de commande, modifiez le nom de la classe pour refléter le nouveau verbe et le nom, puis ajoutez la fonctionnalité dont vous avez besoin à la substitution de la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) de commande. EndProcessing.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>Voir aussi

[System. Management. Automation. applet de commande. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. applet de commande. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. applet de commande. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
