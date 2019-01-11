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
ms.openlocfilehash: e9c537aa8fff5fdf823effeae42382ee499efaf4
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221505"
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>Przewodnik po migracji do programu .NET Framework 4.7, 4.6 i 4.5

Jeśli utworzono aplikację przy użyciu wcześniejszej wersji programu .NET Framework, zazwyczaj uaktualnieniem go do programu .NET Framework 4.5 i jego wydania punktowe (4.5.1 i 4.5.2), .NET Framework 4.6 i jego wydania punktowe (4.6.1 i 4.6.2), lub .NET Framework 4.7 i jego punktu łatwo zwalnia (4.7.1 i 4.7.2). Otwórz swój projekt w programie Visual Studio. Jeśli projekt został utworzony we wcześniejszej wersji programu Visual Studio, **zgodności projektu** automatycznie zostanie otwarte okno dialogowe. Aby uzyskać więcej informacji o uaktualnianiu projektu w programie Visual Studio, zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) i [Visual Studio 2017 i zgodności platformy](/visualstudio/productinfo/vs2017-compatibility-vs).

 Jednak niektóre zmiany w programie .NET Framework wymagają zmian w kodzie. Można również korzystać z zalet funkcji, które są nowe w .NET Framework 4.5 i jego wydania punktowe, w .NET Framework 4.6 i jego wydania punktowe lub w programie .NET Framework 4.7 i jego wydania punktowe. Dokonanie zmian do aplikacji dla nowej wersji programu .NET Framework jest zwykle określane jako *migracji*. Jeśli aplikacja nie musi być migrowana, można uruchomić ją w .NET Framework 4.5 lub nowszej wersji, bez konieczności ponownego kompilowania.

## <a name="migration-resources"></a>Zasoby dotyczące migracji

Przejrzyj następujące dokumenty przed przeprowadzeniem migracji aplikacji z wcześniejszych wersji programu .NET Framework do wersji 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 lub 4.7.2:

- Zobacz [wersje i zależności](versions-and-dependencies.md) Aby zrozumieć wersję środowiska CLR, bazowy każda wersja programu .NET Framework i zapoznaj się z wytycznymi dla odbiorców docelowych aplikacji pomyślnie.

- Przegląd [zgodności aplikacji](application-compatibility.md) Aby dowiedzieć się o środowisku wykonawczym i zmianach retargetingu, które mogą mieć wpływ na aplikację i sposobie ich obsługi.

- Przegląd [What's Obsolete in biblioteki klas](../whats-new/whats-obsolete.md) można określić typy lub członków w kodzie, które zostały oznaczone jako przestarzałe i zalecanych rozwiązań alternatywnych.

- Zobacz [What's New](../whats-new/index.md) opisy nowych funkcji, które chcesz dodać do swojej aplikacji.

## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
- [Migracja z programu .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Zgodność wersji](version-compatibility.md)
- [Wersje i zależności](versions-and-dependencies.md)
- [Instrukcje: Konfigurowanie aplikacji do obsługi w programie .NET Framework 4 lub nowszy](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Co nowego](../whats-new/index.md)
- [Przestarzałe elementy w ułatwieniach dostępu](../whats-new/whats-obsolete.md)
- [.NET framework w wersji i informacji o asemblowaniu](https://go.microsoft.com/fwlink/?LinkId=201701)
- [Cykl wsparcia technicznego dla programu Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607)
- [Problemy podczas migracji programu .NET Framework 4](net-framework-4-migration-issues.md)