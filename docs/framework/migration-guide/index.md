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
ms.openlocfilehash: fc3796e3e79112b14d45bb410e63656a81d474c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526723"
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>Przewodnik po migracji do programu .NET Framework 4.7, 4.6 i 4.5 
Jeśli utworzono aplikację przy użyciu wcześniejszej wersji programu .NET Framework, zazwyczaj uaktualnieniem go do programu .NET Framework 4.5 i jego wydania punktowe (4.5.1 i 4.5.2), .NET Framework 4.6 i jego wydania punktowe (4.6.1 i 4.6.2), lub .NET Framework 4.7 i jego punktu łatwo zwalnia (4.7.1 i 4.7.2). Otwórz swój projekt w programie Visual Studio. Jeśli projekt został utworzony we wcześniejszej wersji programu Visual Studio, **zgodności projektu** automatycznie zostanie otwarte okno dialogowe. Aby uzyskać więcej informacji o uaktualnianiu projektu w programie Visual Studio, zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) i [Visual Studio 2017 i zgodności platformy](/visualstudio/productinfo/vs2017-compatibility-vs).  
  
 Jednak niektóre zmiany w programie .NET Framework wymagają zmian w kodzie. Można również korzystać z zalet funkcji, które są nowe w .NET Framework 4.5 i jego wydania punktowe, w .NET Framework 4.6 i jego wydania punktowe lub w programie .NET Framework 4.7 i jego wydania punktowe. Dokonanie zmian do aplikacji dla nowej wersji programu .NET Framework jest zwykle określane jako *migracji*. Jeśli aplikacja nie musi być migrowana, można uruchomić ją w .NET Framework 4.5 lub nowszej wersji, bez konieczności ponownego kompilowania.  
  
## <a name="migration-resources"></a>Zasoby dotyczące migracji  
 Przejrzyj następujące dokumenty przed przeprowadzeniem migracji aplikacji z wcześniejszych wersji programu .NET Framework do wersji 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 lub 4.7.2:  
  
-   Zobacz [wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md) Aby zrozumieć wersję środowiska CLR, bazowy każda wersja programu .NET Framework i zapoznaj się z wytycznymi dla odbiorców docelowych aplikacji pomyślnie.  
  
-   Przegląd [zgodności aplikacji](../../../docs/framework/migration-guide/application-compatibility.md) Aby dowiedzieć się o środowisku wykonawczym i zmianach retargetingu, które mogą mieć wpływ na aplikację i sposobie ich obsługi.  
  
-   Przegląd [What's Obsolete in biblioteki klas](../../../docs/framework/whats-new/whats-obsolete.md) można określić typy lub członków w kodzie, które zostały oznaczone jako przestarzałe i zalecanych rozwiązań alternatywnych.  
  
-   Zobacz [What's New](../../../docs/framework/whats-new/index.md) opisy nowych funkcji, które chcesz dodać do swojej aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zgodność aplikacji](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Migracja z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Zgodność wersji](../../../docs/framework/migration-guide/version-compatibility.md)  
 [Wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [Instrukcje: Konfiguracja aplikacji do obsługi w programie .NET Framework 4 lub 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Co nowego](../../../docs/framework/whats-new/index.md)  
 [Przestarzałe elementy w ułatwieniach dostępu](../../../docs/framework/whats-new/whats-obsolete.md)  
 [.NET framework w wersji i informacji o asemblowaniu](https://go.microsoft.com/fwlink/?LinkId=201701)  
 [Zasady świadczenia pomocy technicznej firmy Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607) [zagadnienia dotyczące migracji programu .NET Framework 4](net-framework-4-migration-issues.md)
