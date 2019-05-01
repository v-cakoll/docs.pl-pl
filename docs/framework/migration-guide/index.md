---
title: 'Przewodnik po migracji do programu .NET Framework 4,8, 4.7, 4.6 i 4.5 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb51a0be57992d65a88e958d76a5e371dc028a00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871452"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a>Przewodnik po migracji do programu .NET Framework 4,8, 4.7, 4.6 i 4.5

Jeśli użyto do utworzenia aplikacji przy użyciu wcześniejszej wersji programu .NET Framework, zazwyczaj można uaktualnić go do programu .NET Framework 4.5 i jego wydania punktowe (4.5.1 i 4.5.2), .NET Framework 4.6 i jego punktu zwalnia (4.6.1 i 4.6.2), .NET Framework 4.7 i jego punktu zwalnia) 4.7.1 i 4.7.2) lub .NET Framework 4.8 łatwe. Otwórz swój projekt w programie Visual Studio. Jeśli projekt został utworzony we wcześniejszej wersji programu Visual Studio, **zgodności projektu** automatycznie zostanie otwarte okno dialogowe. Aby uzyskać więcej informacji o uaktualnianiu projektu w programie Visual Studio, zobacz [Port, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) i [Visual Studio 2019 r i zgodności platformy](/visualstudio/releases/2019/compatibility).

 Jednak niektóre zmiany w programie .NET Framework wymagają zmian w kodzie. Można również korzystać z zalet funkcji, które są nowe w .NET Framework 4.5 i jego wydania punktowe, w .NET Framework 4.6 i jego wydania punktowe, w .NET Framework 4.7 i jego wydania punktowe lub w .NET Framework 4.8. Dokonanie zmian do aplikacji dla nowej wersji programu .NET Framework jest zwykle określane jako *migracji*. Jeśli aplikacja nie musi być migrowana, można uruchomić ją w .NET Framework 4.5 lub nowszej wersji, bez konieczności ponownego kompilowania.

## <a name="migration-resources"></a>Zasoby dotyczące migracji

Przed przeprowadzeniem migracji aplikacji z wcześniejszych wersji programu .NET Framework do wersji 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 lub 4,8, przejrzyj następujące dokumenty:

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
- [Microsoft .NET Framework Support Lifecycle Policy](https://go.microsoft.com/fwlink/?LinkId=196607)
- [Problemy podczas migracji programu .NET Framework 4](net-framework-4-migration-issues.md)