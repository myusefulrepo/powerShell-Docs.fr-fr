---
ms.date: 08/14/2018
keywords: powershell,applet de commande
title: Aide sur la ligne de commande PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401359"
---
# <a name="powershellexe-command-line-help"></a>Aide sur la ligne de commande PowerShell.exe

Vous pouvez utiliser PowerShell.exe pour démarrer une session PowerShell à partir de la ligne de commande d’un autre outil, tel que Cmd.exe, ou l’utiliser dans la ligne de commande PowerShell pour démarrer une nouvelle session. Utilisez les paramètres pour personnaliser la session.

## <a name="syntax"></a>Syntaxe

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>Paramètres

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Accepte une version de chaîne codée en base 64 d’une commande. Utilisez ce paramètre pour envoyer à PowerShell des commandes qui nécessitent des guillemets ou des accolades complexes.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Définit la stratégie d’exécution par défaut pour la session actuelle et l’enregistre dans la variable d’environnement $env:PSExecutionPolicyPreference. Ce paramètre ne modifie pas la stratégie d’exécution PowerShell qui est définie dans le Registre. Pour plus d’informations sur les stratégies d’exécution PowerShell, notamment une liste de valeurs valides, consultez [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]

Exécute le script spécifié dans l’étendue locale (avec « dot-sourcing »), afin que les fonctions et variables créées par le script soient disponibles dans la session active. Entrez le chemin d’accès au fichier de script et les paramètres éventuels. **File** doit être le dernier paramètre dans la commande. Toutes les valeurs saisies après le paramètre **-File** sont interprétées comme les paramètres et le chemin d’accès au fichier de script passés à ce script.

Les paramètres passés au script sont passés comme chaînes littérales (après l’interprétation de l’interpréteur de commandes actuel). Par exemple, si vous êtes dans cmd.exe et que vous souhaitez passer une valeur de variable d’environnement, vous utiliseriez la syntaxe de cmd.exe : `powershell.exe -File .\test.ps1 -TestParam %windir%`

En revanche, en cours d’exécution `powershell.exe -File .\test.ps1 -TestParam $env:windir` dans les résultats de cmd.exe dans le script reçoit la chaîne littérale `$env:windir` , car il n’a aucune signification spéciale à l’interpréteur de commandes cmd.exe actuel.
Le `$env:windir` style de référence de variable d’environnement _pouvez_ utilisables dans un `-Command` paramètre, dans la mesure où il elle sera interprétée en tant que code PowerShell.

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}

Décrit le format des données envoyées à PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

### <a name="-mta"></a>-Mta

Démarre PowerShell à l’aide d’un cloisonnement multithread. Ce paramètre est introduit dans PowerShell 3.0. Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA). Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).

### <a name="-noexit"></a>-NoExit

Ne quitte pas après l’exécution de commandes de démarrage.

### <a name="-nologo"></a>-Nologo

Masque la bannière de copyright au démarrage.

### <a name="-noninteractive"></a>-NonInteractive

Ne présente pas d’invite interactive à l’utilisateur.

### <a name="-noprofile"></a>-NoProfile

Ne charge pas le profil PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Détermine la mise en forme de la sortie de PowerShell. Les valeurs valides sont « Text » (chaînes de texte) ou « XML » (format CLIXML sérialisé).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Charge le fichier de console PowerShell spécifié. Entrez le chemin d’accès et le nom du fichier de console. Pour créer un fichier de console, utilisez la cmdlet [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) dans PowerShell.

### <a name="-sta"></a>-Sta

Démarre PowerShell à l’aide d’un cloisonnement monothread. Dans PowerShell 3.0, le cloisonnement par défaut est monothread (STA). Dans PowerShell 2.0, le cloisonnement par défaut est multithread (MTA).

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

Démarre la version spécifiée de PowerShell. La version que vous spécifiez doit être installée sur le système. Si PowerShell 3.0 est installé sur l’ordinateur, les valeurs valides sont « 2.0 » et « 3.0 ». La valeur par défaut est « 3.0 ».

Si PowerShell 3.0 n’est pas installé, la seule valeur valide est « 2.0 ». Les autres valeurs sont ignorées.

Pour plus d’informations, voir [Installation de Windows PowerShell](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Définit le style de fenêtre pour la session. Les valeurs valides sont Normal, Hidden, Minimized et Maximized.

### <a name="-command"></a>-Command

Exécute les commandes spécifiées (et les paramètres éventuels) comme si elles étaient tapées à l’invite de commandes PowerShell.
Après l’exécution, PowerShell s’arrête, sauf si le **NoExit** est précisé.
Tout texte qui suit `-Command` est envoyé en tant qu’une seule ligne de commande à PowerShell.
Cela diffère de la façon dont `-File` gère les paramètres envoyés à un script.

La valeur de `-Command` peut être «- », une chaîne ou un bloc de script.
Les résultats de la commande sont retournés à l’interpréteur de commandes parent en tant qu’objets XML désérialisés, objets pas actifs.

Si la valeur de `-Command` est «- », le texte de commande est lu à partir de l’entrée standard.

Lorsque la valeur de `-Command` est une chaîne, **commande** _doit_ être le dernier paramètre spécifié, car les caractères tapés après la commande sont interprétés comme des arguments de commande.

Le **commande** paramètre accepte uniquement un bloc de script pour l’exécution lorsqu’il peut reconnaître la valeur passée à `-Command` comme un type de bloc de script.
Il s’agit de _uniquement_ possible lors de l’exécution de PowerShell.exe à partir d’un autre hôte de PowerShell.
Un bloc de script littérale entre accolades d’héberger le ScriptBlock type peut être contenu dans une variable, retourné par une expression ou analysé par la commande PowerShell existante `{}`, avant passés aux fonctions PowerShell.exe.

Dans cmd.exe, il n’existe pas comme un bloc de script (ou le type de bloc de script), par conséquent, la valeur passée à **commande** sera _toujours_ être une chaîne.
Vous pouvez écrire un bloc de script à l’intérieur de la chaîne, mais au lieu d’en cours d’exécution qu’il se comporte exactement comme si vous avez tapé à l’invite de PowerShell classique, affichant le contenu du script bloquer arrière pour vous.

Une chaîne passée à `-Command` seront toujours exécutées en tant que PowerShell, par conséquent, les accolades de bloc de script ne sont généralement pas requis en premier lieu lors de l’exécution à partir de cmd.exe.
Pour exécuter un bloc de script inline défini à l’intérieur d’une chaîne, le [opérateur d’appel](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` peut être utilisé :

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

Illustre la syntaxe de powershell.exe. Si vous tapez une commande PowerShell.exe dans PowerShell, faites précéder les paramètres de commande d’un trait d’union (-), et non d’une barre oblique (/). Vous pouvez utiliser un trait d’union ou une barre oblique dans Cmd.exe.

> [!NOTE]
> Remarque de dépannage : Dans PowerShell 2.0, démarrage de certains programmes dans Windows PowerShell console échoue en signalant un LastExitCode de 0xc0000142.

## <a name="examples"></a>EXEMPLES

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```