---
title: Uruchom z .NET Framework 1.1 aplikacji w systemie Windows 8, Windows 8.1 lub Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ceaa3ea9d9140c6b5df45f067558da2de80b8dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535414"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Uruchom z .NET Framework 1.1 aplikacji w systemie Windows 8, Windows 8.1 lub Windows 10

.NET Framework 1.1 nie jest obsługiwana w [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], lub w systemach operacyjnych Windows 10. W niektórych przypadkach program .NET Framework 1.1 jest jednoznacznie identyfikowany zgodnie z wymaganiami dla aplikacji do uruchomienia. W takich przypadkach należy skontaktować się z niezależnym dostawcą oprogramowania (ISV), aby aplikacja uaktualnione do uruchamiania na [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] lub nowszej wersji. Aby uzyskać więcej informacji, zobacz [migracji z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Instalowanie programu .NET Framework 1.1 z dysku CD lub Centrum pobierania

Nie jest możliwe ręcznie zainstalowanie programu .NET Framework 1.1 w [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], lub Windows 10. Nie jest już obsługiwany. Jeśli spróbujesz zainstalować pakiet, jest wyświetlany następujący komunikat o błędzie: "Instalator nie może kontynuować, ponieważ ta wersja programu .NET Framework jest niezgodna z jego wcześniej zainstalowaną wersją." Aby rozwiązać ten problem, zainstaluj [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Ta wersja zawiera programu .NET Framework 2.0 (wersja występującego .NET Framework 1.1), który jest obsługiwany w [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]i Windows 10. Zawsze należy spróbować zainstalować aplikację, aby ustalić, jeśli jego zostaną automatycznie zaktualizowane do nowszej wersji programu .NET Framework. Jeśli nie, skontaktuj się z Twojego niezależnego dostawcy oprogramowania aktualizacji aplikacji.

## <a name="see-also"></a>Zobacz także

- [Migracja z programu .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 lub Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)
