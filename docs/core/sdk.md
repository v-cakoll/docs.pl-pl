---
title: Omówienie zestawu .NET Core SDK
description: Dowiedz się więcej o sdk .NET Core, który jest zestawem bibliotek i narzędzi używanych do tworzenia projektów .NET Core.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: c2723e0e28c889f91f79ea3c0b26aa38f69fb41c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157469"
---
# <a name="net-core-sdk-overview"></a>Omówienie zestawu .NET Core SDK

Zestaw SDK .NET Core to zestaw bibliotek i narzędzi, które umożliwiają deweloperom tworzenie aplikacji i bibliotek .NET Core. Zawiera następujące składniki, które są używane do tworzenia i uruchamiania aplikacji:

- Cli rdzenia .NET.
- Biblioteki .NET Core i czas wykonywania.
- `dotnet` [Kierowca](tools/index.md#driver).

## <a name="acquiring-the-net-core-sdk"></a>Pobieranie sdk .NET Core

Podobnie jak w przypadku każdego oprzyrządowania, pierwszą rzeczą jest, aby narzędzia do maszyny. W zależności od scenariusza można zainstalować zestaw SDK przy użyciu jednej z następujących metod:

- Użyj instalatorów natywnych.
- Użyj skryptu powłoki instalacji.

Instalatory natywne są przeznaczone głównie dla maszyn deweloperskich. Zestaw SDK jest dystrybuowany przy użyciu natywnego mechanizmu instalacji każdej obsługiwanej platformy, takiego jak pakiety DEB w pakietach Ubuntu lub MSI w systemie Windows. Instalatorzy te instalują i konfigurują środowisko zgodnie z potrzebami użytkownika do korzystania z zestawu SDK natychmiast po zainstalowaniu. Jednak wymagają one również uprawnień administracyjnych na komputerze. Zestaw SDK do zainstalowania można znaleźć na stronie [pobierania .NET.](https://dotnet.microsoft.com/download)

Z drugiej strony instalowanie skryptów nie wymaga uprawnień administracyjnych. Jednak nie instalują żadnych wymagań wstępnych na komputerze; należy zainstalować wszystkie wymagania wstępne ręcznie. Skrypty są przeznaczone głównie do konfigurowania serwerów kompilacji lub gdy chcesz zainstalować narzędzia bez uprawnień administratora (należy pamiętać o zastrzeżeniu wymagań wstępnych powyżej). Więcej informacji można znaleźć w artykule odwołania do [skryptu instalacji.](tools/dotnet-install-script.md) Jeśli jesteś zainteresowany, jak skonfigurować zestaw SDK na serwerze kompilacji ciągłej, zobacz [using .NET Core SDK and tools in Continuous Integration (CI)](tools/using-ci-with-cli.md) article and tools in Continuous Integration (CI) article.

Domyślnie zestaw SDK instaluje się w sposób "side-by-side" (SxS), co oznacza, że wiele wersji może współistnieć w danym momencie na jednym komputerze. Sposób pobrania wersji po uruchomieniu poleceń wiersza polecenia wiersza polecenia jest wyjaśniony bardziej szczegółowo w [artykule Wybierz wersję .NET Core.](versions/selection.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie procesora CLI programu .NET Core](tools/index.md)
- [Omówienie wersji programu .NET Core](versions/index.md)
- [Jak usunąć program runtime i sdk programu .NET Core](versions/remove-runtime-sdk-versions.md)
- [Wybierz wersję .NET Core, która ma być używana](versions/selection.md)
