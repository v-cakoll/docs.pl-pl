---
title: 'Przewodnik po migracji do programu .NET Framework 4.8, 4.7, 4.6 i 4.5 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: 2fa992e1c0897d360f322581888c51dca8d8a734
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73974984"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a>Przewodnik po migracji do programu .NET Framework 4.8, 4.7, 4.6 i 4.5

Jeśli aplikacja została utworzona przy użyciu starszej wersji programu .NET Framework, można ją ogólnie uaktualnić do platformy .NET Framework 4.5 i jej wersji punktowych (4.5.1 i 4.5.2), .NET Framework 4.6 i jej wersji punktowych (4.6.1 i 4.6.2), .NET Framework 4.7 i jego wydania punktowe ( 4.7.1 i 4.7.2) lub .NET Framework 4.8. Otwórz projekt w programie Visual Studio. Jeśli projekt został utworzony we wcześniejszej wersji programu Visual Studio, zostanie automatycznie otwarte okno dialogowe **Zgodność projektu.** Aby uzyskać więcej informacji na temat uaktualniania projektu w programie Visual Studio, zobacz [Port, Migrate i Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and Visual Studio [2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).

 Jednak niektóre zmiany w .NET Framework wymagają zmian w kodzie. Można również skorzystać z funkcji, które jest nowy w .NET Framework 4.5 i jego wydania punktowe, w .NET Framework 4.6 i jego wydania punktowe, w .NET Framework 4.7 i jego wydania punktowe lub w .NET Framework 4.8. Wprowadzanie tego typu zmian w aplikacji dla nowej wersji programu .NET Framework jest zwykle określane jako *migracja.* Jeśli aplikacja nie musi być migrowana, można ją uruchomić w systemie .NET Framework 4.5 lub nowszej wersji bez ponownego komppilowania.

## <a name="migration-resources"></a>Zasoby dotyczące migracji

Przejrzyj następujące dokumenty przed migracją aplikacji z wcześniejszych wersji programu .NET Framework do wersji 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 lub 4.8:

- Zobacz [wersje i zależności,](versions-and-dependencies.md) aby zrozumieć wersję CLR leżącą u podstaw każdej wersji programu .NET Framework i przejrzeć wskazówki dotyczące pomyślnego kierowania aplikacji.

- Przejrzyj [zgodność aplikacji,](application-compatibility.md) aby dowiedzieć się więcej o czasie wykonywania i przekierowaniu zmian, które mogą mieć wpływ na aplikację i jak sobie z nimi radzić.

- Przejrzyj, [co jest przestarzałe w bibliotece klas,](../whats-new/whats-obsolete.md) aby określić wszelkie typy lub elementy członkowskie w kodzie, które zostały przestarzałe, i zalecane alternatywy.

- Zobacz [Co nowego, aby](../whats-new/index.md) zapoznać się z opisami nowych funkcji, które możesz dodać do aplikacji.

## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
- [Migracja z programu .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Zgodność z wersjami](version-compatibility.md)
- [Wersje i zależności](versions-and-dependencies.md)
- [Jak: Konfigurowanie aplikacji do obsługi wersji programu .NET Framework 4 lub nowszych](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Co nowego](../whats-new/index.md)
- [Przestarzałe elementy w ułatwieniach dostępu](../whats-new/whats-obsolete.md)
- [Oficjalna polityka wsparcia .NET Framework](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Problemy podczas migracji programu .NET Framework 4](net-framework-4-migration-issues.md)
