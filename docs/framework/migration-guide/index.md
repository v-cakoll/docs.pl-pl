---
title: 'Przewodnik po migracji do programu .NET Framework 4.7, 4.6 i 4.5 '
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8ef6d73aa6cd044cf6808878bf6142a735d015c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391252"
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>Przewodnik po migracji do programu .NET Framework 4.7, 4.6 i 4.5 
Jeśli utworzono aplikację przy użyciu wcześniejszej wersji programu .NET Framework, zazwyczaj uaktualnieniem go do programu .NET Framework 4.5 i jego wersje punktu (4.5.1 i 4.5.2), .NET Framework 4.6 i jego wersje punktu (4.6.1 i 4.6.2), lub .NET Framework 4.7 i jego punktu zwalnia łatwo (4.7.1 i 4.7.2). Otwórz projekt w programie Visual Studio. Jeśli projekt został utworzony we wcześniejszej wersji programu Visual Studio, **zgodność projektu** automatycznie zostanie otwarte okno dialogowe. Aby uzyskać więcej informacji na temat uaktualniania projektu programu Visual Studio, zobacz [portu, migracji i uaktualniania projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) i [programu Visual Studio 2017 platformy elementów docelowych i zgodności](/visualstudio/productinfo/vs2017-compatibility-vs).  
  
 Jednak niektóre zmiany w programie .NET Framework wymaga zmian w kodzie. Można również skorzystać z funkcji, które są nowe w .NET Framework 4.5 i zwalnia jego punktu, w .NET Framework 4.6 i zwalnia jego punktu lub .NET Framework 4.7 i zwalnia jego punktu. Wprowadzanie zmiany tego typu aplikacji dla nowej wersji programu .NET Framework jest zwykle nazywany *migracji*. Jeśli aplikacja nie ma do migracji, można uruchomić go w .NET Framework 4.5 lub nowszej wersji, bez konieczności ponownego kompilowania go.  
  
## <a name="migration-resources"></a>Zasoby związane z migracją  
 Przejrzyj poniższe dokumenty, przed przeprowadzeniem migracji aplikacji z wcześniejszych wersji programu .NET Framework w wersji 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 lub 4.7.2:  
  
-   Zobacz [wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md) do zrozumienia wersji środowiska CLR bazowy każda wersja programu .NET Framework i przejrzyj wskazówki dotyczące pomyślnie przeznaczonych dla aplikacji.  
  
-   Przegląd [zgodności aplikacji](../../../docs/framework/migration-guide/application-compatibility.md) Aby uzyskać informacje na temat środowiska uruchomieniowego i przekierowania zmiany, które mogą mieć wpływ na aplikację i sposobu ich obsługi.  
  
-   Przegląd [co to jest przestarzałe w bibliotece klas](../../../docs/framework/whats-new/whats-obsolete.md) do ustalenia lub typy elementów członkowskich w kodzie zostały wprowadzone przestarzałe i zalecanych rozwiązań alternatywnych.  
  
-   Zobacz [What's New](../../../docs/framework/whats-new/index.md) opisy nowych funkcji, które chcesz dodać do aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zgodność aplikacji](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Migracja z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Zgodność wersji](../../../docs/framework/migration-guide/version-compatibility.md)  
 [Wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [Instrukcje: Konfiguracja aplikacji do obsługi w programie .NET Framework 4 lub 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Co nowego](../../../docs/framework/whats-new/index.md)  
 [Przestarzałe elementy w ułatwieniach dostępu](../../../docs/framework/whats-new/whats-obsolete.md)  
 [.NET framework w wersji oraz informacje o zestawie](http://go.microsoft.com/fwlink/?LinkId=201701)  
 [Microsoft .NET Framework wsparcia technicznego produktów](http://go.microsoft.com/fwlink/?LinkId=196607) [problemy przy migracji programu .NET Framework 4](net-framework-4-migration-issues.md)
