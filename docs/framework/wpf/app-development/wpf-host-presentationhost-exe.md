---
title: Host WPF (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743403"
---
# <a name="wpf-host-presentationhostexe"></a>Host WPF (PresentationHost.exe)
Windows Presentation Foundation (WPF) Host (PresentationHost. exe) to aplikacja, która umożliwia obsługiwanie aplikacji WPF w zgodnych przeglądarkach (w tym programu Microsoft Internet Explorer 6 i nowszych). Domyślnie Host Windows Presentation Foundation (WPF) jest zarejestrowany jako powłoka i obsługa MIME dla zawartości WPF hostowanej w przeglądarce, która obejmuje:  
  
- Luźno (niekompilowane) pliki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (. XAML).  
  
- Aplikacja przeglądarki XAML (XBAP) (XBAP).  
  
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
|nazwa_pliku|Ścieżka pliku, który ma zostać aktywowany. Może również być identyfikatorem URI.|  
|-debug|Podczas aktywowania aplikacji program nie zatwierdza jej ani nie uruchamia ze sklepu. Działa to tylko wtedy, gdy plik lokalny jest aktywowany.|  
|-debugSecurityZoneURL \<adres URL >|Używany z wartością adresu URL, aby wskazać PresentationHost. exe, że aplikacja powinna być debugowana tak, jakby została wdrożona z określonego adresu URL. Określa strefę wdrożenia i lokację źródłową.|  
|— Osadzanie|Wymagane przez OLE. Jeśli parametr `-event` lub `-debug` jest określony, nie trzeba określać `-embedding` parametru, ponieważ ten parametr jest ustawiony wewnętrznie.|  
|-Event \<EventName >|Otwórz zdarzenie o tej nazwie i sygnalizuj go, gdy PresentationHost. exe zostanie zainicjowany i będzie gotowy do hostowania zawartości WPF. PresentationHost. exe zakończy się, jeśli wystąpił błąd podczas otwierania zdarzenia, na przykład jeśli nie został jeszcze utworzony.|  
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

- [Security](../security-wpf.md)
