---
title: Host WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 88e4c6895039c84a57ed215a37a10a4b68851b2d
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817923"
---
# <a name="wpf-host-presentationhostexe"></a>Host WPF (PresentationHost.exe)
Windows Presentation Foundation (WPF) Host (PresentationHost. exe) to aplikacja, która umożliwia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługiwanie aplikacji w zgodnych przeglądarkach (w tym programu Microsoft Internet Explorer 6 i nowszych). Domyślnie Host Windows Presentation Foundation (WPF) jest zarejestrowany jako powłoka i [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] program obsługi dla zawartości obsługiwanej [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przez przeglądarkę, w tym:  
  
- Luźne (Nieskompilowane) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki (. XAML).  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)](. XBAP).  
  
 Dla plików tego typu Windows Presentation Foundation (WPF) Host:  
  
- Uruchamia zarejestrowaną procedurę obsługi HTML do hostowania zawartości Windows Presentation Foundation (WPF).  
  
- Ładuje odpowiednie wersje zestawów wymaganych przez środowisko uruchomieniowe języka wspólnego (CLR) i Windows Presentation Foundation (WPF).  
  
- Zapewnia, że stosowane są odpowiednie poziomy uprawnień dla strefy wdrożenia.  
  
 W tym temacie opisano parametry wiersza polecenia, które mogą być używane z PresentationHost. exe.  
  
## <a name="usage"></a>Użycie  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|nazwa_pliku|Ścieżka pliku, który ma zostać aktywowany. Może być [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]również.|  
|-debug|Podczas aktywowania aplikacji program nie zatwierdza jej ani nie uruchamia ze sklepu. Działa to tylko wtedy, gdy plik lokalny jest aktywowany.|  
|-debugSecurityZoneURL \<url>|Używane z [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] wartością wskazującą PresentationHost. exe, że aplikacja powinna być debugowana tak, jakby została wdrożona z określonego [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]elementu. Określa strefę wdrożenia i lokację źródłową.|  
|— Osadzanie|Wymagane przez OLE. Jeśli parametr `-debug` `-embedding` lub jest określony, nie trzeba określać parametru, ponieważ ten parametr jest ustawiony wewnętrznie. `-event`|  
|-Event \<EventName >|Otwórz zdarzenie o tej nazwie i sygnalizuj go, gdy PresentationHost. exe zostanie zainicjowany i będzie gotowy do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hostowania zawartości. PresentationHost. exe zakończy się, jeśli wystąpił błąd podczas otwierania zdarzenia, na przykład jeśli nie został jeszcze utworzony.|  
|-launchApplication \<adres URL >|Uruchamia autonomiczną aplikację ClickOnce z podanego adresu URL. Stosowane są zasady zabezpieczeń programu Internet Explorer i WinINet dotyczące aplikacji .NET.|  
  
## <a name="scenarios"></a>Scenariusze  
  
### <a name="shell-handler"></a>Procedura obsługi powłoki  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>Procedura obsługi MIME  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Debugowanie programu Visual Studio  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Debugowanie programu Visual Studio w strefie  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia](../security-wpf.md)
