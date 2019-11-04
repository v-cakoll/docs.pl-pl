---
title: 'Przewodnik migracji do .NET Framework 4,8, 4,7, 4,6 i 4,5 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: 350d5400b4e1df7238702ce925c974eecb2a0d7a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457953"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a>Przewodnik migracji do .NET Framework 4,8, 4,7, 4,6 i 4,5

Jeśli aplikacja została utworzona przy użyciu wcześniejszej wersji .NET Framework, można ją na ogół uaktualnić do .NET Framework 4,5 i jego wydań punktów (4.5.1 i 4.5.2), .NET Framework 4,6 i jej wydań punktów (4.6.1 i 4.6.2), .NET Framework 4,7 i ich wydań punktów ( 4.7.1 i 4.7.2) lub .NET Framework 4,8. Otwórz projekt w programie Visual Studio. Jeśli projekt został utworzony we wcześniejszej wersji programu Visual Studio, zostanie automatycznie otwarte okno dialogowe **Zgodność projektu** . Aby uzyskać więcej informacji na temat uaktualniania projektu w programie Visual Studio, zobacz [port, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) oraz [Określanie elementów docelowych i zgodności platformy Visual Studio 2019](/visualstudio/releases/2019/compatibility).

 Jednak niektóre zmiany w .NET Framework wymagają wprowadzenia zmian w kodzie. Możesz również skorzystać z zalet nowych funkcji dostępnych w .NET Framework 4,5 i jej wersjach, w .NET Framework 4,6 i jej wersjach punktów, w .NET Framework 4,7 i jego wersjach punktów lub w .NET Framework 4,8. Wprowadzenie zmian w aplikacji dla nowej wersji .NET Framework jest zwykle określane jako *migracja*. Jeśli aplikacja nie musi być migrowana, można uruchomić ją w .NET Framework 4,5 lub nowszej wersji bez konieczności jej ponownego kompilowania.

## <a name="migration-resources"></a>Zasoby migracji

Przed przeprowadzeniem migracji aplikacji z wcześniejszych wersji .NET Framework do wersji 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 lub 4,8:

- Zapoznaj się z wersjami [i zależnościami](versions-and-dependencies.md) , aby zrozumieć wersję środowiska CLR dla każdej wersji .NET Framework i zapoznać się z wytycznymi dotyczącymi pomyślnego określania docelowych aplikacji.

- Przejrzyj temat [zgodność aplikacji](application-compatibility.md) , aby dowiedzieć się więcej o czasie wykonywania i przekierowaniu zmian, które mogą mieć wpływ na aplikację i jak je obsługiwać.

- Sprawdź, [co jest przestarzałe w bibliotece klas](../whats-new/whats-obsolete.md) , aby określić wszelkie typy lub elementy członkowskie w kodzie, które były przestarzałe, a także zalecane alternatywy.

- Zobacz, [co nowego](../whats-new/index.md) w opisach nowych funkcji, które można chcieć dodać do aplikacji.

## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
- [Migracja z programu .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Zgodność wersji](version-compatibility.md)
- [Wersje i zależności](versions-and-dependencies.md)
- [Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Co nowego?](../whats-new/index.md)
- [Przestarzałe elementy w ułatwieniach dostępu](../whats-new/whats-obsolete.md)
- [Informacje o wersji i zestawie .NET Framework](https://go.microsoft.com/fwlink/?LinkId=201701)
- [Zasady cyklu życia obsługi Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607)
- [Problemy podczas migracji programu .NET Framework 4](net-framework-4-migration-issues.md)
