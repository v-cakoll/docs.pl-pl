---
title: Omówienie zestawu SDK .NET core
description: Dowiedz się o .NET Core SDK, czyli zestawowi bibliotek i narzędzi służących do tworzenia projektów .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 5fc04c3ef5a1502251a9caf0b6a5f5809faad5b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-sdk-overview"></a>Omówienie zestawu SDK .NET core 

## <a name="introduction"></a>Wprowadzenie
.NET core Software Development Kit (SDK) to zestaw bibliotek i narzędzia, które umożliwiają deweloperom tworzenie aplikacji platformy .NET Core i bibliotek. To jest pakiet, który najprawdopodobniej uzyska dostęp do deweloperów. 

Ten przewodnik zawiera następujące składniki:

1. Podstawowe narzędzia wiersza polecenia .NET są używane do tworzenia aplikacji
2. Oprogramowanie .NET core (bibliotek i środowiska uruchomieniowego), które umożliwiają aplikacjom zarówno być zbudowany i uruchom
3. `dotnet` Sterownik do uruchomienia [polecenia interfejsu wiersza polecenia](tools/index.md) oraz uruchamiania aplikacji


## <a name="acquiring-the-net-core-sdk"></a>Uzyskiwanie .NET Core SDK
Podobnie jak w przypadku dowolnego narzędzia, najpierw jest aby uzyskać narzędzia do komputera. W zależności od scenariusza możesz użyć natywnych instalatorów Instalacja zestawu SDK lub użyć skryptu powłoki instalacji.

Natywny instalatorów głównie są przeznaczone dla dewelopera maszyny. Zestaw SDK jest dystrybuowane przy użyciu mechanizmu instalacji natywnych każdej z obsługiwanych platform, na przykład DEB pakietów na funkcji MSI lub Ubuntu pakietów w systemie Windows. Te pliki instalacyjne będzie zainstalować i skonfigurować środowisko, zgodnie z potrzebami dla użytkownika korzystanie z zestawu SDK natychmiast po zakończeniu instalacji. Jednak również potrzebują uprawnień administracyjnych na komputerze. Instrukcje instalacji można wyświetlić w [Przewodnik instalacji platformy .NET Core](https://aka.ms/dotnetcoregs).

Instalowanie skryptów, z drugiej strony, nie wymaga uprawnień administracyjnych. Jednak one również nie zostaną zainstalowane wszystkie wstępnie wymagane składniki na komputerze; należy ręcznie zainstalować wszystkie wymagania wstępne. Skrypty są przeznaczone głównie dla ustawienie serwery kompilacji lub gdy chcesz zainstalować narzędzia bez uprawnień administratora (Uwaga zastrzeżenie: wymagania wstępne powyżej). Więcej informacji można znaleźć na [zainstalować temat referencyjny skryptu](tools/dotnet-install-script.md). Jeśli interesuje Cię sposobu konfigurowania zestawu SDK na serwerze kompilacji elementu konfiguracji może potrwać przyjrzeć się [zestawu SDK z serwerami CI](tools/using-ci-with-cli.md) dokumentu. 

Domyślnie zestaw SDK zainstaluje w sposób "side-by-side" (SxS). Oznacza to, że wiele wersji narzędzi interfejsu wiersza polecenia mogą współistnieć na jednym komputerze w danym momencie. Pobiera używania poprawnej wersji to co omówiono bardziej szczegółowo w [sekcji sterowników](tools/index.md#driver) tematu narzędzi wiersza polecenia programu .NET Core.
