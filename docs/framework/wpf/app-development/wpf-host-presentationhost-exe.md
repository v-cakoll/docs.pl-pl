---
title: Host WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 543076c3b00bf7946111df4c18d8c71928ce7ee2
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487327"
---
# <a name="wpf-host-presentationhostexe"></a>Host WPF (PresentationHost.exe)
Windows Presentation Foundation (WPF), hosta (PresentationHost.exe) to aplikacja, która umożliwia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacje hostowane w przeglądarkach zgodne (w tym [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] lub nowszy). Domyślnie Windows Presentation Foundation (WPF), hosta jest zarejestrowany jako powłoki i [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] Obsługa obsługiwane w przeglądarce [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawartość, która obejmuje:  
  
- Luźne (nieskompilowanych) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików (.xaml).  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).  
  
 Pliki te typy hostów Windows Presentation Foundation (WPF):  
  
- Uruchamia zarejestrowaną [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] program obsługi, aby obsługiwać zawartość Windows Presentation Foundation (WPF).  
  
- Ładuje właściwych wersji wymaganego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] i zestawy Windows Presentation Foundation (WPF).  
  
- Gwarantuje, że zostały spełnione właściwe poziomy uprawnień dla strefy wdrożenia.  
  
 W tym temacie opisano parametry wiersza polecenia, które mogą być używane z PresentationHost.exe.  
  
## <a name="usage"></a>Użycie  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|nazwa_pliku|Ścieżka pliku zostanie uaktywniony. Można też [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|-debug|Podczas aktywowania aplikacji, nie Zatwierdź go do ani uruchomić go z magazynu. Ta działa tylko wtedy, gdy plik lokalny jest aktywny.|  
|-debugSecurityZoneURL \<url>|Używane z [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] wartości, aby wskazać PresentationHost.exe, że aplikację można debugować tak, jakby jego zostały wdrożone z określonego [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]. Określa strefę wdrożenia i witrynę pochodzenia.|  
|-embedding|Wymagane przez OLE. Jeśli `-event` lub `-debug` parametr jest określony, nie jest konieczne określić `-embedding` parametru, ponieważ ten parametr ma wartość wewnętrznie.|  
|-Zdarzenie \<eventname >|Otwórz zdarzenie o tej nazwie, a wyda sygnał, gdy PresentationHost.exe jest inicjowany i gotowe do hostowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawartości. PresentationHost.exe przestaną obowiązywać w przypadku, gdy wystąpił błąd podczas otwierania zdarzenia, np. Jeśli go nie już istnieje.|  
|-launchApplication \<adresu url >|Uruchamia samodzielnej aplikacji ClickOnce z określonego adresu URL. [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] i są stosowane zasady zabezpieczeń WinINet dotyczących aplikacji platformy .NET.|  
  
## <a name="scenarios"></a>Scenariusze  
  
### <a name="shell-handler"></a>Obsługa powłoki  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>Program obsługi MIME  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Visual Studio Debugging  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Visual Studio Debugging In Zone  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia](../security-wpf.md)
