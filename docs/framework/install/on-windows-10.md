---
title: Zainstaluj program .NET Framework w systemie Windows 10
description: Dowiedz się, jak zainstalować program .NET Framework w systemie Windows 10 lub Windows Server 2016.
author: rlander
ms.author: mairaw
ms.date: 04/10/2018
ms.custom: updateeachrelease
ms.openlocfilehash: cf374f9d1fd7e343e5eba868d3f686784428a2d0
ms.sourcegitcommit: 3d42e1d73e21c35c540dd4adbea23efcbe1b8b0a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270451"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016"></a>Zainstaluj program .NET Framework w systemie Windows 10 i Windows Server 2016

.NET Framework jest wymagana do uruchamiania wielu aplikacji w systemie Windows. Instrukcje w tym artykule powinny pomóc w instalacji wersji systemu .NET Framework, które są potrzebne. [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) jest najnowszej dostępnej wersji.

Użytkownik może następować na tej stronie po próby uruchomienia aplikacji i wyświetlanie okna dialogowego na tym komputerze podobny do następującego:

![Nie można uruchomić tej aplikacji](./media/this-application-could-not-be-started.png)

## <a name="net-framework-472"></a>.NET framework 4.7.2

.NET Framework 4.7.2 jest dołączana do:

* [Usługa Windows Update 10 kwietnia 2018](https://www.microsoft.com/software-download/windows10)

> [!div class="button"]
[.NET Framework 4.7.2 pobrać](https://www.microsoft.com/net/download/thank-you/net472?utm_source=ms-docs&utm_medium=referral)

[.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) może służyć do uruchamiania aplikacji utworzonych dla programu .NET Framework 4.0 za pośrednictwem 4.7.1.

Można zainstalować [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) na:

* Windows 10 spadek twórców aktualizację (wersja 1709)
* Windows 10 twórców aktualizację (wersja 1703)
* Windows 10 Anniversary Update (w wersji 1607)
* W systemie Windows Server w wersji 1709
* Windows Server 2016

.NET Framework 4.7.2 nie jest obsługiwane na:

* Windows 10 1507
* Windows 10 1511

Jeśli używasz systemu Windows 10 1507 lub 1511 i chcesz zainstalować program .NET Framework 4.7.2, należy najpierw uaktualnić do nowszej wersji systemu Windows 10.

## <a name="net-framework-462"></a>.NET Framework 4.6.2

[.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) jest najnowsza wersja obsługiwana wersja platformy .NET w systemie Windows 10 1507 i 1511.

.NET Framework 4.6.2 obsługuje aplikacje dla programu .NET Framework 4.0 za pośrednictwem 4.6.2.

## <a name="net-framework-35"></a>Program .NET Framework 3,5

Postępuj zgodnie z instrukcjami, aby zainstalować [.NET Framework 3.5 w systemie Windows 10](dotnet-35-windows-10.md).

.NET Framework 3.5 obsługuje aplikacje dla programu .NET Framework 1.0 za pośrednictwem 3.5.

## <a name="additional-information"></a>Dodatkowe informacje

Wersje programu .NET framework 4.x, to aktualizacje w miejscu do wcześniejszych wersji. Oznacza to następujące czynności:

- Może mieć tylko jedną wersję systemu .NET Framework 4.x na komputerze jest zainstalowany.

- Nie można zainstalować starszej wersji programu .NET Framework na komputerze, jeśli jest już zainstalowana nowsza wersja.

- wersje programu .NET Framework 4.x może służyć do uruchamiania aplikacji utworzonych dla programu .NET Framework 4.0, za pomocą tej wersji. Na przykład .NET Framework 4.7 może służyć do uruchamiania aplikacji utworzonych dla programu .NET Framework 4.0 za pośrednictwem 4.7. Najnowszą wersję (.NET Framework 4.7.2) może służyć do uruchamiania aplikacji skompilowanej za pomocą wszystkich wersji platformy .NET, począwszy od 4.0.

Aby uzyskać listę wszystkich wersji programu .NET Framework dostępnych do pobrania, zobacz [pobiera .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) strony.

## <a name="help"></a>Pomoc

Jeśli nie można pobrać poprawna wersja Framework .NET zainstalowany, możesz [kontakt z firmą Microsoft w celu uzyskania pomocy](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).

## <a name="see-also"></a>Zobacz także

[Pobieranie .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)   
[Rozwiązywanie problemów z zablokowaną .NET Framework i odinstalowywaniem programu](troubleshoot-blocked-installations-and-uninstallations.md)   
[Zainstaluj program .NET Framework dla deweloperów](guide-for-developers.md)
