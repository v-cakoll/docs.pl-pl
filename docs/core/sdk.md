---
title: Omówienie zestawu .NET core SDK
description: Dowiedz się o .NET Core SDK, która stanowi zestaw bibliotek i narzędzi służących do tworzenia projektów .NET Core.
ms.date: 05/13/2019
ms.technology: dotnet-cli
ms.openlocfilehash: f56d7238eaaaa677db38430358ce94890632469e
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959230"
---
# <a name="net-core-sdk-overview"></a>Omówienie zestawu .NET core SDK

.NET core Software Development Kit (SDK) to zbiór bibliotek i narzędzi, które umożliwiają deweloperom tworzenie aplikacji .NET Core oraz bibliotek. Zawiera następujące składniki, które są używane do tworzenia i uruchamiania aplikacji:

- Narzędzia wiersza polecenia platformy .NET Core.
- Biblioteki .NET core i środowiska uruchomieniowego.
- `dotnet` [Sterownika](/tools/index.md#driver).

## <a name="acquiring-the-net-core-sdk"></a>Pobieranie zestawu .NET Core SDK

Podobnie jak w przypadku dowolnych narzędzi, najpierw jest Pobierz narzędzia do komputera. Zależnie od scenariusza można zainstalować zestawu SDK przy użyciu jednej z następujących metod:

- Za pomocą natywnych instalatorów.
- Użyj skryptu powłoki instalacji.

Natywnych instalatorów przede wszystkim są przeznaczone dla dewelopera maszyn. Zestaw SDK jest dystrybuowane przy użyciu mechanizmu natywnych instalacji każdej z obsługiwanych platform, takich jak pakiety DEB na pakiety MSI lub Ubuntu na Windows. Te pliki instalacyjne, instalowanie i konfigurowanie środowiska odpowiednio do potrzeb użytkownikowi korzystanie z zestawu SDK natychmiast po zakończeniu instalacji. Jednak również wymagają uprawnień administracyjnych na komputerze. Można znaleźć zestawu SDK do zainstalowania na [pobiera .NET](https://dotnet.microsoft.com/download) strony.

Z drugiej strony, skryptów instalacji nie wymagają uprawnień administracyjnych. Jednak są również nie należy instalować wszystkie wstępnie wymagane składniki na komputerze; należy ręcznie zainstalować wszystkie wymagania wstępne. Skrypty są przeznaczone głównie na potrzeby konfigurowania serwerów kompilacji lub gdy chcesz zainstalować narzędzia bez uprawnień administratora (Uwaga zastrzeżenie: wymagania wstępne powyżej). Więcej informacji można znaleźć [zainstalować odwołanie do skryptu](tools/dotnet-install-script.md) artykułu. Jeśli interesuje Cię sposobu konfigurowania zestawu SDK na serwerze kompilacji ciągłej integracji, zobacz [przy użyciu zestawu .NET Core SDK i narzędzia w ciągłej integracji (CI)](tools/using-ci-with-cli.md) artykułu.

Domyślnie zestaw SDK instaluje się w sposób "side-by-side" (SxS), co oznacza, że wiele wersji narzędzi interfejsu wiersza polecenia mogą współistnieć na jednym komputerze w danym momencie. Jak wersja pobiera pobrane po uruchomieniu polecenia interfejsu wiersza polecenia zostało wyjaśnione bardziej szczegółowo w [wybierz wersję platformy .NET Core do użycia](/versions/selection.md) artykułu.

## <a name="see-also"></a>Zobacz także

- [.NET Core CLI](tools/index.md)
- [Omówienie przechowywania wersji platformy .NET core](/versions/index.md)
- [Jak usunąć środowisko uruchomieniowe programu .NET Core i zestawu SDK](versions/remove-runtime-sdk-versions.md)
- [Wybierz wersję platformy .NET Core do użycia](/versions/selection.md)
