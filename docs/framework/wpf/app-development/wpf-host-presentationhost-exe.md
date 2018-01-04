---
title: Host WPF (PresentationHost.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c5a9df438353701932a3e732d6df28b08402ee8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-host-presentationhostexe"></a>Host WPF (PresentationHost.exe)
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]Host (PresentationHost.exe) to aplikacja, która umożliwia [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji ma być obsługiwana w przeglądarkach zgodne (w tym [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] i nowsze). Domyślnie [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] hosta jest zarejestrowany jako powłoki i [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] Obsługa oparta na przeglądarce [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawartość, która obejmuje:  
  
-   Luźne (nieskompilowanych) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików (.xaml).  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)](.xbap).  
  
 Pliki te typy [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] hosta:  
  
-   Uruchamia zarejestrowaną [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] obsługi hosta [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] zawartości.  
  
-   Ładuje właściwych wersji wymaganego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] i [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] zestawów.  
  
-   Gwarantuje, że poziomy odpowiednich uprawnień dla strefy wdrożenia zostały spełnione.  
  
 W tym temacie opisano parametry wiersza polecenia, które mogą być używane z PresentationHost.exe.  
  
## <a name="usage"></a>Użycie  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|nazwa_pliku|Ścieżka pliku do aktywacji. Można też [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].|  
|-debug|Podczas aktywacji aplikacji, nie go do zatwierdzenia lub uruchomić go z magazynu. Ta działa tylko wtedy, gdy plik lokalny jest aktywny.|  
|-debugSecurityZoneURL \<adres url >|Używane z [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] wartości wskazującej PresentationHost.exe, że aplikację można debugować tak, jakby były na nim wdrożone z określonego [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]. Określa zarówno strefy wdrażania, jak i witryny pochodzenia.|  
|-Osadzanie|Wymagane przez OLE. Jeśli `-event` lub `-debug` podano parametr nie jest konieczne w celu określenia `-embedding` parametru, ponieważ ten parametr ma wartość wewnętrznie.|  
|-zdarzeń \<eventname >|Otworzyć zdarzenia o tej nazwie i sygnału go, gdy PresentationHost.exe jest zainicjowana i gotowa do hosta [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zawartości. PresentationHost.exe spowoduje przerwanie Jeśli wystąpił błąd podczas otwierania zdarzenia, np. Jeśli go nie już został utworzony.|  
|-launchApplication \<adres url >|Uruchamia autonomiczny [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikacji z podanego adresu URL. [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)]i są stosowane zasady zabezpieczeń WinINet dotyczących aplikacji .NET.|  
  
## <a name="scenarios"></a>Scenariusze  
  
### <a name="shell-handler"></a>Obsługa powłoki  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a>Program obsługi MIME  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a>Debugowanie programu Visual Studio  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a>Visual Studio debugowanie w strefie  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia](../../../../docs/framework/wpf/security-wpf.md)
