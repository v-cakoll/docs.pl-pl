---
title: Przegląd zestaw .NET Core SDK
description: Dowiedz się więcej na temat zestaw .NET Core SDK, czyli zestawu bibliotek i narzędzi służących do tworzenia projektów platformy .NET Core.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 0231c08f780455c4956c044815a2e80cef4d827e
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733392"
---
# <a name="net-core-sdk-overview"></a>Przegląd zestaw .NET Core SDK

.NET Core Software Development Kit (SDK) to zestaw bibliotek i narzędzi umożliwiających deweloperom tworzenie aplikacji i bibliotek platformy .NET Core. Zawiera następujące składniki, które są używane do kompilowania i uruchamiania aplikacji:

- Narzędzia interfejs wiersza polecenia platformy .NET Core.
- Biblioteki i środowisko uruchomieniowe platformy .NET Core.
- `dotnet` [Sterownik](tools/index.md#driver).

## <a name="acquiring-the-net-core-sdk"></a>Uzyskiwanie zestaw .NET Core SDK

Podobnie jak w przypadku każdego narzędzia, pierwszym krokiem jest uzyskanie narzędzi do komputera. W zależności od danego scenariusza można zainstalować zestaw SDK przy użyciu jednej z następujących metod:

- Użyj natywnych instalatorów.
- Użyj skryptu powłoki instalacji.

Natywne Instalatory są przeznaczone głównie dla maszyn dewelopera. Zestaw SDK jest dystrybuowany przy użyciu każdego obsługiwanego natywnego mechanizmu instalacji platformy, takiego jak pakiety DEB w pakietach Ubuntu i MSI w systemie Windows. Te Instalatory instalują i konfigurują środowisko jako konieczne, aby użytkownik mógł korzystać z zestawu SDK bezpośrednio po instalacji. Jednak wymagają one również uprawnień administracyjnych na komputerze. Zestaw SDK można znaleźć na stronie [pliki do pobrania platformy .NET](https://dotnet.microsoft.com/download) .

Zainstaluj skrypty, z drugiej strony, nie wymagaj uprawnień administracyjnych. Jednak nie instalują one również wymagań wstępnych dotyczących maszyny; należy ręcznie zainstalować wszystkie wymagania wstępne. Skrypty są przeznaczone głównie do konfigurowania serwerów kompilacji lub instalowania narzędzi bez uprawnień administratora (należy zanotować powyższe zastrzeżenie dotyczące wymagań wstępnych). Więcej informacji można znaleźć w artykule [Informacje o skrypcie instalacji](tools/dotnet-install-script.md) . Jeśli interesuje Cię sposób konfigurowania zestawu SDK na serwerze kompilacji CI, zobacz artykuł [Using zestaw .NET Core SDK and Tools in Continuous Integration (ci)](tools/using-ci-with-cli.md) .

Domyślnie zestaw SDK jest instalowany w sposób "Side-by-side" (SxS), co oznacza, że wiele wersji narzędzi interfejsu wiersza polecenia może współistnieć w danym momencie na pojedynczym komputerze. Sposób pobierania wersji podczas uruchamiania poleceń interfejsu wiersza polecenia znajduje się bardziej szczegółowo w artykule [Wybieranie wersji .NET Core do użycia](versions/selection.md) .

## <a name="see-also"></a>Zobacz także

- [.NET Core CLI](tools/index.md)
- [Omówienie wersji platformy .NET Core](versions/index.md)
- [Jak usunąć środowisko uruchomieniowe programu .NET Core i zestaw SDK](versions/remove-runtime-sdk-versions.md)
- [Wybierz wersję platformy .NET Core do użycia](versions/selection.md)
