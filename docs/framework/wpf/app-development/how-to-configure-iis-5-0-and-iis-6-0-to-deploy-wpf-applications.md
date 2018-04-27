---
title: Jak skonfigurować IS 5.0 oraz IIS 6.0, aby wdrożyć aplikacje WPF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c1b03cf39608566ed80e2288204480e77994ad7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="c7e4c-102">Jak skonfigurować IS 5.0 oraz IIS 6.0, aby wdrożyć aplikacje WPF</span><span class="sxs-lookup"><span data-stu-id="c7e4c-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>
<span data-ttu-id="c7e4c-103">Można wdrożyć [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji z większości serwerów sieci Web, tak długo, jak są one skojarzone z odpowiednim [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] typów.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] types.</span></span> <span data-ttu-id="c7e4c-104">Domyślnie [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] jest skonfigurowany z tych [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typów, ale [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] i [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nie są.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-104">By default, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] is configured with these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types, but [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] are not.</span></span>  
  
 <span data-ttu-id="c7e4c-105">W tym temacie opisano sposób konfigurowania [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] i [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] wdrażania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-105">This topic describes how to configure [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>  
  
  
> [!NOTE]
>  <span data-ttu-id="c7e4c-106">Możesz sprawdzić *agenta użytkownika* ciągu w rejestrze, aby ustalić, czy system ma [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-106">You can check the *UserAgent* string in the registry to determine whether a system has [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] installed.</span></span> <span data-ttu-id="c7e4c-107">Szczegółowe informacje i skrypt, który sprawdza *agenta użytkownika* ciąg, aby określić, czy [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] jest zainstalowany na komputerze, zobacz [wykryć, czy .NET Framework 3.0 jest zainstalowana](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="c7e4c-107">For details and a script that examines the *UserAgent* string to determine whether [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="c7e4c-108">Dostosuj ustawienia wygaśnięcia zawartości</span><span class="sxs-lookup"><span data-stu-id="c7e4c-108">Adjust the Content Expiration Setting</span></span>  
 <span data-ttu-id="c7e4c-109">Należy dostosować ustawienie czasu wygaśnięcia zawartości na 1 minutę.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="c7e4c-110">Poniższa procedura przedstawia sposób, w tym z [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7e4c-110">The following procedure outlines how to do this with [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span>  
  
1.  <span data-ttu-id="c7e4c-111">Kliknij przycisk **Start** menu wskaż **narzędzia administracyjne**i kliknij przycisk **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="c7e4c-112">Można również uruchomić tę aplikację z poziomu wiersza polecenia z "% SystemRoot%\system32\inetsrv\iis.msc".</span><span class="sxs-lookup"><span data-stu-id="c7e4c-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>  
  
2.  <span data-ttu-id="c7e4c-113">Rozwiń węzeł [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] drzewa do momentu znalezienia **domyślnej witryny sieci Web** węzła.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-113">Expand the [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] tree until you find the **Default Web site** node.</span></span>  
  
3.  <span data-ttu-id="c7e4c-114">Kliknij prawym przyciskiem myszy **domyślnej witryny sieci Web** i wybierz **właściwości** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>  
  
4.  <span data-ttu-id="c7e4c-115">Wybierz **nagłówków HTTP** i kliknij "Włącz wygaśnięcia zawartości".</span><span class="sxs-lookup"><span data-stu-id="c7e4c-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>  
  
5.  <span data-ttu-id="c7e4c-116">Ustaw zawartość wygaśnie po 1 minutę.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-116">Set the content to expire after 1 minute.</span></span>  
  
<a name="register_mime_types"></a>   
## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="c7e4c-117">Typy MIME rejestru i rozszerzenia plików</span><span class="sxs-lookup"><span data-stu-id="c7e4c-117">Register MIME Types and File Extensions</span></span>  
 <span data-ttu-id="c7e4c-118">Należy zarejestrować kilka [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy i rozszerzenia plików, dzięki czemu przeglądarki w systemie klienta można załadować obsługi poprawne.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-118">You must register several [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="c7e4c-119">Konieczne jest dodanie następujących typów:</span><span class="sxs-lookup"><span data-stu-id="c7e4c-119">You need to add the following types:</span></span>  
  
|<span data-ttu-id="c7e4c-120">Rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="c7e4c-120">Extension</span></span>|<span data-ttu-id="c7e4c-121">Typ MIME</span><span class="sxs-lookup"><span data-stu-id="c7e4c-121">MIME Type</span></span>|  
|---------------|---------------|  
|<span data-ttu-id="c7e4c-122">Manifest</span><span class="sxs-lookup"><span data-stu-id="c7e4c-122">.manifest</span></span>|<span data-ttu-id="c7e4c-123">manifest/aplikacji</span><span class="sxs-lookup"><span data-stu-id="c7e4c-123">application/manifest</span></span>|  
|<span data-ttu-id="c7e4c-124">.XAML</span><span class="sxs-lookup"><span data-stu-id="c7e4c-124">.xaml</span></span>|<span data-ttu-id="c7e4c-125">Aplikacja/xaml + xml</span><span class="sxs-lookup"><span data-stu-id="c7e4c-125">application/xaml+xml</span></span>|  
|<span data-ttu-id="c7e4c-126">.Application</span><span class="sxs-lookup"><span data-stu-id="c7e4c-126">.application</span></span>|<span data-ttu-id="c7e4c-127">Application/x-ms aplikacji</span><span class="sxs-lookup"><span data-stu-id="c7e4c-127">application/x-ms-application</span></span>|  
|<span data-ttu-id="c7e4c-128">.XBAP</span><span class="sxs-lookup"><span data-stu-id="c7e4c-128">.xbap</span></span>|<span data-ttu-id="c7e4c-129">Application/x-ms-xbap</span><span class="sxs-lookup"><span data-stu-id="c7e4c-129">application/x-ms-xbap</span></span>|  
|<span data-ttu-id="c7e4c-130">.Deploy</span><span class="sxs-lookup"><span data-stu-id="c7e4c-130">.deploy</span></span>|<span data-ttu-id="c7e4c-131">application/octet-stream</span><span class="sxs-lookup"><span data-stu-id="c7e4c-131">application/octet-stream</span></span>|  
|<span data-ttu-id="c7e4c-132">XPS</span><span class="sxs-lookup"><span data-stu-id="c7e4c-132">.xps</span></span>|<span data-ttu-id="c7e4c-133">Aplikacja/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="c7e4c-133">application/vnd.ms-xpsdocument</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c7e4c-134">Nie trzeba zarejestrować [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy i rozszerzenia plików w systemach klienckich.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-134">You do not need to register [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types or file extensions on client systems.</span></span> <span data-ttu-id="c7e4c-135">Zostały one zarejestrowane automatycznie podczas instalacji programu Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>  
  
 <span data-ttu-id="c7e4c-136">W poniższym przykładzie programu Microsoft Visual Basic Scripting Edition (VBScript) automatycznie dodaje niezbędne [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typów, aby [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7e4c-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types to [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span> <span data-ttu-id="c7e4c-137">Aby użyć skryptu, skopiuj kod do pliku vbs na serwerze.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="c7e4c-138">Następnie uruchom skrypt uruchamiania pliku w wierszu polecenia lub dwukrotne kliknięcie pliku w [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7e4c-138">Then, run the script by running the file from the command line or double-clicking the file in [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span></span>  
  
```  
' This script adds the necessary Windows Presentation Foundation MIME types   
' to an IIS Server.  
' To use this script, just double-click or execute it from a command line.  
' Running this script multiple times results in multiple entries in the IIS MimeMap.  
  
Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec  
Const ADS_PROPERTY_UPDATE = 2   
  
' Set the MIME types to be added  
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _  
    "application/xaml+xml", ".application", "application/x-ms-application", _  
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _  
    ".xps", "application/vnd.ms-xpsdocument")   
  
' Get the mimemap object   
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")  
  
' Call AddMimeType for every pair of extension/MIME type  
For counter = 0 to UBound(MimeTypesToAddArray) Step 2  
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)  
Next  
  
' Create a Shell object  
Set WshShell = CreateObject("WScript.Shell")  
  
' Stop and Start the IIS Service  
Set oExec = WshShell.Exec("net stop w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = WshShell.Exec("net start w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = Nothing  
  
' Report status to user  
WScript.Echo "Windows Presentation Foundation MIME types have been registered."  
  
' AddMimeType Sub  
Sub AddMimeType (Ext, MType)  
  
    ' Get the mappings from the MimeMap property.   
    MimeMapArray = MimeMapObj.GetEx("MimeMap")   
  
    ' Add a new mapping.   
    i = UBound(MimeMapArray) + 1   
    Redim Preserve MimeMapArray(i)   
    Set MimeMapArray(i) = CreateObject("MimeMap")   
    MimeMapArray(i).Extension = Ext   
    MimeMapArray(i).MimeType = MType   
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray  
    MimeMapObj.SetInfo  
  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="c7e4c-139">Uruchamianie wielokrotne ten skrypt tworzy wiele [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] mapy wpisów w [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabazy.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-139">Running this script multiple times creates multiple [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] map entries in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>  
  
 <span data-ttu-id="c7e4c-140">Po uruchomieniu tego skryptu, mogą nie być widoczne dodatkowe [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy z [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7e4c-140">After you have run this script, you may not see additional [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types from the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span></span> <span data-ttu-id="c7e4c-141">Jednak te [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy zostały dodane do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabazy.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-141">However, these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types have been added to the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span> <span data-ttu-id="c7e4c-142">Poniższy skrypt zostaną wyświetlone wszystkie [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy w [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabazy.</span><span class="sxs-lookup"><span data-stu-id="c7e4c-142">The following script will display all the [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>  
  
```  
' This script lists the MIME types for an IIS Server.  
' To use this script, just double-click or execute it from a command line   
' by calling cscript.exe  
  
dim mimeMapEntry, allMimeMaps  
  
' Get the mimemap object.  
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")  
allMimeMaps = mimeMapEntry.GetEx("MimeMap")  
  
' Display the mappings in the table.  
For Each mimeMap In allMimeMaps  
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")  
Next  
```  
  
 <span data-ttu-id="c7e4c-143">Zapisz skrypt jako `.vbs` pliku (na przykład `DiscoverIISMimeTypes.vbs`) i uruchom go z wiersza polecenia, używając następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c7e4c-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>  
  
 `cscript DiscoverIISMimeTypes.vbs`
