---
title: Jak skonfigurować IS 5.0 oraz IIS 6.0, aby wdrożyć aplikacje WPF
titleSuffix: ''
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
ms.openlocfilehash: d557ac6cd380edcbc93b5315f6356697817274bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740408"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="2bbe8-102">Jak skonfigurować IS 5.0 oraz IIS 6.0, aby wdrożyć aplikacje WPF</span><span class="sxs-lookup"><span data-stu-id="2bbe8-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>

<span data-ttu-id="2bbe8-103">Aplikację [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można wdrożyć z większości serwerów sieci Web, o ile są one skonfigurowane przy użyciu odpowiednich typów MIME (Multipurpose Internet Mail Extensions).</span><span class="sxs-lookup"><span data-stu-id="2bbe8-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate Multipurpose Internet Mail Extensions (MIME) types.</span></span> <span data-ttu-id="2bbe8-104">Domyślnie usługi Microsoft Internet Information Services (IIS) 7,0 są skonfigurowane przy użyciu tych typów MIME, ale nie są one obsługiwane przez program Microsoft Internet Information Services (IIS) 5,0 i Microsoft Internet Information Services (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-104">By default, Microsoft Internet Information Services (IIS) 7.0 is configured with these MIME types, but Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 are not.</span></span>

<span data-ttu-id="2bbe8-105">W tym temacie opisano sposób konfigurowania programu Microsoft Internet Information Services (IIS) 5,0 i Microsoft Internet Information Services (IIS) 6,0 w celu wdrażania aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2bbe8-105">This topic describes how to configure Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2bbe8-106">Możesz sprawdzić ciąg *UserAgent* w rejestrze, aby określić, czy system ma zainstalowaną .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-106">You can check the *UserAgent* string in the registry to determine whether a system has .NET Framework installed.</span></span> <span data-ttu-id="2bbe8-107">Aby uzyskać szczegółowe informacje i skrypt, który sprawdza ciąg *UserAgent* , aby określić, czy .NET Framework jest zainstalowana w systemie, zobacz [wykrywanie, czy .NET Framework 3,0 jest zainstalowany](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="2bbe8-107">For details and a script that examines the *UserAgent* string to determine whether .NET Framework is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="2bbe8-108">Dostosuj ustawienie wygaśnięcia zawartości</span><span class="sxs-lookup"><span data-stu-id="2bbe8-108">Adjust the Content Expiration Setting</span></span>

<span data-ttu-id="2bbe8-109">Ustawienie wygaśnięcia zawartości należy dostosować do 1 minuty.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="2bbe8-110">Poniższa procedura przedstawia, jak to zrobić za pomocą usług IIS.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-110">The following procedure outlines how to do this with IIS.</span></span>

1. <span data-ttu-id="2bbe8-111">Kliknij menu **Start** , wskaż polecenie **Narzędzia administracyjne**, a następnie kliknij pozycję **Menedżer Internet Information Services (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="2bbe8-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="2bbe8-112">Tę aplikację można również uruchomić z wiersza polecenia z opcją "%SystemRoot%\system32\inetsrv\iis.msc".</span><span class="sxs-lookup"><span data-stu-id="2bbe8-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>

2. <span data-ttu-id="2bbe8-113">Rozwiń drzewo IIS do momentu znalezienia **domyślnego węzła witryny sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="2bbe8-113">Expand the IIS tree until you find the **Default Web site** node.</span></span>

3. <span data-ttu-id="2bbe8-114">Kliknij prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web** i wybierz polecenie **Właściwości** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>

4. <span data-ttu-id="2bbe8-115">Wybierz kartę **nagłówki HTTP** , a następnie kliknij pozycję "Włącz wygasanie zawartości".</span><span class="sxs-lookup"><span data-stu-id="2bbe8-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>

5. <span data-ttu-id="2bbe8-116">Ustaw, aby zawartość wygaśnie po 1 minucie.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-116">Set the content to expire after 1 minute.</span></span>

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="2bbe8-117">Rejestrowanie typów MIME i rozszerzeń plików</span><span class="sxs-lookup"><span data-stu-id="2bbe8-117">Register MIME Types and File Extensions</span></span>

<span data-ttu-id="2bbe8-118">Należy zarejestrować kilka typów MIME i rozszerzeń plików, dzięki czemu przeglądarka w systemie klienta może załadować poprawną procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-118">You must register several MIME types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="2bbe8-119">Należy dodać następujące typy:</span><span class="sxs-lookup"><span data-stu-id="2bbe8-119">You need to add the following types:</span></span>

|<span data-ttu-id="2bbe8-120">Rozszerzenie</span><span class="sxs-lookup"><span data-stu-id="2bbe8-120">Extension</span></span>|<span data-ttu-id="2bbe8-121">Typ MIME</span><span class="sxs-lookup"><span data-stu-id="2bbe8-121">MIME Type</span></span>|
|---------------|---------------|
|<span data-ttu-id="2bbe8-122">. manifest</span><span class="sxs-lookup"><span data-stu-id="2bbe8-122">.manifest</span></span>|<span data-ttu-id="2bbe8-123">Aplikacja/manifest</span><span class="sxs-lookup"><span data-stu-id="2bbe8-123">application/manifest</span></span>|
|<span data-ttu-id="2bbe8-124">. XAML</span><span class="sxs-lookup"><span data-stu-id="2bbe8-124">.xaml</span></span>|<span data-ttu-id="2bbe8-125">Application/XAML + XML</span><span class="sxs-lookup"><span data-stu-id="2bbe8-125">application/xaml+xml</span></span>|
|<span data-ttu-id="2bbe8-126">. aplikacja</span><span class="sxs-lookup"><span data-stu-id="2bbe8-126">.application</span></span>|<span data-ttu-id="2bbe8-127">aplikacja/x-MS-Application</span><span class="sxs-lookup"><span data-stu-id="2bbe8-127">application/x-ms-application</span></span>|
|<span data-ttu-id="2bbe8-128">. XBAP</span><span class="sxs-lookup"><span data-stu-id="2bbe8-128">.xbap</span></span>|<span data-ttu-id="2bbe8-129">aplikacja/x-MS-XBAP</span><span class="sxs-lookup"><span data-stu-id="2bbe8-129">application/x-ms-xbap</span></span>|
|<span data-ttu-id="2bbe8-130">. deploy</span><span class="sxs-lookup"><span data-stu-id="2bbe8-130">.deploy</span></span>|<span data-ttu-id="2bbe8-131">Aplikacja/oktet — strumień</span><span class="sxs-lookup"><span data-stu-id="2bbe8-131">application/octet-stream</span></span>|
|<span data-ttu-id="2bbe8-132">. XPS</span><span class="sxs-lookup"><span data-stu-id="2bbe8-132">.xps</span></span>|<span data-ttu-id="2bbe8-133">application/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="2bbe8-133">application/vnd.ms-xpsdocument</span></span>|

> [!NOTE]
> <span data-ttu-id="2bbe8-134">Nie trzeba rejestrować typów MIME ani rozszerzeń plików w systemach klienckich.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-134">You do not need to register MIME types or file extensions on client systems.</span></span> <span data-ttu-id="2bbe8-135">Są one rejestrowane automatycznie podczas instalowania Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>

<span data-ttu-id="2bbe8-136">Poniższy przykład Microsoft Visual Basic Scripting Edition (VBScript) automatycznie dodaje niezbędne typy MIME do usług IIS.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary MIME types to IIS.</span></span> <span data-ttu-id="2bbe8-137">Aby użyć skryptu, skopiuj kod do pliku vbs na serwerze.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="2bbe8-138">Następnie uruchom skrypt, uruchamiając plik z wiersza polecenia lub klikając dwukrotnie plik w Eksploratorze Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-138">Then, run the script by running the file from the command line or double-clicking the file in Microsoft Windows Explorer.</span></span>

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
> <span data-ttu-id="2bbe8-139">Uruchomienie tego skryptu wiele razy powoduje utworzenie wielu wpisów mapy MIME w metabazie programu Microsoft Internet Information Services (IIS) 5,0 lub Microsoft Internet Information Services (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-139">Running this script multiple times creates multiple MIME map entries in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

<span data-ttu-id="2bbe8-140">Po uruchomieniu tego skryptu mogą nie być widoczne dodatkowe typy MIME z programu Microsoft Internet Information Services (IIS) 5,0 lub Microsoft Internet Information Services (IIS) 6,0 Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="2bbe8-140">After you have run this script, you may not see additional MIME types from the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 Microsoft Management Console (MMC).</span></span> <span data-ttu-id="2bbe8-141">Jednak te typy MIME zostały dodane do metabazy programu Microsoft Internet Information Services (IIS) 5,0 lub Microsoft Internet Information Services (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-141">However, these MIME types have been added to the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span> <span data-ttu-id="2bbe8-142">Następujący skrypt będzie wyświetlał wszystkie typy MIME w metabazie programu Microsoft Internet Information Services (IIS) 5,0 lub Microsoft Internet Information Services (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="2bbe8-142">The following script will display all the MIME types in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

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

<span data-ttu-id="2bbe8-143">Zapisz skrypt jako plik `.vbs` (na przykład `DiscoverIISMimeTypes.vbs`) i uruchom go z wiersza polecenia przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="2bbe8-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>

```console
cscript DiscoverIISMimeTypes.vbs
```
