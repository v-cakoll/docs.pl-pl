---
title: global.json — omówienie
description: Dowiedz się, jak używać pliku Global. JSON do ustawiania wersji zestaw .NET Core SDK podczas uruchamiania poleceń interfejs wiersza polecenia platformy .NET Core.
ms.date: 12/03/2018
ms.custom: updateeachrelease, seodec18
ms.openlocfilehash: 2c1fec102993b61e1eb699e8d3508b773302f569
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117435"
---
# <a name="globaljson-overview"></a>global.json — omówienie

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

Plik *Global. JSON* pozwala określić, która wersja zestaw .NET Core SDK jest używana podczas uruchamiania poleceń interfejs wiersza polecenia platformy .NET Core. Wybór zestaw .NET Core SDK jest niezależny od określania środowiska uruchomieniowego projektu. Wersja zestaw .NET Core SDK wskazuje, które wersje narzędzi interfejs wiersza polecenia platformy .NET Core są używane. Ogólnie rzecz biorąc, chcesz użyć najnowszej wersji narzędzi, dlatego plik *Global. JSON* nie jest potrzebny.

Aby uzyskać więcej informacji na temat określania środowiska uruchomieniowego, zobacz [platforme docelowe](../../standard/frameworks.md).

Zestaw .NET Core SDK szuka pliku *Global. JSON* w bieżącym katalogu roboczym (który nie musi być taki sam jak katalog projektu) lub jednego z jego katalogów nadrzędnych.

## <a name="globaljson-schema"></a>global.json schema

### <a name="sdk"></a>sdk

Wpisz: Obiekt

Określa informacje o zestaw .NET Core SDK do wybrania.

#### <a name="version"></a>version

Wpisz: String

Wersja zestaw .NET Core SDK do użycia.

Należy zauważyć, że to pole:

- Nie ma obsługi obsługi symboli wieloznacznych, czyli należy określić pełny numer wersji.
- Nie obsługuje zakresów wersji.

Poniższy przykład pokazuje zawartość pliku *Global. JSON* :

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>Global. JSON i interfejs wiersza polecenia platformy .NET Core

Warto wiedzieć, które wersje są dostępne w celu ustawienia jednej w pliku *Global. JSON* . Pełną listę obsługiwanych zestawów SDK można znaleźć na stronie [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) . Począwszy od zestawu SDK platformy .NET Core 2,1, możesz uruchomić następujące polecenie, aby sprawdzić, które wersje zestawu SDK są już zainstalowane na maszynie:

```dotnetcli
dotnet --list-sdks
```

Aby zainstalować dodatkowe zestaw .NET Core SDK wersje na komputerze, odwiedź stronę [pobieranie platformy .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .

Nowy plik *Global. JSON* można utworzyć w bieżącym katalogu, wykonując polecenie [dotnet New](dotnet-new.md) , podobnie jak w poniższym przykładzie:

```dotnetcli
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a>Reguły dopasowania

> [!NOTE]
> Reguły dopasowania podlegają AppHost, który jest częścią środowiska uruchomieniowego platformy .NET Core.
> Najnowsza wersja hosta jest używana w przypadku, gdy wiele programów uruchomieniowych jest zainstalowanych obok siebie.

Począwszy od platformy .NET Core 2,0, stosowane są następujące reguły podczas określania, która wersja zestawu SDK ma być używana:

- Jeśli nie odnaleziono pliku *Global. JSON* lub plik *Global. JSON* nie określa wersji zestawu SDK, zostanie użyta Najnowsza zainstalowana wersja zestawu SDK. Najnowsza wersja zestawu SDK może być wydaniem lub wersjami wstępnymi — numer najwyższej wersji usługi WINS.
- Jeśli *Global. JSON* określi wersję zestawu SDK:
  - Jeśli określona wersja zestawu SDK zostanie znaleziona na komputerze, używana jest dokładna wersja.
  - Jeśli na maszynie nie można znaleźć określonej wersji zestawu SDK, zostanie użyta Najnowsza zainstalowana **wersja poprawki** zestawu SDK. Najnowsza zainstalowana **wersja poprawki** zestawu SDK może być wydaniem lub w wersji wstępnej — najwyższa wersja usługi WINS. W przypadku programu .NET Core 2,1 lub nowszego **wersje poprawek** niższe niż określona **wersja poprawki** są ignorowane w wyborze zestawu SDK.
  - Jeśli nie można znaleźć określonej wersji zestawu SDK i odpowiedniej **wersji poprawki** zestawu SDK, zostanie zgłoszony błąd.

Wersja zestawu SDK składa się obecnie z następujących części:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Wersja funkcji** zestaw .NET Core SDK jest reprezentowana przez pierwszą cyfrę (`x`) w ostatniej części cyfry (`xyz`) dla wersji zestawu SDK 2.1.100 i wyższych. Ogólnie rzecz biorąc zestaw .NET Core SDK ma szybszy cykl wydawniczy niż .NET Core.

**Wersja poprawki** jest definiowana przez ostatnie dwie cyfry (`yz`) w ostatniej części cyfry (`xyz`) dla wersji zestawu SDK 2.1.100 i wyższych. `2.1.300` Na przykład jeśli określisz jako wersję zestawu SDK, wybór zestawu SDK znajdzie się do `2.1.399` , ale `2.1.400` nie jest traktowany jako `2.1.300`wersja poprawki dla programu.

Wersje `2.1.100` zestaw .NET Core SDK za `2.1.201` pomocą zostały wydane podczas przejścia między schematami numerów wersji `xyz` i nie obsługują poprawnie notacji. Zdecydowanie zalecamy, aby określić te wersje w pliku *Global. JSON* , że określone wersje znajdują się na komputerach docelowych.

W przypadku wybrania wersji zestaw .NET Core SDK 1. x, jeśli określono wersję i nie znaleziono dokładnego dopasowania, użyto najnowszej zainstalowanej wersji zestawu SDK. Najnowsza wersja zestawu SDK może być wydaniem lub wersjami wstępnymi — numer najwyższej wersji usługi WINS.

## <a name="troubleshooting-build-warnings"></a>Rozwiązywanie problemów z ostrzeżeniami kompilacji

> [!WARNING]
> Pracujesz z wersją zapoznawczą zestaw .NET Core SDK. Możesz zdefiniować wersję zestawu SDK za pośrednictwem pliku Global. JSON w bieżącym projekcie. Więcej o<https://go.microsoft.com/fwlink/?linkid=869452>

To ostrzeżenie wskazuje, że projekt jest kompilowany przy użyciu wersji zapoznawczej zestaw .NET Core SDK, zgodnie z opisem w sekcji [reguły dopasowywania](#matching-rules) . Wersje zestaw .NET Core SDK mają historię i zobowiązanie o wysokiej jakości. Jeśli jednak nie chcesz korzystać z wersji zapoznawczej, Dodaj plik *Global. JSON* do struktury hierarchii projektu, aby określić wersję zestawu SDK, która ma być używana, i `dotnet --list-sdks` potwierdzić, że wersja jest zainstalowana na maszynie. Po wydaniu nowej wersji, aby użyć nowej wersji, należy usunąć plik *Global. JSON* lub zaktualizować go tak, aby korzystał z nowszej wersji.

> [!WARNING]
> Projekt startowy "{startupProject}" wskazuje platformę ". NETCoreApp "wersja" {targetFrameworkVersion} ". Ta wersja narzędzi wiersza polecenia Entity Framework Core .NET obsługuje tylko wersję 2,0 lub nowszą. Aby uzyskać informacje na temat używania starszych wersji narzędzi, zobacz.<https://go.microsoft.com/fwlink/?linkid=871254>

Począwszy od zestawu SDK programu .NET Core 2,1 (wersja 2.1.300) `dotnet ef` , polecenie znajduje się w zestawie SDK. To ostrzeżenie wskazuje, że projekt jest ukierunkowany na EF Core 1,0 lub 1,1, co nie jest zgodne z zestawem SDK .NET Core 2,1 i nowszymi wersjami. Aby skompilować projekt, zainstaluj program .NET Core 2,0 SDK (wersja 2.1.201) i jego wcześniejszą wersję na maszynie i zdefiniuj żądaną wersja zestawu SDK przy użyciu pliku *Global. JSON* . Aby uzyskać więcej informacji na `dotnet ef` temat tego polecenia, zobacz [EF Core narzędzia wiersza polecenia programu .NET](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Zobacz także

- [Jak są rozwiązywane zestawy SDK projektu](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
