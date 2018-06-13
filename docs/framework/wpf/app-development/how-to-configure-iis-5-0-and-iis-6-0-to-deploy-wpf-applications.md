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
ms.openlocfilehash: 7638c6c9af5394838ac584e4dd9a9ca4cfbf8af0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547930"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Jak skonfigurować IS 5.0 oraz IIS 6.0, aby wdrożyć aplikacje WPF
Można wdrożyć [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji z większości serwerów sieci Web, tak długo, jak są one skojarzone z odpowiednim [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] typów. Domyślnie [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] jest skonfigurowany z tych [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typów, ale [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] i [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nie są.  
  
 W tym temacie opisano sposób konfigurowania [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] i [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] wdrażania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
  
> [!NOTE]
>  Możesz sprawdzić *agenta użytkownika* ciągu w rejestrze, aby ustalić, czy system ma zainstalowania środowiska .NET Framework. Szczegółowe informacje i skrypt, który sprawdza *agenta użytkownika* ciąg, aby ustalić, czy .NET Framework jest zainstalowana w systemie, zobacz temat [wykryć, czy .NET Framework 3.0 jest zainstalowana](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).  
  
<a name="content_expiration"></a>   
## <a name="adjust-the-content-expiration-setting"></a>Dostosuj ustawienia wygaśnięcia zawartości  
 Należy dostosować ustawienie czasu wygaśnięcia zawartości na 1 minutę. Poniższa procedura przedstawia sposób, w tym z [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].  
  
1.  Kliknij przycisk **Start** menu wskaż **narzędzia administracyjne**i kliknij przycisk **Internet Information Services (IIS) Manager**. Można również uruchomić tę aplikację z poziomu wiersza polecenia z "% SystemRoot%\system32\inetsrv\iis.msc".  
  
2.  Rozwiń węzeł [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] drzewa do momentu znalezienia **domyślnej witryny sieci Web** węzła.  
  
3.  Kliknij prawym przyciskiem myszy **domyślnej witryny sieci Web** i wybierz **właściwości** z menu kontekstowego.  
  
4.  Wybierz **nagłówków HTTP** i kliknij "Włącz wygaśnięcia zawartości".  
  
5.  Ustaw zawartość wygaśnie po 1 minutę.  
  
<a name="register_mime_types"></a>   
## <a name="register-mime-types-and-file-extensions"></a>Typy MIME rejestru i rozszerzenia plików  
 Należy zarejestrować kilka [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy i rozszerzenia plików, dzięki czemu przeglądarki w systemie klienta można załadować obsługi poprawne. Konieczne jest dodanie następujących typów:  
  
|Rozszerzenia|Typ MIME|  
|---------------|---------------|  
|Manifest|manifest/aplikacji|  
|.XAML|Aplikacja/xaml + xml|  
|.Application|Application/x-ms aplikacji|  
|.XBAP|Application/x-ms-xbap|  
|.Deploy|application/octet-stream|  
|XPS|Aplikacja/vnd.ms-xpsdocument|  
  
> [!NOTE]
>  Nie trzeba zarejestrować [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy i rozszerzenia plików w systemach klienckich. Zostały one zarejestrowane automatycznie podczas instalacji programu Microsoft .NET Framework.  
  
 W poniższym przykładzie programu Microsoft Visual Basic Scripting Edition (VBScript) automatycznie dodaje niezbędne [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typów, aby [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]. Aby użyć skryptu, skopiuj kod do pliku vbs na serwerze. Następnie uruchom skrypt uruchamiania pliku w wierszu polecenia lub dwukrotne kliknięcie pliku w [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].  
  
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
>  Uruchamianie wielokrotne ten skrypt tworzy wiele [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] mapy wpisów w [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabazy.  
  
 Po uruchomieniu tego skryptu, mogą nie być widoczne dodatkowe [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy z [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)]. Jednak te [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy zostały dodane do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabazy. Poniższy skrypt zostaną wyświetlone wszystkie [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy w [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] lub [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabazy.  
  
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
  
 Zapisz skrypt jako `.vbs` pliku (na przykład `DiscoverIISMimeTypes.vbs`) i uruchom go z wiersza polecenia, używając następującego polecenia:  
  
 `cscript DiscoverIISMimeTypes.vbs`
