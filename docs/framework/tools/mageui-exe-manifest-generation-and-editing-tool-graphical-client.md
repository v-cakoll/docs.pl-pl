---
title: MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 99f522181232d16b9913ba3c55f34274b75d8966
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449414"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (Narzędzie generowania i edytowania manifestu, klient grafiki)

MageUI.exe obsługuje takie same funkcje jak narzędzie wiersza polecenia Mage.exe, ale z interfejsem użytkownika systemu Windows (UI). Za pomocą tego narzędzia można tworzyć, edytować i podpisywać manifesty wdrażania i aplikacji. New manifests that are created with MageUI.exe target the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Poprzednie wersje MageUI.exe stosuje się do poprzednich wersji .NET Framework. When adding or removing assemblies from a manifest, or re-signing existing manifests, MageUI.exe does not update the manifest to target [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. For more information, see [Mage.exe (Manifest Generation and Editing Tool)](mage-exe-manifest-generation-and-editing-tool.md).

 To narzędzie jest instalowane automatycznie z programem Visual Studio. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). For more information, see [Command Prompts](developer-command-prompt-for-vs.md).

 Two versions of Mage.exe and MageUI.exe are included as a component of Visual Studio. To see version information, run MageUI.exe, select **Help**, and select **About**. W tej dokumentacji opisano wersję 4.0.x.x programów Mage.exe i MageUI.exe.

> [!NOTE]
> MageUI.exe does not support the [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) element when saving an application manifest that has already been signed with a certificate using MageUI.exe. Instead, you must use [Mage.exe](mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 W następującej tabeli wymieniono elementy menu i paski narzędzi, które są dostępne.  
  
|Polecenie|Menu|Skrót|Opis|  
|-------------|----------|--------------|-----------------|  
|**Application Manifest**|**File, New**||Tworzy nowy manifest aplikacji.|  
|**Deployment Manifest**|**File, New**||Tworzy nowy manifest wdrożenia.|  
|**Open**|**File**|CTRL+O|Otwiera do edycji istniejący manifest wdrażania, manifest aplikacji lub licencję zaufania.|  
|**Close**|**File**|CTRL+F4|Zamyka otwarty plik.<br /><br /> Jeśli modyfikujesz plik przed jego zamknięciem, MageUI.exe monituje o ponowne podpisywanie pliku kluczem publicznym, parą kluczy lub przechowywanym certyfikatem.|  
|**Save**|**File**|CTRL+S|Zapisuje na dysku dokument, który aktualnie ma fokus wprowadzania użytkownika.|  
|**Save As**|**File**||Zapisuje plik na dysku, umożliwiając podanie nowej nazwy pliku i/lub lokalizacji.|  
|**Save All**|**File**||Zapisuje zmiany wprowadzone do wszystkich plików aktualnie otwartych w MageUI.exe.|  
|**Preferencje**|**File**||Opens the **Preferences** dialog box. Aby uzyskać więcej informacji, zobacz następującą sekcję.|  
|**Zakończ**|**File**|ALT+F4|Zamyka program MageUI.exe.|  
|**Cut**|**Edytowanie**|CTRL+X|Usuwa zaznaczony tekst z aplikacji i przenosi je do Schowka systemu Windows.|  
|**Kopiuj**|**Edytowanie**|CTRL+C|Kopiuje zaznaczony tekst do Schowka systemu Windows.|  
|**Paste**|**Edytowanie**|CTRL+V|Wkleja tekst ze Schowka systemu Windows do aktywnego elementu tekstu.|  
|**Delete**|**Edytowanie**||Deletes an element currently selected in a list, such as a trust license on the **Deployment Manifest** tab.|  
|**Close All**|**Window**||Zamyka wszystkie pliki otwarte w MageUI.exe. Jeżeli jeden lub więcej plików wymagają zapisania, MageUI.exe wyświetli monit o zapisanie ich. MageUI.exe również wyświetla monit o wybranie klucza podpisywania dla każdego niepodpisanego lub zmienionego pliku.|  
|**About**|**Help**||Wyświetla informacje o wersji i prawach autorskich dotyczące MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Okno dialogowe Preferencje  
 The **Preferences** dialog box contains the following elements.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Sign on save**|Monituje o podpisanie pliku przy każdym zapisie modyfikacji.|  
|**Use default signing certificate**|Uses the key entered in the **Certificate file** text box to sign all files. This eliminates the signing prompt that typically appears when you save a file and **Sign on Save** is selected. Use the ellipsis ( **…** ) button next to the **Certificate file** text box to select a key file.|  
|Algorytm porządkowania|Określa algorytm, za pomocą którego zostaną wygenerowane skróty zależności. Wartością musi być „sha256RSA” lub „sha1RSA”. Domyślną wartością jest SHA1. Używana zarówno w manifestach aplikacji, jak i wdrażania. Jeśli użytkownik poda certyfikat podczas zapisywania manifestu, używane są algorytmy w certyfikacie do wygenerowania rozkładów zależności.|  
  
## <a name="signing-options-dialog-box"></a>Okno dialogowe Opcje podpisywania  
 The **Signing Options** dialog box appears when you save a manifest or trust license for the first time, or when you change a manifest or trust license. It only appears if the **Sign on Save** option in the **Preferences** dialog box is selected. You must be connected to the Internet when signing a manifest that specifies a value in the **TimeStamping URI** text box.  
  
 To okno dialogowe zawiera następujące elementy.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Sign with certificate file**|Podpisuje manifest certyfikatem cyfrowym przechowywanym w systemie plików.|  
|**File**|Zapewnia miejsce do wpisania ścieżki do pliku pfx reprezentującego certyfikat.|  
|**...**|Opens a **Choose File** dialog box for selecting an existing .pfx file.|  
|**New**|Generuje nowy pfx niesprawdzalny przez urząd certyfikacji (CA). For more information about the types of certificates used for signing ClickOnce deployments, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Password**|Miejsce na wpisanie hasła używanego do podpisywania tym certyfikatem. Jeśli nie ma to zastosowania, może być puste.|  
|**Sign with stored certificate**|Wyświetla listę wyboru certyfikatów cyfrowych przechowywanych w magazynie certyfikatów na komputerze.|  
|**TimeStamping URI**|Wyświetla identyfikator URI usługi sygnatur cyfrowych. Przypisanie do manifestu znacznika czasu zapobiega konieczności ponownego podpisania manifestu, jeśli certyfikat cyfrowy wygaśnie przed wdrożeniem następnej wersji aplikacji. For more information, see [Windows root certificate program members](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) and [ClickOnce and Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Don't Sign**|Umożliwia zapisanie manifestu bez dodawania podpisu z certyfikatu cyfrowego.|  
  
## <a name="tab-and-panel-descriptions"></a>Opisy karta i panelu  
 Po otwarciu w programie MageUI.exe dokument pojawia się w obrębie własnej strony karty. Każda karta zawiera zestaw paneli właściwości. Panele zawierają zgrupowane podzbiory danych dokumentu.  
  
### <a name="application-manifest-tab"></a>Application Manifest Tab  
 The **Application Manifest** tab displays the contents of an application manifest. The application manifest describes all files included with the deployment, and the permissions required for the application to run on the client.  
  
 The **Application Manifest** tab contains the following tabs.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Specifies identifying information about this deployment.|  
|**Opis**|Specifies publisher, product, and support information.|  
|**Application Options**|Specifies whether this is a browser application, and whether this manifest is the source of trust information.|  
|**Pliki**|Specifies all of the files that constitute this deployment.|  
|**Permissions Required**|Specifies the minimum permission set required by the application to run on a client.|  
  
### <a name="name-tab"></a>Name Tab  
 The **Name** tab is displayed when you first create or open an application manifest. It uniquely identifies the deployment, and optionally specifies a valid target platform.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagany. The name of the application manifest. Usually the same as the file name.|  
|**Wersja**|Wymagany. The version number of the deployment in the form *N.N.N.N*. Only the first major build number is required. For example, for version 1.0 of an application, valid values would include `1`, `1.0`, `1.0.0`, and `1.0.0.0`.|  
|**Processor**|Opcjonalny. The machine architecture on which this deployment can run. The default is `msil`, or Microsoft Intermediate Language, which is the default format of all managed assemblies. Change this field if you have pre-compiled the assemblies in your application for a specific architecture. For more information about pre-compilation, see [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).|  
|**Culture**|Opcjonalny. The two-part ISO country and region code in which this application runs. Wartość domyślna to `neutral`.|  
|**Public key token**|Opcjonalny. The public key with which this application manifest has been signed. If this is a new or unsigned manifest, this field will appear as `Unsigned`.|  
  
### <a name="description-tab"></a>Description Tab  
 This information is usually provided within the deployment manifest. These fields can only be modified if the **Use Application Manifest Trust Information** check box is selected on the **Application Options** tab.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Publisher**|The name of the person or organization responsible for the application. This value is used as the Start menu folder name.|  
|**Product**|The full product name. If you selected **Install Locally** for the **Application Type** element on the **Deployment Options** tab of the deployment manifest, this name will be what appears in the **Start** menu link and in **Add or Remove Programs** for this application.|  
|**Support Location**|The URL from which customers can obtain help and support for the application.|  
  
### <a name="application-options-tab"></a>Application Options Tab  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Windows Presentation Foundation Browser Application**|Specifies whether this is a WPF application that runs in the browser as a XAML browser application (XBAP).|  
|**Use Application Manifest Trust Information**|Specifies whether this manifest contains trust information.|  
  
### <a name="files-tab"></a>Files Tab  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Application directory**|The directory in which the application's files reside. Use the ellipses ( **…** ) button to select the directory.|  
|**Populate**|Adds all of the files in the application directory and subdirectories to the application manifest. If MageUI.exe finds a single executable file in the directory, it automatically marks this as the Entry Point, which is the file first executed when the ClickOnce application is launched on the client.|  
|**Application Files**|Lists all of the files in the application. Each file has three editable attributes, discussed below.|  
|**File Type**|File Type can be one of four values:<br /><br /> -   None.<br />-   Entry Point. The application's primary executable. Only one executable file can be marked as the entry point.<br />-   Data File. A file, such as an XML file, that supplies data to the application.<br />-   Icon File. An application icon, such as appears on the desktop or in the corner of an application's window.|  
|**Optional**|Files marked optional are not downloaded on initial install or update, but may be downloaded at run time using the System.Deployment On-Demand API. For more information, see [Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Group**|A label for a set of optional files. You can apply a Group label to a set of files, and use the On-Demand API to download a batch of files with a single API call.|  
  
### <a name="permissions-required-tab"></a>Permissions Required Tab  
 Use the **Permissions Required** tab if you need to grant your application more access to the local computer than is granted by default. For more information, see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications).  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Permission set type**|The minimum permission set required by this application to run on the client. For a description of these permission sets and which permissions they do or do not demand, see [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Details**|The XML created for the application manifest to represent the permission set. Unless you have a good understanding of the application manifest XML format, you should not edit this XML manually. For more information, see [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Deployment Manifest Tab  
 The **Deployment Manifest** tab contains the following tabs.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Specifies identifying information about this deployment.|  
|**Opis**|Specifies publisher, product, and support information.|  
|**Deployment Options**|Specifies additional information about the deployment, such as the application type and the start location.|  
|**Update Options**|Specifies how often ClickOnce should check for application updates.|  
|**Application Reference**|Specifies the application manifest for this deployment.|  
  
### <a name="name-tab"></a>Name Tab  
 The **Name** tab is displayed when you first create or open a deployment manifest. It uniquely identifies the deployment, and optionally specifies a valid target platform.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Nazwa**|Wymagany. The name of the deployment manifest. Usually the same as the file name.|  
|**Wersja**|Wymagany. The version number of the deployment in the form *N.N.N.N*. Only the first major build number is required. For example, for version 1.0 of an application, valid values would include `1`, `1.0`, `1.0.0`, and `1.0.0.0`.|  
|**Processor**|Opcjonalny. The machine architecture on which this deployment can run. The default is `msil`, or Microsoft Intermediate Language, the default format of all managed assemblies. Change this field if you have compiled the assemblies in your application for a specific architecture.|  
|**Culture**|Opcjonalny. The two-part ISO country/region code in which this application runs. Wartość domyślna to `neutral`.|  
|**Public key token**|Opcjonalny. The public key with which this deployment manifest has been signed. If this is a new or unsigned manifest, this field will appear as `Unsigned`.|  
  
### <a name="description-tab"></a>Description Tab  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Publisher**|Wymagany. The name of the person or organization responsible for the application. This value is used as the Start menu folder name.|  
|**Product**|Wymagany. The full product name. If you selected **Install Locally** for the **Application Type** element on the **Deployment Options** tab, this name will be what appears in the **Start** menu link and in **Add or Remove Programs** for this application.|  
|**Support Location**|Opcjonalny. The URL from which customers can obtain help and support for the application.|  
  
### <a name="deployment-options-tab"></a>Deployment Options Tab  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Application Type**|Opcjonalny. Specifies whether this application installs itself to the client computer (**Install Locally**), runs online (**Online Only**), or is a WPF application that runs in the browser (**WPF Browser Application**). The default is **Install Locally**.|  
|**Start Location**|Opcjonalny. The URL from which the application should actually be started. Useful when deploying an application from a CD that should update itself from the Web.|  
|**Include Start Location (ProviderURL) in the manifest**|Opcjonalny. Określa adres URL, pod którym technologia ClickOnce będzie szukać aktualizacji aplikacji.|  
|**Automatically run application after installing**|Wymagany. Specifies that the ClickOnce application should run immediately after the initial installation from a URL. The default is the check box is selected.|  
|**Allow URL parameters to be passed to application**|Wymagany. Permits the transfer of parameter data to the ClickOnce application through a query string appended to the deployment manifest's URL. The default is the check box is cleared.|  
|**Use .deploy file extension**|Wymagany. When selected, all files in the application manifest must have the .deploy extension. The default is the check box is cleared.|  
  
### <a name="update-options-tab"></a>Update Options Tab  
 The **Update Options** tab only contains options mentioned here when the **Application Type** selection box on the **Name** tab is set to **Install Locally**.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**This application should check for updates**|Specifies whether ClickOnce should check for application updates. If this check box is not selected, the application will not check for updates unless you update it programmatically by using the APIs in the <xref:System.Deployment.Application> namespace.|  
|**Choose when the application should check for updates**|Provides two options for update checks:<br /><br /> -   **Before the application starts**. The update check is performed prior to application execution.<br />-   **After the application starts**. The update check begins once the main form of the application has initialized, and will run the next time the application starts.|  
|**Update check frequency**|Determines how often ClickOnce should check for updates:<br /><br /> -   **Check every time the application runs**. ClickOnce will perform an update check every time the user opens the application.<br />-   **Check every**: Select a time interval and a unit (hours, days, or weeks) that must elapse before checking for updates.|  
|**Specify a minimum required version for this application**|Opcjonalny. Specifies that a specific version of your application is a required installation, preventing your users from working with an earlier version.|  
|**Wersja**|Required if **Specify a minimum required version for this application** check box is selected. The version number supplied must be of the form *N.N.N.N*. Only the first major build number is required. For example, for version 1.0 of an application, valid values would include `1`, `1.0`, `1.0.0`, and `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Application Reference Tab  
 The **Application Reference** tab contains the same fields as the **Name** tab described earlier in this topic. The one exception is the following field.  
  
|Element interfejsu użytkownika|Opis|  
|----------------|-----------------|  
|**Select Manifest**|Allows you to choose the application manifest. All of the other fields on this page will populate when you choose an application manifest.|  
  
## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](mage-exe-manifest-generation-and-editing-tool.md)
