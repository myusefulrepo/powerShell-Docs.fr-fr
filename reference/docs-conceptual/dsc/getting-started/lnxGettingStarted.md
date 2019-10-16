---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Prendre en main la fonctionnalité DSC (Desired State Configuration) pour Linux
ms.openlocfilehash: 523b91741dba57a98ac6e7ba660a776568af7065
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953886"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="83031-103">Prendre en main la fonctionnalité DSC (Desired State Configuration) pour Linux</span><span class="sxs-lookup"><span data-stu-id="83031-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="83031-104">Cette rubrique explique comment prendre en main la fonctionnalité DSC (Desired State Configuration) PowerShell pour Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="83031-105">Pour obtenir des informations générales sur DSC, consultez [Prendre en main la fonctionnalité DSC (Desired State Configuration) Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="83031-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="83031-106">Versions du système d’exploitation Linux prises en charge</span><span class="sxs-lookup"><span data-stu-id="83031-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="83031-107">Les versions suivantes du système d’exploitation Linux prennent en charge DSC pour Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="83031-108">CentOS 5, 6 et 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="83031-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="83031-109">Debian GNU/Linux 6, 7 et 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="83031-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="83031-110">Oracle Linux 5, 6 et 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="83031-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="83031-111">Red Hat Enterprise Linux Server 5, 6 et 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="83031-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="83031-112">SUSE Linux Enterprise Server 10, 11 et 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="83031-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="83031-113">Ubuntu Server 12.04 LTS, 14.04 LTS et 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="83031-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="83031-114">Le tableau suivant décrit les dépendances de package nécessaires pour utiliser DSC pour Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="83031-115">Package nécessaire</span><span class="sxs-lookup"><span data-stu-id="83031-115">Required package</span></span> |  <span data-ttu-id="83031-116">Description</span><span class="sxs-lookup"><span data-stu-id="83031-116">Description</span></span> |  <span data-ttu-id="83031-117">Version minimale</span><span class="sxs-lookup"><span data-stu-id="83031-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="83031-118">glibc</span><span class="sxs-lookup"><span data-stu-id="83031-118">glibc</span></span>| <span data-ttu-id="83031-119">Bibliothèque GNU</span><span class="sxs-lookup"><span data-stu-id="83031-119">GNU Library</span></span>| <span data-ttu-id="83031-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="83031-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="83031-121">python</span><span class="sxs-lookup"><span data-stu-id="83031-121">python</span></span>| <span data-ttu-id="83031-122">Python</span><span class="sxs-lookup"><span data-stu-id="83031-122">Python</span></span>| <span data-ttu-id="83031-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="83031-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="83031-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="83031-124">omiserver</span></span>| <span data-ttu-id="83031-125">Infrastructure de gestion ouverte</span><span class="sxs-lookup"><span data-stu-id="83031-125">Open Management Infrastructure</span></span>| <span data-ttu-id="83031-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="83031-126">1.0.8.1</span></span>|
| <span data-ttu-id="83031-127">openssl</span><span class="sxs-lookup"><span data-stu-id="83031-127">openssl</span></span>| <span data-ttu-id="83031-128">Bibliothèques OpenSSL</span><span class="sxs-lookup"><span data-stu-id="83031-128">OpenSSL Libraries</span></span>| <span data-ttu-id="83031-129">0.9.8 ou 1.0</span><span class="sxs-lookup"><span data-stu-id="83031-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="83031-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="83031-130">ctypes</span></span>| <span data-ttu-id="83031-131">Bibliothèque CTypes Python</span><span class="sxs-lookup"><span data-stu-id="83031-131">Python CTypes library</span></span>| <span data-ttu-id="83031-132">Identique à la version Python</span><span class="sxs-lookup"><span data-stu-id="83031-132">Must match Python version</span></span>|
| <span data-ttu-id="83031-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="83031-133">libcurl</span></span>| <span data-ttu-id="83031-134">Bibliothèque client http cURL</span><span class="sxs-lookup"><span data-stu-id="83031-134">cURL http client library</span></span>| <span data-ttu-id="83031-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="83031-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="83031-136">Installation de DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="83031-136">Installing DSC for Linux</span></span>

<span data-ttu-id="83031-137">Vous devez installer [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) avant d’installer DSC pour Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="83031-138">Installation d’OMI</span><span class="sxs-lookup"><span data-stu-id="83031-138">Installing OMI</span></span>

<span data-ttu-id="83031-139">DSC pour Linux nécessite le serveur CIM d’Open Management Infrastructure (OMI), version 1.0.8.1 ou ultérieure.</span><span class="sxs-lookup"><span data-stu-id="83031-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="83031-140">Vous pouvez télécharger OMI à partir de The Open Group : [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="83031-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="83031-141">Pour installer OMI, installez le package approprié pour le système Linux (.rpm ou .deb), la version d’OpenSSL (ssl_098 ou ssl_100) et l’architecture (x64/x86) que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="83031-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="83031-142">Les packages RPM sont conçus pour les systèmes CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server et Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="83031-143">Les packages DEB sont conçus pour les systèmes Debian GNU/Linux et Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="83031-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="83031-144">Les packages ssl_098 et les packages ssl_100 sont conçus pour les ordinateurs avec OpenSSL 0.9.8 et les ordinateurs avec OpenSSL 1.0, respectivement.</span><span class="sxs-lookup"><span data-stu-id="83031-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="83031-145">Pour connaître la version d’OpenSSL installée, exécutez la commande `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="83031-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="83031-146">Exécutez la commande suivante pour installer OMI sur un système CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="83031-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="83031-147">Installation de DSC</span><span class="sxs-lookup"><span data-stu-id="83031-147">Installing DSC</span></span>

<span data-ttu-id="83031-148">DSC pour Linux est disponible en téléchargement [ici](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span><span class="sxs-lookup"><span data-stu-id="83031-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="83031-149">Pour installer DSC, installez le package approprié pour le système Linux (.rpm ou .deb), la version d’OpenSSL (ssl_098 ou ssl_100) et l’architecture (x64/x86) que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="83031-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="83031-150">Les packages RPM sont conçus pour les systèmes CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server et Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="83031-151">Les packages DEB sont conçus pour les systèmes Debian GNU/Linux et Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="83031-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="83031-152">Les packages ssl_098 et les packages ssl_100 sont conçus pour les ordinateurs avec OpenSSL 0.9.8 et les ordinateurs avec OpenSSL 1.0, respectivement.</span><span class="sxs-lookup"><span data-stu-id="83031-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="83031-153">Pour connaître la version d’OpenSSL installée, exécutez la commande « openssl version ».</span><span class="sxs-lookup"><span data-stu-id="83031-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="83031-154">Exécutez la commande suivante pour installer DSC sur un système CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="83031-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="83031-155">Utilisation de DSC pour Linux</span><span class="sxs-lookup"><span data-stu-id="83031-155">Using DSC for Linux</span></span>

<span data-ttu-id="83031-156">Les sections suivantes expliquent comment créer et exécuter des configurations DSC sur les ordinateurs Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="83031-157">Création d’un document MOF de configuration</span><span class="sxs-lookup"><span data-stu-id="83031-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="83031-158">Le mot clé Windows PowerShell « Configuration » permet de créer une configuration pour les ordinateurs Linux, tout comme pour les ordinateurs Windows.</span><span class="sxs-lookup"><span data-stu-id="83031-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="83031-159">Suivez les étapes décrites ci-dessous pour créer un document de configuration pour un ordinateur Linux à l’aide de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83031-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="83031-160">Importez le module nx.</span><span class="sxs-lookup"><span data-stu-id="83031-160">Import the nx module.</span></span> <span data-ttu-id="83031-161">Le module nx de Windows PowerShell contient le schéma des ressources intégrées pour DSC pour Linux. Il doit être installé sur votre ordinateur local et importé dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="83031-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="83031-162">Pour installer le module nx, copiez le répertoire du module nx vers `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` ou `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="83031-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="83031-163">Le module nx est inclus dans le package d’installation de DSC pour Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="83031-164">Pour importer le module nx dans votre configuration, utilisez la commande `Import-DSCResource` :</span><span class="sxs-lookup"><span data-stu-id="83031-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="83031-165">Définissez une configuration et créez le document de configuration :</span><span class="sxs-lookup"><span data-stu-id="83031-165">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="83031-166">Transmission de la configuration en mode Push à l’ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="83031-167">Vous pouvez effectuer une transmission Push des documents de configuration (fichiers MOF) vers l’ordinateur Linux à l’aide de l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="83031-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="83031-168">Pour utiliser cette applet de commande avec les applets de commande [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) ou [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) à distance sur un ordinateur Linux, vous devez utiliser une session CIMSession.</span><span class="sxs-lookup"><span data-stu-id="83031-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="83031-169">L’applet de commande [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) permet de créer une session CIMSession sur l’ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="83031-170">Le code suivant crée une session CIMSession pour DSC pour Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> <span data-ttu-id="83031-171">En mode « Push », les informations d’identification de l’utilisateur doivent correspondre à l’utilisateur racine sur l’ordinateur Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-171">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="83031-172">Seules les connexions SSL/TLS sont prises en charge pour DSC pour Linux. L’applet de commande `New-CimSession` doit être utilisée avec le paramètre –UseSSL défini sur $true.</span><span class="sxs-lookup"><span data-stu-id="83031-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="83031-173">Le certificat SSL utilisé par OMI (pour DSC) est spécifié dans le fichier `/opt/omi/etc/omiserver.conf` avec les propriétés pemfile et keyfile.</span><span class="sxs-lookup"><span data-stu-id="83031-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="83031-174">Si ce certificat n’est pas approuvé par l’ordinateur Windows où l’applet de commande [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) est exécutée, vous pouvez choisir d’ignorer la validation des certificats en spécifiant les options CIMSession suivantes : `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span><span class="sxs-lookup"><span data-stu-id="83031-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="83031-175">Exécutez la commande suivante pour transmettre en mode Push la configuration DSC vers le nœud Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="83031-176">Distribution de la configuration à l’aide d’un serveur collecteur</span><span class="sxs-lookup"><span data-stu-id="83031-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="83031-177">Vous pouvez utiliser un serveur collecteur pour distribuer des configurations sur un ordinateur Linux, de la même manière que sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="83031-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="83031-178">Pour obtenir des conseils d’utilisation d’un serveur collecteur, consultez [Serveurs collecteurs dans DSC Windows PowerShell](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="83031-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="83031-179">Pour obtenir plus d’informations et connaître les limitations relatives à l’utilisation d’ordinateurs Linux avec un serveur collecteur, consultez les notes de publication concernant DSC pour Linux.</span><span class="sxs-lookup"><span data-stu-id="83031-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="83031-180">Utilisation de configurations locales</span><span class="sxs-lookup"><span data-stu-id="83031-180">Working with configurations locally</span></span>

<span data-ttu-id="83031-181">DSC pour Linux fournit des scripts qui peuvent être utilisés avec une configuration de l’ordinateur Linux local.</span><span class="sxs-lookup"><span data-stu-id="83031-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="83031-182">Ces scripts se trouvent dans le répertoire `/opt/microsoft/dsc/Scripts` et contiennent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="83031-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="83031-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="83031-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="83031-184">Retourne la configuration actuellement appliquée à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83031-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="83031-185">Semblable à l’applet de commande `Get-DscConfiguration` Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83031-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="83031-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="83031-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="83031-187">Retourne la métaconfiguration actuellement appliquée à l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83031-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="83031-188">Similaire à l’applet de commande [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="83031-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="83031-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="83031-189">InstallModule.py</span></span>

<span data-ttu-id="83031-190">Installe un module de ressources DSC personnalisé.</span><span class="sxs-lookup"><span data-stu-id="83031-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="83031-191">Doit spécifier le chemin d’un fichier .zip contenant la bibliothèque d’objets partagés et les fichiers MOF de schéma du module.</span><span class="sxs-lookup"><span data-stu-id="83031-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="83031-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="83031-192">RemoveModule.py</span></span>

<span data-ttu-id="83031-193">Supprime un module de ressources DSC personnalisé.</span><span class="sxs-lookup"><span data-stu-id="83031-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="83031-194">Doit spécifier le nom du module à supprimer.</span><span class="sxs-lookup"><span data-stu-id="83031-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="83031-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="83031-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="83031-196">Applique un fichier MOF de configuration sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83031-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="83031-197">Similaire à l’applet de commande [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="83031-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="83031-198">Doit spécifier le chemin du fichier MOF de configuration à appliquer.</span><span class="sxs-lookup"><span data-stu-id="83031-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="83031-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="83031-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="83031-200">Applique un fichier MOF de métaconfiguration sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="83031-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="83031-201">Similaire à l’applet de commande [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="83031-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="83031-202">Doit spécifier le chemin du fichier MOF de métaconfiguration à appliquer.</span><span class="sxs-lookup"><span data-stu-id="83031-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="83031-203">Fichiers journaux de DSC PowerShell pour Linux</span><span class="sxs-lookup"><span data-stu-id="83031-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="83031-204">Les messages concernant DSC pour Linux sont écrits dans les fichiers journaux suivants.</span><span class="sxs-lookup"><span data-stu-id="83031-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="83031-205">Fichier journal</span><span class="sxs-lookup"><span data-stu-id="83031-205">Log file</span></span>|<span data-ttu-id="83031-206">Répertoire</span><span class="sxs-lookup"><span data-stu-id="83031-206">Directory</span></span>|<span data-ttu-id="83031-207">Description</span><span class="sxs-lookup"><span data-stu-id="83031-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="83031-208">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="83031-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="83031-209">Messages relatifs au fonctionnement du serveur CIM d’OMI.</span><span class="sxs-lookup"><span data-stu-id="83031-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="83031-210">**dsc.log**</span><span class="sxs-lookup"><span data-stu-id="83031-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="83031-211">Messages relatifs au fonctionnement de LCM (Local Configuration Manager) et à l’utilisation des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="83031-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|