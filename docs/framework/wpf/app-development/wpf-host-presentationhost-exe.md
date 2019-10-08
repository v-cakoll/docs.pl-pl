---
title: Host WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: c1c26b49a33a58189f66e7b938333f362e467853
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002154"
---
# <a name="wpf-host-presentationhostexe"></a>Host WPF (PresentationHost.exe)
Windows Presentation Foundation (WPF) Host (PresentationHost. exe) to aplikacja, która umożliwia obsługiwanie aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] w zgodnych przeglądarkach (w tym programu Microsoft Internet Explorer 6 i nowszych). Domyślnie Host Windows Presentation Foundation (WPF) jest zarejestrowany jako powłoka i obsługa MIME dla zawartości [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hostowanej w przeglądarce, która obejmuje:  
  
- Luźne (Nieskompilowane) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików (. XAML).  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (. XBAP).  
  
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
|nazwa_pliku|Ścieżka pliku, który ma zostać aktywowany. Może być również [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|-debug|Podczas aktywowania aplikacji program nie zatwierdza jej ani nie uruchamia ze sklepu. Działa to tylko wtedy, gdy plik lokalny jest aktywowany.|  
|-debugSecurityZoneURL \<url >|Używany z wartością adresu URL, aby wskazać PresentationHost. exe, że aplikacja powinna być debugowana tak, jakby została wdrożona z określonego adresu URL. Określa strefę wdrożenia i lokację źródłową.|  
|— Osadzanie|Wymagane przez OLE. Jeśli określono parametr `-event` lub `-debug`, nie trzeba określać `-embedding` parametru, ponieważ ten parametr jest ustawiony wewnętrznie.|  
|-Event @no__t — 0eventname >|Otwórz zdarzenie o tej nazwie i sygnalizuj go, gdy PresentationHost. exe zostanie zainicjowany i będzie gotowy do hostowania zawartości [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. PresentationHost. exe zakończy się, jeśli wystąpił błąd podczas otwierania zdarzenia, na przykład jeśli nie został jeszcze utworzony.|  
|-launchApplication \<url >|Uruchamia autonomiczną aplikację ClickOnce z podanego adresu URL. Stosowane są zasady zabezpieczeń programu Internet Explorer i WinINet dotyczące aplikacji .NET.|  
  
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
