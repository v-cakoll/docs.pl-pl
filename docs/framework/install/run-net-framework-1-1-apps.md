---
title: Uruchamianie aplikacji programu .NET Framework 1.1 w systemie Windows 8, Windows 8.1 lub Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aae87b60e207ebe406e863f123e1dc3e56aeb4f7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051934"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Uruchamianie aplikacji programu .NET Framework 1.1 w systemie Windows 8, Windows 8.1 lub Windows 10

.NET Framework 1,1 [!INCLUDE[win8](../../../includes/win8-md.md)]nie jest obsługiwana w systemach operacyjnych, [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], i Windows 10. W niektórych przypadkach .NET Framework 1,1 jest określony jako wymagany do uruchomienia aplikacji. W takich przypadkach należy skontaktować się z niezależnym dostawcą oprogramowania (ISV), aby aplikacja została uaktualniona do działania w .NET Framework 3,5 z dodatkiem SP1 lub nowszym. Aby uzyskać dodatkowe informacje, zobacz [Migrowanie z .NET Framework 1,1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Zainstaluj .NET Framework 1,1 z dysku CD lub Download Center

Nie jest możliwe ręczne zainstalowanie .NET Framework 1,1 [!INCLUDE[win8](../../../includes/win8-md.md)]w systemach [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)],, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]i Windows 10. Nie jest już obsługiwane. Jeśli spróbujesz zainstalować pakiet, zostanie wyświetlony następujący komunikat o błędzie: "Nie można kontynuować instalacji, ponieważ ta wersja .NET Framework jest niezgodna z wcześniej zainstalowaną wersją". Aby rozwiązać ten problem, zainstaluj [.NET Framework 3,5 z dodatkiem SP1](https://www.microsoft.com/download/details.aspx?id=22). Ta wersja zawiera .NET Framework 2,0 (wersja zgodna z .NET Framework 1,1), która jest obsługiwana w [!INCLUDE[win8](../../../includes/win8-md.md)]systemach, [!INCLUDE[win81](../../../includes/win81-md.md)]i Windows 10. Należy zawsze najpierw próbować zainstalować aplikację, aby określić, czy zostanie ona automatycznie zaktualizowana do nowszej wersji .NET Framework. Jeśli nie, skontaktuj się z dostawcą niezależnego dostawcy oprogramowania, aby uzyskać aktualizację aplikacji.

## <a name="see-also"></a>Zobacz także

- [Migracja z programu .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 lub Windows 8](dotnet-35-windows-10.md)
