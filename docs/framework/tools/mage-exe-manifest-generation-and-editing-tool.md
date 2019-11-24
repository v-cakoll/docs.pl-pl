---
title: Mage.exe (Narzędzie generowania manifestu i edytowania)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: aa2ad9222460f8732397f8b1c72e36085bbe4a21
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449421"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (Narzędzie generowania manifestu i edytowania)

The Manifest Generation and Editing Tool (*Mage.exe*) is a command-line tool that supports the creation and editing of application and deployment manifests. As a command-line tool, *Mage.exe* can be run from both batch scripts and other Windows-based applications, including ASP.NET applications.

You can also use *MageUI.exe*, a graphical application, instead of *Mage.exe*. For more information, see [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

To narzędzie jest instalowane automatycznie z programem Visual Studio. To run the tool, use Developer Command Prompt for Visual Studio. For more information, see [Command Prompts](developer-command-prompt-for-vs.md).

Two versions of *Mage.exe* and *MageUI.exe* are included with Visual Studio. To see version information, run *MageUI.exe*, select **Help**, and select **About**. This documentation describes version 4.0.x.x of *Mage.exe* and *MageUI.exe*.

## <a name="syntax"></a>Składnia

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametry

The following table shows the commands supported by *Mage.exe*. For more information about the options supported by these commands, see [New and Update command options](#new-and-update-command-options) and [Sign command options](#sign-command-options).

|Polecenie|Opis|
|-------------|-----------------|
|**-cc, ClearApplicationCache**|Czyści pamięć podręczną pobranych aplikacji ze wszystkich aplikacji działających tylko w trybie online.|
|**-n, -New** *fileType [newOptions]*|Tworzy nowy plik danego typu. Prawidłowymi typami są:<br /><br /> -   `Deployment`: Creates a new deployment manifest.<br />-   `Application`: Creates a new application manifest.<br /><br /> Jeśli nie określono żadnych dodatkowych parametrów dla tego polecenia, zostanie utworzony plik odpowiedniego typu, z odpowiednimi domyślnymi tagami oraz wartościami atrybutów.<br /><br /> Use the **-ToFile** option (see in the following table) to specify the file name and path of the new file.<br /><br /> Use the **-FromDirectory** option (see in the following table) to create an application manifest with all of the assemblies for an application added to the \<dependency> section of the manifest.|
|**-u, -Update** *[filePath] [updateOptions]*|Wprowadza co najmniej jedną zmianę w pliku manifestu. Nie trzeba określać typu edytowanego pliku. Program Mage.exe zbada plik za pomocą zestawu algorytmów heurystycznych i ustali, czy jest to manifest wdrożenia, czy aplikacji.<br /><br /> If you have already signed a file with a certificate, **-Update** will remove the key signature block. Dzieje się tak dlatego, że podpis klucza zawiera skrót pliku i modyfikacja pliku spowoduje, że skrót będzie nieprawidłowy.<br /><br /> Use the **-ToFile** option (see in the following table) to specify a new file name and path instead of overwriting the existing file.|
|**-s, -Sign** `[signOptions]`|Używa pary kluczy lub certyfikatu X509 w celu podpisania pliku. Podpisy są wstawiane jako elementy XML wewnątrz plików.<br /><br /> You must be connected to the Internet when signing a manifest that specifies a **-TimestampUri** value.|
|**-ver, -Verify** *[manifest-filename]*|Verifies that the manifest is signed correctly. Cannot be combined with other commands. <br/><br/>**Available in .NET Framework 4.7 and later versions.**|
|**-h, -?, -Help** *[verbose]*|Opisuje wszystkie z dostępnych poleceń i ich opcji. Specify `verbose` to get detailed help.|

## <a name="new-and-update-command-options"></a>New and Update command options

The following table shows the options supported by the `-New` and `-Update` commands:

|Opcje|Wartość domyślna|Dotyczy:|Opis|
|-------------|-------------------|----------------|-----------------|
|**-a, -Algorithm**|sha1RSA|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”.<br /><br /> Należy używać z opcją „-Update”. Ta opcja jest ignorowana, gdy używana jest opcja „-Sign”.|
|**-appc, -AppCodeBase** `manifestReference`||Manifesty wdrożenia.|Wstawia odwołanie do adresu URL lub ścieżki pliku do pliku manifestu aplikacji. Ta wartość musi być pełną ścieżką do manifestu aplikacji.|
|**-appm, -AppManifest** `manifestPath`||Manifesty wdrożenia.|Wstawia do manifestu wdrożenia odwołanie do manifestu wdrażanej aplikacji.<br /><br /> The file indicated by `manifestPath` must exist, or *Mage.exe* will issue an error. If the file referenced by `manifestPath` is not an application manifest, *Mage.exe* will issue an error.|
|**-cf, -CertFile** `filePath`||Wszystkie typy plików.|Specifies the location of an X509 digital certificate for signing a manifest or license file. This option can be used in conjunction with the **-Password** option if the certificate requires a password for Personal Information Exchange (PFX) files. Starting with .NET Framework 4.7, if the file does not contain a private key, a combination of the **-CryptoProvider** and **-KeyContainer** options is required.<br/><br/>Starting with .NET Framework 4.6.2, *Mage.exe* signs manifests with CNG as well as CAPI certificates.|
|**-ch, -CertHash** `hashSignature`||Wszystkie typy plików.|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada on ciągowi odcisku palca certyfikatu cyfrowego wyświetlanego w konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature` can be either uppercase or lowercase, and can be supplied either as a single string, or with each octet of the Thumbprint separated by spaces and the entire Thumbprint enclosed in quotation marks.|
|**-csp, -CryptoProvider** `provider-name`||Wszystkie typy plików.|Specifies the name of a cryptographic service provider (CSP) that contains the private key container. This option requires the **-KeyContainer** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-fd, -FromDirectory** `directoryPath`||Manifesty aplikacji.|Populates the application manifest with descriptions of all assemblies and files found in `directoryPath`, including all subdirectories, where `directoryPath` is the directory that contains the application that you want to deploy. For each file in the directory, *Mage.exe* decides whether the file is an assembly or a static file. If it is an assembly, it adds a `<dependency>` tag and `installFrom` attribute to the application with the assembly's name, code base, and version. If it is a static file, it adds a `<file>` tag. *Mage.exe* will also use a simple set of heuristics to detect the main executable for the application, and will mark it as the ClickOnce application's entry point in the manifest.<br /><br /> *Mage.exe* will never automatically mark a file as a "data" file. Tę czynność należy wykonać ręcznie. For more information, see [How to: Include a Data File in a ClickOnce Application](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* also generates a hash for each file based on its size. Technologia ClickOnce używa tych skrótów, aby zagwarantować, że nikt nie ingerował w pliki wdrożenia od czasu utworzenia manifestu. If any of the files in your deployment change, you can run *Mage.exe* with the **-Update** command and the **-FromDirectory** option, and it will update the hashes and assembly versions of all referenced files.<br /><br /> **-FromDirectory** will include all files in all subdirectories found within `directoryPath`.<br /><br /> If you use **-FromDirectory** with the **-Update** command, *Mage.exe* will remove any files in the application manifest that no longer exist in the directory.|
|**-if, -IconFile**  `filePath`||Manifesty aplikacji.|Określa pełną ścieżkę do pliku ikony ICO. Ta ikona pojawia się obok nazwy aplikacji w menu Start oraz we wpisie w aplecie Dodaj lub usuń programy. Jeśli nie zostanie dostarczona ikona, będzie używana ikona domyślna.|
|**-ip, -IncludeProviderURL**  `url`|true|Manifesty wdrożenia.|Indicates whether the deployment manifest includes the update location value set by **-ProviderURL**.|
|**-i, -Install** `willInstall`|true|Manifesty wdrożenia.|Wskazuje, czy aplikacja ClickOnce ma zostać zainstalowana na komputerze lokalnym, czy ma być uruchamiana z sieci Web. Installing an application gives that application a presence in the Windows **Start** menu. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> If you specify the **-MinVersion** option, and a user has a version less than **-MinVersion** installed, it will force the application to install, regardless of the value that you pass to **-Install**.<br /><br /> This option cannot be used with the **-BrowserHosted** option. Próba określenia obu tych opcji dla jednego manifestu spowoduje błąd.|
|**-kc, -KeyContainer** `name`||Wszystkie typy plików.|Specifies the key container that contains the name of the private key. This option requires the **CryptoProvider** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-mv, -MinVersion**  `[version]`|The version listed in the ClickOnce deployment manifest as specified by the **-Version** flag.|Manifesty wdrożenia.|Minimalna wersja aplikacji, jaką może uruchomić użytkownik. Ta flaga powoduje, że nazwana wersja aplikacji staje się wymaganą aktualizacją. Jeśli zostanie wydana wersja produktu z aktualizacją dotyczącą ważnej zmiany lub krytycznej wady zabezpieczeń, można użyć tej flagi, aby określić, że ta aktualizacja musi zostać zainstalowana, a użytkownik nie może kontynuować używania wcześniejszych wersji.<br /><br /> `version` has the same semantics as the argument to the **-Version** flag.|
|**-n, -Name** `nameString`|Deploy|Wszystkie typy plików.|Nazwa, która jest używana do identyfikacji aplikacji. ClickOnce will use this name to identify the application in the **Start** menu (if the application is configured to install itself) and in Permission Elevation dialog boxes. **Note:**  If you are updating an existing manifest and you do not specify a publisher name with this option, *Mage.exe* updates the manifest with the organization name defined on the computer. Aby użyć innej nazwy, należy użyć tej opcji i określić odpowiednią nazwę wydawcy.|
|**-pwd, -Password** `passwd`||Wszystkie typy plików.|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Must be used in conjunction with the **-CertFile** option.|
|**-p, Processor** `processorValue`|Msil|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Architektura mikroprocesora, na której będzie uruchomiona dystrybucja. Ta wartość jest wymagana, jeśli jest przygotowywanych kilka instalacji, których zestawy są wstępnie kompilowane dla określonego mikroprocesora. Valid values include `msil`, `x86`, `ia64`, and `amd64`. `msil` is Microsoft intermediate language, which means all of your assemblies are platform-independent, and the common language runtime (CLR) will just-in-time compile them when your application is first run.|
|**-pu,** **-ProviderURL** `url`||Manifesty wdrożenia.|Określa adres URL, pod którym technologia ClickOnce będzie szukać aktualizacji aplikacji.|
|**-pub, -Publisher** `publisherName`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Dodaje nazwę wydawcy do opisu elementu manifestu wdrożenia lub aplikacji. When used on an application manifest, **-UseManifestForTrust** must also be specified with a value of "true" or "t"; otherwise, this parameter will raise an error.|
|**-s, -SupportURL**  `url`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Określa łącze, które pojawia się w aplecie Dodaj lub usuń programy dla aplikacji ClickOnce.|
|**-ti, -TimestampUri** `uri`||Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Adres URL usługi cyfrowego oznaczania znacznikami czasu. Oznaczenie manifestu znacznikiem czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. For more information, see [Windows root certificate program members](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)).|
|**-t, -ToFile** `filePath`|-   New:<br />-   Deployment: deploy.application<br />-   Application: application.exe.manifest<br />-   Update:<br />-   The input file.|Wszystkie typy plików.|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.<br /><br /> If **-ToFile** is not supplied when you use **-New**, the output is written to the current working directory. If **-ToFile** is not supplied when you use **-Update**, *Mage.exe* will write the file back to the input file.|
|**-tr, -TrustLevel** `level`|Wartość określana na podstawie strefy, w której znajduje się adres URL aplikacji.|Manifesty aplikacji.|Poziom zaufania, który zostanie przyznany aplikacji na komputerach klientów. Dostępne wartości to Internet, Intranet i FullTrust.|
|**-um, -UseManifestForTrust** `willUseForTrust`|False|Manifesty aplikacji.|Określa, czy podpis cyfrowy manifestu aplikacji będzie używany do podejmowania decyzji dotyczących zaufania, gdy aplikacja zostanie uruchomiona na komputerze klienckim. Określenie wartości „true” lub „t” wskazuje, że manifest aplikacji zostanie użyty do podejmowania decyzji dotyczących zaufania. Określenie wartości „false” lub „f” wskazuje, że zostanie użyty podpis manifestu wdrożenia.|
|**-v, -Version** `versionNumber`|1.0.0.0|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Wersja wdrożenia. The argument must be a valid version string of the format "*N.N.N.N*", where "*N*" is an unsigned 32-bit integer.|
|**-wpf, -WPFBrowserApp**  `isWPFApp`|false|Manifesty aplikacji.<br /><br /> Manifesty wdrożenia.|Tej flagi należy używać tyko wtedy, gdy aplikacja jest aplikacją programu Windows Presentation Foundation (WPF), która będzie obsługiwana wewnątrz programu Internet Explorer i nie jest autonomicznym plikiem wykonywalnym. Prawidłowymi wartościami są „true” lub „t” oraz „false” lub „f”.<br /><br /> For application manifests, inserts the `hostInBrowser` attribute under the `entryPoint` element of the application manifest.<br /><br /> For deployment manifests, sets the `install` attribute on the `deployment` element to false, and saves the deployment manifest with a .xbap extension. Specifying this argument along with the **-Install** argument produces an error, because a browser-hosted application cannot be an installed, offline application.|

## <a name="sign-command-options"></a>Sign command options

The following table shows the options supported by the `-Sign` command, which apply to all types of files.

|Opcje|Opis|
|-------------|-----------------|
|**-cf, -CertFile** `filePath`|Określa lokalizację certyfikatu cyfrowego używanego do podpisania manifestu. This option can be used in conjunction with the **-Password** option if the certificate requires a password for Personal Information Exchange (PFX) files. Starting with .NET Framework 4.7, if the file does not contain a private key, a combination of the **-CryptoProvider** and **-KeyContainer** options is required.<br/><br/>Starting with .NET Framework 4.6.2, *Mage.exe* signs manifests with CNG as well as CAPI certificates.|
|**-ch, -CertHash** `hashSignature`|Skrót certyfikatu cyfrowego przechowywanego w osobistym magazynie certyfikatów na komputerze klienta. Odpowiada właściwości odcisku palca certyfikatu cyfrowego wyświetlanego na konsoli certyfikatów systemu Windows.<br /><br /> `hashSignature` can be either uppercase or lowercase, and can be supplied either as a single string or with each octet of the Thumbprint separated by spaces and the entire Thumbprint enclosed in quotation marks.|
**-csp, -CryptoProvider** `provider-name`|Specifies the name of a cryptographic service provider (CSP) that contains the private key container. This option requires the **-KeyContainer** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-kc, -KeyContainer** `name`|Specifies the key container that contains the name of the private key. This option requires the **CryptoProvider** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-pwd, -Password** `passwd`|Hasło używane do podpisywania manifestu za pomocą certyfikatu cyfrowego. Must be used in conjunction with the **-CertFile** option.|
|**-t, -ToFile** `filePath`|Określa ścieżkę wyjściową utworzonego lub zmodyfikowanego pliku.|

## <a name="remarks"></a>Uwagi

All arguments to *Mage.exe* are case-insensitive. Polecenia i opcje mogą być poprzedzone kreską (-) lub ukośnikiem (/).

All of the arguments used with the **-Sign** command can be used at any time with the **-New** or **-Update** commands as well. Poniższe polecenia są równoważne.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> Beginning with .NET Framework version 4.6.2, CNG certificates are also supported.

 Podpisywanie jest ostatnim zadaniem, które należy wykonać, ponieważ podpisany dokument używa skrótu pliku w celu weryfikacji, czy podpis jest prawidłowy dla dokumentu. W przypadku wprowadzenia jakiejkolwiek zmiany w podpisanym pliku należy podpisać go ponownie. If you sign a document that was previously signed, *Mage.exe* will replace the old signature with the new.

 When you use the **-AppManifest** option to populate a deployment manifest, *Mage.exe* will assume that your application manifest will reside in the same directory as the deployment manifest within a subdirectory named after the current deployment version, and will configure your deployment manifest appropriately. If your application manifest will reside elsewhere, use the **-AppCodeBase** option to set the alternate location.

 Manifesty wdrożenia i aplikacji muszą zostać podpisane przed wdrożeniem aplikacji. For guidance about signing manifests, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).

 The **-TrustLevel** option for application manifests describes the permission set an application requires to run on the client computer. By default, applications are assigned a trust level based on the *zone* in which their URL resides. Aplikacje wdrożone przez sieć firmową są zazwyczaj umieszczane w strefie Intranet, podczas gdy te wdrożone przez Internet umieszczane są w strefie Internet. Obie strefy zabezpieczeń nakładają na aplikację ograniczenia w zakresie dostępu do lokalnych zasobów, przy czym strefa Intranet ma nieco łagodniejsze ograniczenia niż strefa Internet. Strefa FullTrust udziela aplikacji pełnego dostępu do lokalnych zasobów komputera. If you use the **-TrustLevel** option to place an application in this zone, the Trust Manager component of the CLR will prompt the user to decide whether he or she wants to grant this higher level of trust. Jeśli aplikacja jest wdrażana przez sieć firmową, można użyć narzędzia Wdrażanie zaufanych aplikacji, aby podnieść poziom zaufania aplikacji bez monitowania użytkownika.

 Manifesty aplikacji obsługują także niestandardowe sekcje zaufania. Pomaga to aplikacji przestrzegać reguły zabezpieczeń, zgodnie z którą należy żądać jak najniższych uprawnień, ponieważ można skonfigurować manifest do żądania tylko tych określonych uprawnień, których aplikacja wymaga do działania. *Mage.exe* does not directly support adding a custom trust section. You can add one using a text editor, an XML parser, or the graphical tool *MageUI.exe*. For more information about how to use *MageUI.exe* to add custom trust sections, see [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017 includes version 4.6.1 of *Mage.exe*. Manifests created with this version of *Mage.exe* target .NET Framework 4. To target older versions of the .NET Framework, use an earlier version of *Mage.exe*.

When you add or remove assemblies from an existing manifest, or re-sign an existing manifest, *Mage.exe* does not update the manifest to target .NET Framework 4.

The following tables show these features and restrictions:

|Wersja manifestu|Operacja|Mage w wersji 2.0|Mage w wersji 4.0|
|----------------------|---------------|---------------|---------------|
|Manifest dla aplikacji, których platforma docelowa to wersja 2.0 lub 3.x programu .NET Framework|Otwarcie|OK|OK|
||Zamknięcie|OK|OK|
||Zapisanie|OK|OK|
||Ponowne podpisane|OK|OK|
||New|OK|Nieobsługiwane|
||Aktualizacja (zobacz poniżej)|OK|OK|
|Manifest dla aplikacji, których platforma docelowa to wersja 4 programu .NET Framework|Otwarcie|OK|OK|
||Zamknięcie|OK|OK|
||Zapisanie|OK|OK|
||Ponowne podpisane|OK|OK|
||New|Nieobsługiwane|OK|
||Aktualizacja (zobacz poniżej)|Nieobsługiwane|OK|

|Wersja manifestu|Szczegóły operacji aktualizacji|Mage w wersji 2.0|Mage w wersji 4.0|
|----------------------|------------------------------|---------------|---------------|
|Manifest dla aplikacji, których platforma docelowa to wersja 2.0 lub 3.x programu .NET Framework|Modyfikacja zestawu|OK|OK|
||Dodanie zestawu|OK|OK|
||Usunięcie zestawu|OK|OK|
|Manifest dla aplikacji, których platforma docelowa to wersja 4 programu .NET Framework|Modyfikacja zestawu|Nieobsługiwane|OK|
||Dodanie zestawu|Nieobsługiwane|OK|
||Usunięcie zestawu|Nieobsługiwane|OK|

 Mage.exe creates new manifests that target the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. ClickOnce applications that target the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] can run on both the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] and the full version of the .NET Framework 4. If your application targets the full version of the .NET Framework 4 and cannot run on the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], remove the client `<framework>` element by using a text editor and re-sign the manifest.

The following is a sample `<framework>` element that targets the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Przykłady

The following example opens the user interface for Mage (*MageUI.exe*).

```console
mage
```

W poniższym przykładzie są tworzone domyślne manifesty wdrożenia i aplikacji. Wszystkie te pliki są tworzone w bieżącym katalogu roboczym i są nazwane odpowiednio deploy.application i application.exe.manifest.

```console
mage -New Deployment
mage -New Application
```

The following example creates an application manifest populated with all of the assemblies and resource files from the current directory.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0
```

W poniższym przykładzie jest kontynuowany poprzedni przykład i jest określana nazwa wdrożenia oraz docelowy mikroprocesor. Określany jest także adres URL, pod którym technologia ClickOnce będzie sprawdzać dostępność aktualizacji.

```console
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/
```

W poniższym przykładzie pokazano sposób tworzenia pary manifestów dla wdrożenia aplikacji programu WPF, która będzie obsługiwana w programie Internet Explorer.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true
```

The following example creates an application manifest populated with all of the assemblies and resource files from the current directory and signs.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -KeyContainer keypair.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

W poniższym przykładzie manifest wdrożenia jest aktualizowany informacjami z manifestu aplikacji, a także jest ustawiana podstawa kodu dla lokalizacji manifestu aplikacji.

```console
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy
```

W poniższym przykładzie manifest wdrożenia jest edytowany w celu wymuszenia aktualizacji zainstalowanej wersji użytkownika.

```console
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0
```

W poniższym przykładzie manifest wdrożenia otrzymuje instrukcję pobrania manifestu aplikacji z innego katalogu.

```console
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/
```

W poniższym przykładzie istniejący manifest wdrożenia jest podpisywany przy użyciu certyfikatu cyfrowego w bieżącym katalogu roboczym.

```console
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>
```

The following example signs an existing deployment manifest using a digital certificate and private key in the current working directory.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Przegląd wdrażania zaufanych aplikacji](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
