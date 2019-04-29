---
title: Instalowanie programu .NET Framework w systemie Windows 10
description: Dowiedz się, jak zainstalować program .NET Framework w systemie Windows 10 lub Windows Server 2016.
author: rlander
ms.author: mairaw
ms.date: 04/18/2019
ms.custom: updateeachrelease
ms.openlocfilehash: c9499e44a6074525c634959e385ee91c03cdf9d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643923"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016-and-later"></a>Instalowanie programu .NET Framework w systemie Windows 10 i Windows Server 2016 lub nowszy

.NET Framework jest wymagana do uruchamiania wielu aplikacji na Windows. Instrukcje w tym artykule powinno pomóc w wersji programu .NET Framework, które należy zainstalować. [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) jest najnowszej dostępnej wersji.

Użytkownik może już korzystać na tej stronie po próby uruchomienia aplikacji i wyświetlanie okna dialogowego na swojej maszynie, podobny do następującego:

![Nie można uruchomić tej aplikacji](./media/this-application-could-not-be-started.png)

## <a name="net-framework-48"></a>.NET Framework 4.8

.NET Framework 4.8 jest dołączony do:

* [Usługa Windows Update 10 maja 2019 r.](https://support.microsoft.com/help/4028685/windows-10-get-the-update)

> [!div class="button"]
> [Pobierz program .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

[.NET framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) może służyć do uruchamiania aplikacji dla programu .NET Framework 4.0, za pośrednictwem 4.7.2.

Możesz zainstalować [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) na:

* Windows 10 października 2018 aktualizacja (wersja 1809)
* Windows 10 kwietnia 2018 r. Updae (w wersji 1803)
* Windows 10 Fall Creators Update (wersja 1709)
* Windows 10 Creators Update (wersja 1703)
* Aktualizacja Rocznicowa systemu Windows 10 (wersja 1607)
* Windows Server 2019
* W systemie Windows Server w wersji 1809
* W systemie Windows Server w wersji 1803
* Windows Server 2016

.NET Framework 4.8 nie jest obsługiwane na:

* Windows 10 1507
* Windows 10 1511

Jeśli używasz systemu Windows 10 1507 i 1511 i chcesz zainstalować .NET Framework 4.8, należy najpierw uaktualnić do nowszej wersji systemu Windows 10.

## <a name="net-framework-462"></a>.NET Framework 4.6.2

[Platformy .NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) jest najnowszej obsługiwanej wersji .NET Framework w systemie Windows 10 1507 i 1511.

.NET Framework 4.6.2 obsługuje aplikacje są kompilowane dla programu .NET Framework 4.0, za pośrednictwem 4.6.2.

## <a name="net-framework-35"></a>Program .NET Framework 3,5

Postępuj zgodnie z instrukcjami, aby zainstalować [.NET Framework 3.5 w systemie Windows 10](dotnet-35-windows-10.md).

.NET Framework 3.5 obsługuje aplikacje są kompilowane dla programu .NET Framework 1.0 za pośrednictwem 3.5.

## <a name="additional-information"></a>Dodatkowe informacje

.NET framework w wersji 4.x są aktualizacje w miejscu do wcześniejszych wersji. Oznacza to, że:

- Może mieć tylko jedną wersję programu .NET Framework 4.x, zainstalowana na tym komputerze.

- Nie można zainstalować starszej wersji programu .NET Framework na komputerze, jeśli jest już zainstalowana nowsza wersja.

- wersje programu .NET Framework 4.x, może służyć do uruchamiania aplikacji dla programu .NET Framework 4.0, za pomocą tej wersji. Na przykład .NET Framework 4.7 może służyć do uruchamiania aplikacji dla programu .NET Framework 4.0, za pośrednictwem 4.7. Najnowsza wersja (.NET Framework 4.8) może służyć do uruchamiania aplikacji utworzonych za pomocą wszystkich wersji programu .NET Framework, począwszy od 4.0.

Aby uzyskać listę wszystkich wersji programu .NET Framework jest dostępna do pobrania, zobacz [pobiera .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) strony.

## <a name="help"></a>Help

Jeśli nie można pobrać poprawną wersję programu .NET Framework zainstalowana, możesz to zrobić [kontakt z firmą Microsoft w celu uzyskania pomocy](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).

## <a name="see-also"></a>Zobacz także

- [Pliki do pobrania platformy .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)
- [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
- [Instalowanie programu .NET Framework dla deweloperów](guide-for-developers.md)
