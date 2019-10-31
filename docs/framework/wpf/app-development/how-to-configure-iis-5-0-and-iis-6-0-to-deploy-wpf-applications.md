---
title: Jak skonfigurować IS 5.0 oraz IIS 6.0, aby wdrożyć aplikacje WPF
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
ms.openlocfilehash: a731dc49556a73c585c6201a80ea3ea77c15cb11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124419"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Jak skonfigurować IS 5.0 oraz IIS 6.0, aby wdrożyć aplikacje WPF

Aplikację [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można wdrożyć z większości serwerów sieci Web, o ile są one skonfigurowane przy użyciu odpowiednich typów MIME (Multipurpose Internet Mail Extensions). Domyślnie usługi Microsoft Internet Information Services (IIS) 7,0 są skonfigurowane przy użyciu tych typów MIME, ale nie są one obsługiwane przez program Microsoft Internet Information Services (IIS) 5,0 i Microsoft Internet Information Services (IIS) 6,0.

W tym temacie opisano sposób konfigurowania programu Microsoft Internet Information Services (IIS) 5,0 i Microsoft Internet Information Services (IIS) 6,0 w celu wdrażania aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

> [!NOTE]
> Możesz sprawdzić ciąg *UserAgent* w rejestrze, aby określić, czy system ma zainstalowaną .NET Framework. Aby uzyskać szczegółowe informacje i skrypt, który sprawdza ciąg *UserAgent* , aby określić, czy .NET Framework jest zainstalowana w systemie, zobacz [wykrywanie, czy .NET Framework 3,0 jest zainstalowany](how-to-detect-whether-the-net-framework-3-0-is-installed.md).

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>Dostosuj ustawienie wygaśnięcia zawartości

Ustawienie wygaśnięcia zawartości należy dostosować do 1 minuty. Poniższa procedura przedstawia, jak to zrobić za pomocą usług IIS.

1. Kliknij menu **Start** , wskaż polecenie **Narzędzia administracyjne**, a następnie kliknij pozycję **Menedżer Internet Information Services (IIS)** . Tę aplikację można również uruchomić z wiersza polecenia z opcją "%SystemRoot%\system32\inetsrv\iis.msc".

2. Rozwiń drzewo IIS do momentu znalezienia **domyślnego węzła witryny sieci Web** .

3. Kliknij prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web** i wybierz polecenie **Właściwości** z menu kontekstowego.

4. Wybierz kartę **nagłówki HTTP** , a następnie kliknij pozycję "Włącz wygasanie zawartości".

5. Ustaw, aby zawartość wygaśnie po 1 minucie.

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>Rejestrowanie typów MIME i rozszerzeń plików

Należy zarejestrować kilka typów MIME i rozszerzeń plików, dzięki czemu przeglądarka w systemie klienta może załadować poprawną procedurę obsługi. Należy dodać następujące typy:

|rozszerzenia|Typ MIME|
|---------------|---------------|
|. manifest|Aplikacja/manifest|
|. XAML|Application/XAML + XML|
|. aplikacja|aplikacja/x-MS-Application|
|. XBAP|aplikacja/x-MS-XBAP|
|. deploy|Aplikacja/oktet — strumień|
|. XPS|application/vnd. MS-XpsDocument|

> [!NOTE]
> Nie trzeba rejestrować typów MIME ani rozszerzeń plików w systemach klienckich. Są one rejestrowane automatycznie podczas instalowania Microsoft .NET Framework.

Poniższy przykład Microsoft Visual Basic Scripting Edition (VBScript) automatycznie dodaje niezbędne typy MIME do usług IIS. Aby użyć skryptu, skopiuj kod do pliku vbs na serwerze. Następnie uruchom skrypt, uruchamiając plik z wiersza polecenia lub klikając dwukrotnie plik w Eksploratorze Microsoft Windows.

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
> Uruchomienie tego skryptu wiele razy powoduje utworzenie wielu wpisów mapy MIME w metabazie programu Microsoft Internet Information Services (IIS) 5,0 lub Microsoft Internet Information Services (IIS) 6,0.

Po uruchomieniu tego skryptu mogą nie być widoczne dodatkowe typy MIME z programu Microsoft Internet Information Services (IIS) 5,0 lub Microsoft Internet Information Services (IIS) 6,0 Microsoft Management Console (MMC). Jednak te typy MIME zostały dodane do metabazy programu Microsoft Internet Information Services (IIS) 5,0 lub Microsoft Internet Information Services (IIS) 6,0. Następujący skrypt będzie wyświetlał wszystkie typy MIME w metabazie programu Microsoft Internet Information Services (IIS) 5,0 lub Microsoft Internet Information Services (IIS) 6,0.

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

Zapisz skrypt jako plik `.vbs` (na przykład `DiscoverIISMimeTypes.vbs`) i uruchom go z wiersza polecenia przy użyciu następującego polecenia:

```console
cscript DiscoverIISMimeTypes.vbs
```
