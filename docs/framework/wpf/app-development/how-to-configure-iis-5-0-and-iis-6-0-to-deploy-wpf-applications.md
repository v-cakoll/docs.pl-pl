---
title: 'Instrukcje: Konfigurowanie w usługach IIS 5.0 oraz IIS 6.0 wdrażania aplikacji WPF'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3179679abcf32e40374c7f02e64466a326a73195
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2019
ms.locfileid: "69013020"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="899ea-102">Instrukcje: Konfigurowanie w usługach IIS 5.0 oraz IIS 6.0 wdrażania aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="899ea-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>

<span data-ttu-id="899ea-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Aplikację można wdrożyć z większości serwerów sieci Web, o ile są one skonfigurowane przy użyciu odpowiednich typów MIME (Multipurpose Internet Mail Extensions).</span><span class="sxs-lookup"><span data-stu-id="899ea-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate Multipurpose Internet Mail Extensions (MIME) types.</span></span> <span data-ttu-id="899ea-104">Domyślnie program [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] jest skonfigurowany przy użyciu tych typów MIME, ale [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] i [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nie.</span><span class="sxs-lookup"><span data-stu-id="899ea-104">By default, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] is configured with these MIME types, but [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] are not.</span></span>

<span data-ttu-id="899ea-105">W tym temacie opisano sposób konfigurowania [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] i [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] wdrażania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="899ea-105">This topic describes how to configure [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>

> [!NOTE]
> <span data-ttu-id="899ea-106">Możesz sprawdzić ciąg *UserAgent* w rejestrze, aby określić, czy system ma zainstalowaną .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="899ea-106">You can check the *UserAgent* string in the registry to determine whether a system has .NET Framework installed.</span></span> <span data-ttu-id="899ea-107">Aby uzyskać szczegółowe informacje i skrypt, który sprawdza ciąg *UserAgent* , aby określić, czy .NET Framework jest zainstalowana w systemie, zobacz [wykrywanie, czy .NET Framework 3,0 jest zainstalowany](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="899ea-107">For details and a script that examines the *UserAgent* string to determine whether .NET Framework is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="899ea-108">Dostosuj ustawienie wygaśnięcia zawartości</span><span class="sxs-lookup"><span data-stu-id="899ea-108">Adjust the Content Expiration Setting</span></span>

<span data-ttu-id="899ea-109">Ustawienie wygaśnięcia zawartości należy dostosować do 1 minuty.</span><span class="sxs-lookup"><span data-stu-id="899ea-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="899ea-110">Poniższa procedura przedstawia, jak to zrobić za pomocą programu [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="899ea-110">The following procedure outlines how to do this with [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span>

1. <span data-ttu-id="899ea-111">Kliknij menu **Start** , wskaż polecenie **Narzędzia administracyjne**, a następnie kliknij pozycję **Menedżer Internet Information Services (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="899ea-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="899ea-112">Tę aplikację można również uruchomić z wiersza polecenia z opcją "%SystemRoot%\system32\inetsrv\iis.msc".</span><span class="sxs-lookup"><span data-stu-id="899ea-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>

2. <span data-ttu-id="899ea-113">Rozwiń drzewo do momentu znalezienia **domyślnego węzła witryny sieci Web.** [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]</span><span class="sxs-lookup"><span data-stu-id="899ea-113">Expand the [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] tree until you find the **Default Web site** node.</span></span>

3. <span data-ttu-id="899ea-114">Kliknij prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web** i wybierz polecenie **Właściwości** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="899ea-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>

4. <span data-ttu-id="899ea-115">Wybierz kartę **nagłówki HTTP** , a następnie kliknij pozycję "Włącz wygasanie zawartości".</span><span class="sxs-lookup"><span data-stu-id="899ea-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>

5. <span data-ttu-id="899ea-116">Ustaw, aby zawartość wygaśnie po 1 minucie.</span><span class="sxs-lookup"><span data-stu-id="899ea-116">Set the content to expire after 1 minute.</span></span>

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="899ea-117">Rejestrowanie typów MIME i rozszerzeń plików</span><span class="sxs-lookup"><span data-stu-id="899ea-117">Register MIME Types and File Extensions</span></span>

<span data-ttu-id="899ea-118">Należy zarejestrować kilka typów MIME i rozszerzeń plików, dzięki czemu przeglądarka w systemie klienta może załadować poprawną procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="899ea-118">You must register several MIME types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="899ea-119">Należy dodać następujące typy:</span><span class="sxs-lookup"><span data-stu-id="899ea-119">You need to add the following types:</span></span>

|<span data-ttu-id="899ea-120">Wewnętrzny</span><span class="sxs-lookup"><span data-stu-id="899ea-120">Extension</span></span>|<span data-ttu-id="899ea-121">Typ MIME</span><span class="sxs-lookup"><span data-stu-id="899ea-121">MIME Type</span></span>|
|---------------|---------------|
|<span data-ttu-id="899ea-122">. manifest</span><span class="sxs-lookup"><span data-stu-id="899ea-122">.manifest</span></span>|<span data-ttu-id="899ea-123">Aplikacja/manifest</span><span class="sxs-lookup"><span data-stu-id="899ea-123">application/manifest</span></span>|
|<span data-ttu-id="899ea-124">. XAML</span><span class="sxs-lookup"><span data-stu-id="899ea-124">.xaml</span></span>|<span data-ttu-id="899ea-125">Application/XAML + XML</span><span class="sxs-lookup"><span data-stu-id="899ea-125">application/xaml+xml</span></span>|
|<span data-ttu-id="899ea-126">. aplikacja</span><span class="sxs-lookup"><span data-stu-id="899ea-126">.application</span></span>|<span data-ttu-id="899ea-127">aplikacja/x-MS-Application</span><span class="sxs-lookup"><span data-stu-id="899ea-127">application/x-ms-application</span></span>|
|<span data-ttu-id="899ea-128">. XBAP</span><span class="sxs-lookup"><span data-stu-id="899ea-128">.xbap</span></span>|<span data-ttu-id="899ea-129">aplikacja/x-MS-XBAP</span><span class="sxs-lookup"><span data-stu-id="899ea-129">application/x-ms-xbap</span></span>|
|<span data-ttu-id="899ea-130">. deploy</span><span class="sxs-lookup"><span data-stu-id="899ea-130">.deploy</span></span>|<span data-ttu-id="899ea-131">Aplikacja/oktet — strumień</span><span class="sxs-lookup"><span data-stu-id="899ea-131">application/octet-stream</span></span>|
|<span data-ttu-id="899ea-132">. XPS</span><span class="sxs-lookup"><span data-stu-id="899ea-132">.xps</span></span>|<span data-ttu-id="899ea-133">application/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="899ea-133">application/vnd.ms-xpsdocument</span></span>|

> [!NOTE]
> <span data-ttu-id="899ea-134">Nie trzeba rejestrować typów MIME ani rozszerzeń plików w systemach klienckich.</span><span class="sxs-lookup"><span data-stu-id="899ea-134">You do not need to register MIME types or file extensions on client systems.</span></span> <span data-ttu-id="899ea-135">Są one rejestrowane automatycznie podczas instalowania Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="899ea-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>

<span data-ttu-id="899ea-136">Poniższy przykład Microsoft Visual Basic Scripting Edition (VBScript) automatycznie dodaje wymagane typy MIME do [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]programu.</span><span class="sxs-lookup"><span data-stu-id="899ea-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary MIME types to [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span> <span data-ttu-id="899ea-137">Aby użyć skryptu, skopiuj kod do pliku vbs na serwerze.</span><span class="sxs-lookup"><span data-stu-id="899ea-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="899ea-138">Następnie uruchom skrypt, uruchamiając plik z wiersza polecenia lub dwukrotnie klikając plik w [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span><span class="sxs-lookup"><span data-stu-id="899ea-138">Then, run the script by running the file from the command line or double-clicking the file in [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span></span>

```vb
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

' Get the MimeMap object
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
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> <span data-ttu-id="899ea-139">Uruchomienie tego skryptu wiele razy powoduje utworzenie wielu wpisów mapy MIME w [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] metabazie lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="899ea-139">Running this script multiple times creates multiple MIME map entries in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>

<span data-ttu-id="899ea-140">Po uruchomieniu tego skryptu mogą nie być widoczne dodatkowe typy MIME z [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] programu lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] programu Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="899ea-140">After you have run this script, you may not see additional MIME types from the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] Microsoft Management Console (MMC).</span></span> <span data-ttu-id="899ea-141">Jednak te typy MIME zostały dodane do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] metabazy lub. [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]</span><span class="sxs-lookup"><span data-stu-id="899ea-141">However, these MIME types have been added to the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span> <span data-ttu-id="899ea-142">Poniższy skrypt będzie wyświetlał wszystkie typy MIME w [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] metabazie lub. [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]</span><span class="sxs-lookup"><span data-stu-id="899ea-142">The following script will display all the MIME types in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

<span data-ttu-id="899ea-143">Zapisz skrypt jako `.vbs` plik (na `DiscoverIISMimeTypes.vbs`przykład) i uruchom go z wiersza polecenia przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="899ea-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>

```console
cscript DiscoverIISMimeTypes.vbs
```
