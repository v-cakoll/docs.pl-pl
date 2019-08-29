---
title: Instalowanie .NET Framework w systemie Windows 10
description: Dowiedz się, jak zainstalować .NET Framework w systemie Windows 10 lub Windows Server 2016.
author: rlander
ms.author: mairaw
ms.date: 04/18/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 33805230e0aa6c75443773d60e73f9463ee1fde5
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106545"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016-and-later"></a>Instalowanie .NET Framework w systemach Windows 10 i Windows Server 2016 i nowszych

.NET Framework jest wymagane do uruchamiania wielu aplikacji w systemie Windows. Instrukcje zawarte w tym artykule powinny pomóc w zainstalowaniu wymaganych wersji .NET Framework. [.NET Framework 4,8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) jest najnowszą dostępną wersją.

Na tej stronie może nastąpić próba uruchomienia aplikacji i wyświetlenia okna dialogowego na maszynie podobnej do następującego:

![Nie można uruchomić tej aplikacji](./media/this-application-could-not-be-started.png)

## <a name="net-framework-48"></a>.NET Framework 4,8

.NET Framework 4,8 jest dołączony do:

- [Aktualizacja systemu Windows 10 maja 2019](https://support.microsoft.com/help/4028685/windows-10-get-the-update)

> [!div class="button"]
> [Pobierz .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

[.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) może służyć do uruchamiania aplikacji skompilowanych dla .NET Framework 4,0 za pomocą 4.7.2.

[.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) można zainstalować w:

- Aktualizacja systemu Windows 10 październik 2018 (wersja 1809)
- Aktualizacja systemu Windows 10 z kwietnia 2018 (wersja 1803)
- Aktualizacja systemu Windows 10 dla twórców (wersja 1709)
- Aktualizacja systemu Windows 10 dla twórców (wersja 1703)
- Rocznicowa Aktualizacja systemu Windows 10 (wersja 1607)
- Windows Server 2019
- System Windows Server w wersji 1809
- System Windows Server w wersji 1803
- Windows Server 2016

.NET Framework 4,8 nie jest obsługiwana w:

- Windows 10 1507
- Windows 10 1511

Jeśli używasz systemu Windows 10 1507 lub 1511 i chcesz zainstalować .NET Framework 4,8, musisz najpierw przeprowadzić uaktualnienie do nowszej wersji systemu Windows 10.

## <a name="net-framework-462"></a>.NET Framework 4.6.2

[.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345) to najnowsza obsługiwana wersja .NET Framework w systemach Windows 10 1507 i 1511.

.NET Framework 4.6.2 obsługuje aplikacje skompilowane dla .NET Framework 4,0 do 4.6.2.

## <a name="net-framework-35"></a>Program .NET Framework 3,5

Postępuj zgodnie z instrukcjami, aby zainstalować [.NET Framework 3,5 w systemie Windows 10](dotnet-35-windows-10.md).

.NET Framework 3,5 obsługuje aplikacje skompilowane dla .NET Framework 1,0 do 3,5.

## <a name="additional-information"></a>Dodatkowe informacje

Wersje .NET Framework 4. x są aktualizacjami w miejscu do wcześniejszych wersji. Oznacza to następujące kwestie:

- Na maszynie może być zainstalowana tylko jedna wersja .NET Framework 4. x.

- Jeśli nowsza wersja jest już zainstalowana, nie można zainstalować starszej wersji .NET Framework na maszynie.

- 4. x wersje .NET Framework mogą służyć do uruchamiania aplikacji skompilowanych dla .NET Framework 4,0 za pomocą tej wersji. Na przykład .NET Framework 4,7 może służyć do uruchamiania aplikacji skompilowanych dla .NET Framework 4,0 do 4,7. Najnowsza wersja (.NET Framework 4,8) może służyć do uruchamiania aplikacji skompilowanych ze wszystkimi wersjami .NET Framework, począwszy od 4,0.

Aby uzyskać listę wszystkich wersji .NET Framework dostępnych do pobrania, zobacz stronę [pliki do pobrania platformy .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) .

## <a name="help"></a>Help

Jeśli nie możesz uzyskać zainstalowanej poprawnej wersji .NET Framework, możesz [skontaktować się z firmą Microsoft w celu uzyskania pomocy](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).

## <a name="see-also"></a>Zobacz także

- [Pliki do pobrania dla platformy .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)
- [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
- [Zainstaluj .NET Framework dla deweloperów](guide-for-developers.md)
