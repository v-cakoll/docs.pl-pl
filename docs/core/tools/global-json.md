---
title: Omówienie Global.JSON
description: Dowiedz się, jak za pomocą plik global.json Ustaw wersję .NET Core SDK, podczas uruchamiania poleceń interfejsu wiersza polecenia platformy .NET Core.
ms.date: 12/03/2018
ms.custom: updateeachrelease, seodec18
ms.openlocfilehash: e0f929a049812cac6f62e5218629c9b0add83de8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647976"
---
# <a name="globaljson-overview"></a>Omówienie Global.JSON

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

*Global.json* pliku umożliwia definiowanie, która wersja programu .NET Core SDK jest używany podczas uruchamiania poleceń interfejsu wiersza polecenia platformy .NET Core. Wybieranie zestawu .NET Core SDK jest niezależna od określając docelowy system operacyjny projektu w czasie wykonywania. Wersja zestawu SDK programu .NET Core wskazuje, które wersje narzędzi interfejsu wiersza polecenia platformy .NET Core są używane. Ogólnie rzecz biorąc, do którego chcesz użyć najnowszej wersji narzędzia, więc nie *global.json* potrzebny jest plik.

Aby uzyskać więcej informacji na temat określania środowiska uruchomieniowego zamiast tego zobacz [ustalać platformy docelowe](../../standard/frameworks.md).

Wyszukuje zestaw .NET core SDK *global.json* plik w bieżącym katalogu roboczym (co nie jest zawsze taki sam jak katalog projektu) lub jeden z jego katalogi nadrzędne.

## <a name="globaljson-schema"></a>global.json schema

### <a name="sdk"></a>sdk

Wpisz: Obiekt

Określa informacje dotyczące zestawu .NET Core SDK, aby wybrać.

#### <a name="version"></a>version

Wpisz: String

Wersja zestawu .NET Core SDK do użycia.

Należy pamiętać, że w tym polu:

- Nie ma obsługi symboli wieloznacznych, oznacza to, że pełny numer wersji musi być określony.
- Nie obsługuje zakresów wersji.

W poniższym przykładzie pokazano zawartość *global.json* pliku:

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>Global.JSON i zestawu .NET Core interfejsu wiersza polecenia

Warto wiedzieć, które wersje są dostępne, aby ustawić jeden *global.json* pliku. Można znaleźć pełną listę obsługiwanych dostępnych zestawów SDK na [pobiera .NET](https://www.microsoft.com/net/download/all) lokacji. Począwszy od zestawu SDK programu .NET Core 2.1 można uruchomić następujące polecenie, aby sprawdzić, które wersje zestawu SDK są już zainstalowane na komputerze:

```console
dotnet --list-sdks
```

Aby zainstalować dodatkowe wersje programu .NET Core SDK na maszynie, odwiedź stronę [pobiera .NET](https://www.microsoft.com/net/download/all) lokacji.

Można utworzyć nową *global.json* plik w bieżącym katalogu, wykonując [dotnet nowe](dotnet-new.md) polecenia podobnego do poniższego przykładu:

```console
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a>Reguł dopasowania

> [!NOTE]
> Reguł dopasowania podlegają apphost, który jest częścią środowiska uruchomieniowego .NET Core.
> Najnowszą wersję hosta jest używana, jeśli masz wiele środowisk uruchomieniowych zainstalowane obok siebie.

Począwszy od programu .NET Core 2.0, obowiązują następujące reguły podczas ustalania, która wersja zestawu SDK do użycia:

- Jeśli nie *global.json* znajduje się plik lub *global.json* nie określa wersji zestawu SDK, jego Najnowsza zainstalowana wersja zestawu SDK jest używany. Najnowsza wersja zestawu SDK może być wersji lub wersji wstępnej — najwyższy wins numeru wersji.
- Jeśli *global.json* Określ wersję zestawu SDK:
  - Jeśli określonej wersji zestawu SDK znajduje się na komputerze, że dokładna wersja jest używana.
  - Jeśli nie można odnaleźć określonej wersji zestawu SDK na maszynie, najnowsze zainstalowany zestaw SDK **wersja poprawki zabezpieczeń** to wersja jest używana. Najnowsze zainstalowany zestaw SDK **wersja poprawki zabezpieczeń** może być wersji lub wersji wstępnej — najwyższa wersja numeru wins. W programie .NET Core 2.1 lub nowszym **poprawki wersji** niższa niż **wersja poprawki zabezpieczeń** określonego są ignorowane w zaznaczeniu zestawu SDK.
  - Jeśli określona wersja zestawu SDK i właściwy zestaw SDK **wersja poprawki zabezpieczeń** nie zostanie znaleziony, zostanie zgłoszony błąd.

Wersja zestawu SDK obecnie składa się z następujących elementów:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Funkcji wersji** programu .NET Core SDK jest reprezentowany przez pierwszą (`x`) w ostatniej części numeru (`xyz`) dla wersji zestawu SDK 2.1.100 lub nowszy. Ogólnie rzecz biorąc .NET Core SDK ma szybszy cyklu tworzenia wydań niż .NET Core.

**Wersja poprawki zabezpieczeń** jest definiowany przez dwie ostatnie cyfry (`yz`) w ostatniej części numeru (`xyz`) dla wersji zestawu SDK 2.1.100 lub nowszy. Na przykład, jeśli określisz `2.1.300` jako wersję zestawu SDK, wybór zestawu SDK znajduje się maksymalnie `2.1.399` , ale `2.1.400` nie jest uważany za wersję poprawki dla `2.1.300`.

Wersje programu .NET core SDK `2.1.100` za pośrednictwem `2.1.201` zostały wydane podczas przejścia między schematami numeru wersji i nie zapewnia prawidłowej obsługi `xyz` notacji. Zdecydowanie zaleca się Jeśli określisz te wersje w *global.json* pliku, który można zapewnić, że określone wersje są na komputerach docelowych.

Przy użyciu zestawu SDK programu .NET Core 1.x, jeśli określona wersja i dokładnego dopasowania został znaleziony, użyto jego Najnowsza zainstalowana wersja zestawu SDK. Najnowsza wersja zestawu SDK może być wersji lub wersji wstępnej — najwyższy wins numeru wersji.

## <a name="troubleshooting-build-warnings"></a>Rozwiązywanie problemów z ostrzeżenia kompilacji

> [!WARNING]
> Pracujesz z wersję zapoznawczą programu .NET Core SDK. Wersja zestawu SDK przy użyciu pliku global.json można zdefiniować w bieżącym projekcie. Więcej na stronie <https://go.microsoft.com/fwlink/?linkid=869452>

To ostrzeżenie wskazuje, że projekt jest kompilowany przy użyciu zestawu .NET Core SDK w wersji zapoznawczej zgodnie z objaśnieniem w [reguł dopasowania](#matching-rules) sekcji. Wersje programu .NET core SDK ma historię i zaangażowanie on wysokiej jakości. Jeśli nie chcesz użyć wersji zapoznawczej, jednak dodać *global.json* pliku do struktury projektu hierarchii w celu określenia którą wersję zestawu SDK i wykorzystaj `dotnet --list-sdks` aby upewnić się, że na komputerze jest zainstalowana wersja. Po wydaniu nowej wersji do nowej wersji, albo usuń *global.json* pliku, lub zaktualizuj go do korzystania z nowszej wersji.

> [!WARNING]
> Platformy elementy docelowe projektu "{Projekt startowy}" Uruchamianie ". Element NETCoreApp "wersja"{targetFrameworkVersion}". Ta wersja narzędzia wiersza polecenia programu Entity Framework Core .NET obsługuje tylko w wersji 2.0 lub nowszej. Aby uzyskać informacji na temat używania starszych wersji narzędzia Zobacz <https://go.microsoft.com/fwlink/?linkid=871254>

Począwszy od .NET Core 2.1 SDK (wersja 2.1.300) `dotnet ef` polecenia jest uwzględniony w zestawie SDK. To ostrzeżenie wskazuje, że projekt jest ukierunkowany EF Core 1.0 i 1.1, która nie jest zgodna z zestawu SDK programu .NET Core 2.1 i nowsze wersje. Aby skompilować projekt, zainstaluj zestaw .NET Core 2.0 SDK (wersja 2.1.201) i starszych na Twojej maszynie i definiują żądany zestaw SDK w wersji przy użyciu *global.json* pliku. Aby uzyskać więcej informacji na temat `dotnet ef` polecenia, zobacz [narzędzia wiersza polecenia platformy .NET Core EF](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Zobacz także

- [Jak są rozwiązywane projektów zestawów SDK](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)