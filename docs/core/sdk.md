---
title: Omówienie zestawu SDK programu .NET core
description: Dowiedz się o .NET Core SDK, która stanowi zestaw bibliotek i narzędzi służących do tworzenia projektów .NET Core.
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: f23140166ada0c39d4267a4fd2ba5187b6c13c83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648727"
---
# <a name="net-core-sdk-overview"></a>Omówienie zestawu SDK programu .NET core

.NET core Software Development Kit (SDK) to zbiór bibliotek i narzędzi, które umożliwiają deweloperom tworzenie aplikacji .NET Core oraz bibliotek. To jest pakiet, który najprawdopodobniej uzyska dostęp do deweloperów. 

Zawiera następujące składniki:

1. Podstawowe narzędzia wiersza polecenia platformy .NET są używane do tworzenia aplikacji
2. .NET core (biblioteki i środowisko uruchomieniowe), dzięki czemu aplikacje, które zarówno można skompilować i uruchomić
3. `dotnet` Sterownik do uruchomienia [poleceń interfejsu wiersza polecenia](tools/index.md) oraz uruchamiania aplikacji

## <a name="acquiring-the-net-core-sdk"></a>Pobieranie zestawu .NET Core SDK
Podobnie jak w przypadku dowolnych narzędzi, najpierw jest Pobierz narzędzia do komputera. Zależnie od scenariusza możesz użyć natywnych instalatorów do zainstalowania zestawu SDK lub użyj skryptu powłoki instalacji.

Natywnych instalatorów przede wszystkim są przeznaczone dla dewelopera maszyn. Zestaw SDK jest dystrybuowane przy użyciu mechanizmu natywnych instalacji każdej z obsługiwanych platform, na przykład DEB pakiety na pakiety MSI lub Ubuntu na Windows. Te pliki instalacyjne spowoduje Instalowanie i konfigurowanie środowiska odpowiednio do potrzeb użytkownikowi korzystanie z zestawu SDK natychmiast po zakończeniu instalacji. Jednak również wymagają uprawnień administracyjnych na komputerze. Instrukcje dotyczące instalacji można wyświetlić na [Przewodnik instalacji platformy .NET Core](https://aka.ms/dotnetcoregs).

Z drugiej strony, skryptów instalacji nie wymagają uprawnień administracyjnych. Jednak są również nie zainstaluje wszystkie wstępnie wymagane składniki na komputerze; należy ręcznie zainstalować wszystkie wymagania wstępne. Skrypty są przeznaczone głównie na potrzeby konfigurowania serwerów kompilacji lub gdy chcesz zainstalować narzędzia bez uprawnień administratora (Uwaga zastrzeżenie: wymagania wstępne powyżej). Więcej informacji można znaleźć na [zainstalować temat referencyjny skryptu](tools/dotnet-install-script.md). Jeśli interesują Cię sposobu konfigurowania zestawu SDK na serwerze kompilacji ciągłej integracji, możesz wykonać przyjrzeć się [zestawu SDK z serwerami CI](tools/using-ci-with-cli.md) dokumentu.

Domyślnie zestaw SDK zainstaluje się w sposób "side-by-side" (SxS). Oznacza to, że wiele wersji narzędzi interfejsu wiersza polecenia mogą współistnieć na jednym komputerze w danym momencie. Sposobu poprawna wersja zostanie wykorzystany zostało wyjaśnione bardziej szczegółowo w [sekcji sterownika](tools/index.md#driver) tematu narzędzia wiersza polecenia programu .NET Core.