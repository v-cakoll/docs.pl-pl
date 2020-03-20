---
title: Uruchamianie aplikacji programu .NET Framework 1.1 w systemie Windows 8, Windows 8.1 lub Windows 10
description: W tym artykule opisano sposób obsługi aplikacji, które wymagają programu .NET Framework 1.1, który nie jest już obsługiwany w wielu wersjach systemu operacyjnego Windows.
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 28bf3669c24fdd8a6bf45f57059c2953c5ab27dd
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79506973"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Uruchamianie aplikacji programu .NET Framework 1.1 w systemie Windows 8, Windows 8.1 lub Windows 10

Program .NET Framework 1.1 nie jest obsługiwany w systemach operacyjnych Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 ani Windows 10. W niektórych przypadkach .NET Framework 1.1 jest specjalnie identyfikowany jako wymagane dla aplikacji do uruchomienia. W takich przypadkach należy skontaktować się z niezależnym dostawcą oprogramowania (ISV), aby aplikacja została uaktualniona do uruchomienia w wersji .NET Framework 3.5 z dodatkiem SP1 lub nowszej. Aby uzyskać dodatkowe informacje, zobacz [Migrowanie z programu .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Instalowanie programu .NET Framework 1.1 z dysku CD lub Centrum pobierania

Nie można ręcznie zainstalować programu .NET Framework 1.1 w systemach Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 lub Windows 10. Nie jest już obsługiwany. Jeśli spróbujesz zainstalować pakiet, zostanie wyświetlony następujący komunikat o błędzie: "Instalator nie może kontynuować, ponieważ ta wersja programu .NET Framework jest niezgodna z wcześniej zainstalowaną wersją." Aby rozwiązać ten problem, zainstaluj [program .NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Ta wersja zawiera program .NET Framework 2.0 (wydanie następujące po programie .NET Framework 1.1), który jest obsługiwany w systemach Windows 8, Windows 8.1 i Windows 10. Należy zawsze spróbować zainstalować aplikację najpierw, aby ustalić, czy zostanie ona automatycznie zaktualizowana do nowszej wersji programu .NET Framework. Jeśli tak się nie stanie, skontaktuj się z niezależną firmą, aby uzyskać aktualizację aplikacji.

## <a name="see-also"></a>Zobacz też

- [Migracja z programu .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalowanie programu .NET Framework 3.5 w systemie Windows 10, Windows 8.1 lub Windows 8](dotnet-35-windows-10.md)
