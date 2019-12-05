---
title: Uruchamianie aplikacji programu .NET Framework 1.1 w systemie Windows 8, Windows 8.1 lub Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 442864cf520d86a819b2dda1b9f24bdb6357fa8e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802192"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Uruchamianie aplikacji programu .NET Framework 1.1 w systemie Windows 8, Windows 8.1 lub Windows 10

.NET Framework 1,1 nie jest obsługiwana w systemach operacyjnych Windows 8, Windows 8.1, [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]ani Windows 10. W niektórych przypadkach .NET Framework 1,1 jest określony jako wymagany do uruchomienia aplikacji. W takich przypadkach należy skontaktować się z niezależnym dostawcą oprogramowania (ISV), aby aplikacja została uaktualniona do działania w .NET Framework 3,5 z dodatkiem SP1 lub nowszym. Aby uzyskać dodatkowe informacje, zobacz [Migrowanie z .NET Framework 1,1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Zainstaluj .NET Framework 1,1 z dysku CD lub Download Center

Nie jest możliwe ręczne zainstalowanie .NET Framework 1,1 w systemie Windows 8, Windows 8.1, [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]lub Windows 10. Nie jest już obsługiwany. Podczas próby zainstalowania pakietu jest wyświetlany następujący komunikat o błędzie: „Kontynuowanie instalacji jest niemożliwe, ponieważ ta wersja programu .NET Framework jest niezgodna z jego wcześniej zainstalowaną wersją.” Aby rozwiązać ten problem, zainstaluj [.NET Framework 3,5 z dodatkiem SP1](https://www.microsoft.com/download/details.aspx?id=22). Ta wersja zawiera .NET Framework 2,0 (wydanie zgodne z .NET Framework 1,1), które jest obsługiwane w systemie Windows 8, Windows 8.1 i Windows 10. Należy zawsze najpierw próbować zainstalować aplikację, aby określić, czy zostanie ona automatycznie zaktualizowana do nowszej wersji .NET Framework. Jeśli nie, skontaktuj się z dostawcą niezależnego dostawcy oprogramowania, aby uzyskać aktualizację aplikacji.

## <a name="see-also"></a>Zobacz także

- [Migracja z programu .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 lub Windows 8](dotnet-35-windows-10.md)
