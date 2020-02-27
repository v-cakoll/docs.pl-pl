---
title: global.json — omówienie
description: Dowiedz się, jak używać pliku Global. JSON do ustawiania wersji zestaw .NET Core SDK podczas uruchamiania poleceń interfejs wiersza polecenia platformy .NET Core.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 70257566e1ff30f5c97212a5e0e3c308c27738b7
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625998"
---
# <a name="globaljson-overview"></a>global.json — omówienie

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach

Plik *Global. JSON* pozwala określić, która wersja zestaw .NET Core SDK jest używana podczas uruchamiania poleceń interfejs wiersza polecenia platformy .NET Core. Wybór zestaw .NET Core SDK jest niezależny od określania środowiska uruchomieniowego projektu. Wersja zestaw .NET Core SDK wskazuje, które wersje interfejs wiersza polecenia platformy .NET Core są używane.

Ogólnie rzecz biorąc, chcesz użyć najnowszej wersji narzędzi zestawu SDK, więc nie jest potrzebny plik *Global. JSON* . W niektórych zaawansowanych scenariuszach możesz chcieć kontrolować wersję narzędzi zestawu SDK, a w tym artykule wyjaśniono, jak to zrobić.

Aby uzyskać więcej informacji na temat określania środowiska uruchomieniowego, zobacz [platforme docelowe](../../standard/frameworks.md).

Zestaw .NET Core SDK szuka pliku *Global. JSON* w bieżącym katalogu roboczym (który nie musi być taki sam jak katalog projektu) lub jednego z jego katalogów nadrzędnych.

## <a name="globaljson-schema"></a>global.json schema

### <a name="sdk"></a>sdk

Typ: `object`

Określa informacje o zestaw .NET Core SDK do wybrania.

#### <a name="version"></a>version

- Typ: `string`

- Dostępne od: .NET Core 1,0 SDK.

Wersja zestaw .NET Core SDK do użycia.

To pole:

- Nie ma obsługi symboli wieloznacznych, czyli należy określić pełny numer wersji.
- Nie obsługuje zakresów wersji.

#### <a name="allowprerelease"></a>allowPrerelease

- Typ: `boolean`

- Dostępne od: .NET Core 3,0 SDK.

Wskazuje, czy program rozpoznawania SDK powinien wziąć pod uwagę wersje wstępne podczas wybierania wersji zestawu SDK do użycia.

Jeśli ta wartość nie zostanie jawnie ustawiona, wartość domyślna zależy od tego, czy korzystasz z programu Visual Studio:

- Jeśli **nie** Jesteś w programie Visual Studio, wartość domyślna to `true`.
- Jeśli używasz programu Visual Studio, zostanie użyty żądany stan wersji wstępnej. Oznacza to, że jeśli korzystasz z wersji zapoznawczej programu Visual Studio lub ustawisz podglądy **użycia opcji zestaw .NET Core SDK** (w obszarze **narzędzia** > **Opcje** > **środowisku** > **funkcji wersji zapoznawczej**), wartość domyślna to `true`; w przeciwnym razie `false`.

#### <a name="rollforward"></a>Przeniesienia

- Typ: `string`

- Dostępne od: .NET Core 3,0 SDK.

Zasady przyciągania do przodu, które mają być używane podczas wybierania wersji zestawu SDK, jako rezerwy w przypadku braku określonej wersji zestawu SDK lub jako dyrektywy do korzystania z nowszej wersji. Należy określić [wersję](#version) z wartością `rollForward`, chyba że jest ona ustawiana na `latestMajor`.

Aby zrozumieć dostępne zasady i ich zachowanie, należy wziąć pod uwagę następujące definicje wersji zestawu SDK w formacie `x.y.znn`:

- `x` jest wersją główną.
- `y` jest wersją pomocniczą.
- `z` jest paskiem funkcji.
- `nn` to wersja poprawki.

W poniższej tabeli przedstawiono możliwe wartości klucza `rollForward`:

| Wartość         | Zachowanie |
| ------------- | ---------- |
| `patch`       | Używa określonej wersji. <br> Jeśli nie zostanie znaleziony, przenosi do przodu do najnowszego poziomu poprawki. <br> Jeśli nie zostanie znaleziony, kończy się niepowodzeniem. <br><br> Ta wartość to starsze zachowanie z wcześniejszych wersji zestawu SDK. |
| `feature`     | Używa najnowszego poziomu poprawek dla określonych głównych, pomocniczych i grup funkcji. <br> Jeśli nie zostanie znaleziony, przenosi dalej do kolejnej wyższej grupy funkcji w ramach tego samego elementu głównego/pomocniczego i używa najnowszego poziomu poprawek dla tej grupy funkcji. <br> Jeśli nie zostanie znaleziony, kończy się niepowodzeniem. |
| `minor`       | Używa najnowszego poziomu poprawek dla określonych głównych, pomocniczych i grup funkcji. <br> Jeśli nie zostanie znaleziony, przenosi dalej do kolejnej wyższej grupy funkcji w tej samej wersji głównej/pomocniczej i używa najnowszego poziomu poprawek dla tej grupy funkcji. <br> Jeśli nie zostanie znaleziony, przenosi dalej do następnego wyższego elementu pomocniczego i grupy funkcji w ramach tego samego elementu głównego i używa najnowszego poziomu poprawek dla tej grupy funkcji. <br> Jeśli nie zostanie znaleziony, kończy się niepowodzeniem. |
| `major`       | Używa najnowszego poziomu poprawek dla określonych głównych, pomocniczych i grup funkcji. <br> Jeśli nie zostanie znaleziony, przenosi dalej do kolejnej wyższej grupy funkcji w tej samej wersji głównej/pomocniczej i używa najnowszego poziomu poprawek dla tej grupy funkcji. <br> Jeśli nie zostanie znaleziony, przenosi dalej do następnego wyższego elementu pomocniczego i grupy funkcji w ramach tego samego elementu głównego i używa najnowszego poziomu poprawek dla tej grupy funkcji. <br> Jeśli nie zostanie znaleziony, przenosi dalej do następnej wyższej, pomocniczej i funkcjonalnej grupy i używa najnowszego poziomu poprawek dla tej grupy funkcji. <br> Jeśli nie zostanie znaleziony, kończy się niepowodzeniem. |
| `latestPatch` | Używa najnowszego zainstalowanego poziomu poprawek, który jest zgodny z żądanym głównym, pomocniczym i grupą funkcji z poziomem poprawek, który jest większy lub równy określonej wartości. <br> Jeśli nie zostanie znaleziony, kończy się niepowodzeniem. |
| `latestFeature` | Używa najwyższej zainstalowanej grupy funkcji i poziomu poprawek, które pasują do żądanego elementu głównego i pomocniczego za pomocą pasma funkcji, która jest większa lub równa określonej wartości. <br> Jeśli nie zostanie znaleziony, kończy się niepowodzeniem. |
| `latestMinor` | Używa najwyższej zainstalowanej pomocniczej, pasma funkcji i poziomu poprawek, który jest zgodny z zażądaną główną wartością pomocniczą, która jest większa lub równa określonej wartości. <br> Jeśli nie zostanie znaleziony, kończy się niepowodzeniem. |
| `latestMajor` | Używa największej zainstalowanej zestaw .NET Core SDK, która jest większa lub równa określonej wartości. <br> Jeśli nie zostanie znaleziona, kończy się niepowodzeniem. |
| `disable`     | Nie jest rzutowany do przodu. Dokładne dopasowanie jest wymagane. |

## <a name="examples"></a>Przykłady

Poniższy przykład pokazuje, jak nie używać wersji wstępnych:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

Poniższy przykład pokazuje, jak używać zainstalowanej najwyższej wersji, która jest większa lub równa określonej wersji:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

Poniższy przykład pokazuje, jak używać dokładnej wersji:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

Poniższy przykład pokazuje, jak używać najnowszej zainstalowanej wersji poprawki (w postaci 3.1.1 XX):

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>Global. JSON i interfejs wiersza polecenia platformy .NET Core

Warto wiedzieć, które wersje zestawu SDK są zainstalowane na maszynie, aby ustawić je w pliku *Global. JSON* . Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [Jak sprawdzić, czy program .NET Core jest już zainstalowany](../install/how-to-detect-installed-versions.md#check-sdk-versions).

Aby zainstalować dodatkowe zestaw .NET Core SDK wersje na komputerze, odwiedź stronę [pobieranie platformy .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .

Nowy plik *Global. JSON* można utworzyć w bieżącym katalogu, wykonując polecenie [dotnet New](dotnet-new.md) , podobnie jak w poniższym przykładzie:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Reguły dopasowania

> [!NOTE]
> Reguły dopasowywania podlegają punktowi wejścia `dotnet.exe`, który jest wspólny dla wszystkich zainstalowanych środowiska uruchomieniowego platformy .NET Core. Reguły dopasowania dla najnowszej zainstalowanej wersji środowiska uruchomieniowego .NET Core są używane w przypadku, gdy wiele programów uruchomieniowych jest zainstalowanych równolegle.

## <a name="net-core-3x"></a>[.NET Core 3. x](#tab/netcore3x)

Począwszy od platformy .NET Core 3,0, stosowane są następujące reguły podczas określania, która wersja zestawu SDK ma być używana:

- Jeśli nie odnaleziono pliku *Global. JSON* lub plik *Global. JSON* nie określa wersji zestawu SDK ani wartości `allowPrerelease`, używana jest najwyższa zainstalowana wersja zestawu sdk (odpowiednik ustawienia `rollForward` do `latestMajor`). Czy wersje wstępnego zestawu SDK są uwzględniane w zależności od sposobu, w jaki `dotnet` jest wywoływany.
  - Jeśli **nie** Jesteś w programie Visual Studio, są brane pod uwagę wersje wstępne.
  - Jeśli używasz programu Visual Studio, zostanie użyty żądany stan wersji wstępnej. Oznacza to, że w przypadku korzystania z wersji zapoznawczej programu Visual Studio lub ustawienia **Użyj** podglądu opcji zestaw .NET Core SDK (w obszarze **narzędzia** > **Opcje** > **środowisko** > wersja **zapoznawcza**) są uwzględniane wersje wstępne. w przeciwnym razie są brane pod uwagę tylko wersje wydań.
- Jeśli zostanie znaleziony plik *Global. JSON* , który nie określa wersji zestawu SDK, ale określa wartość `allowPrerelease`, używana jest najwyższa zainstalowana wersja zestawu SDK (odpowiednik ustawienia `rollForward` do `latestMajor`). Czy Najnowsza wersja zestawu SDK może być wykorzystana lub wersja wstępna zależy od wartości `allowPrerelease`. `true` wskazuje, że wersje wstępne są brane pod uwagę; `false` wskazuje, że są brane pod uwagę tylko wersje wydań.
- Jeśli zostanie znaleziony plik *Global. JSON* i określi on wersję zestawu SDK:

  - Jeśli wartość `rollFoward` nie jest ustawiona, używa `latestPatch` jako domyślnych zasad `rollForward`. W przeciwnym razie Sprawdź każdą wartość i ich zachowanie w sekcji [przeniesienia](#rollforward) .
  - Bez względu na to, czy są brane pod uwagę wersje wstępne i jakie jest zachowanie domyślne, gdy `allowPrerelease` nie jest ustawiona, jest opisana w sekcji [allowPrerelease](#allowprerelease) .

## <a name="net-core-2x"></a>[.NET Core 2. x](#tab/netcore2x)

W przypadku zestawu SDK platformy .NET Core 2. x następujące reguły są stosowane podczas określania, która wersja zestawu SDK ma być używana:

- Jeśli nie odnaleziono pliku *Global. JSON* lub plik *Global. JSON* nie określa wersji zestawu SDK, zostanie użyta Najnowsza zainstalowana wersja zestawu SDK. Najnowsza wersja zestawu SDK może być wydaniem lub w wersji wstępnej — najwyższa wersja usługi WINS.
- Jeśli *Global. JSON* określi wersję zestawu SDK:
  - Jeśli określona wersja zestawu SDK zostanie znaleziona na komputerze, używana jest dokładna wersja.
  - Jeśli na maszynie nie można znaleźć określonej wersji zestawu SDK, zostanie użyta Najnowsza zainstalowana **wersja poprawki** zestawu SDK. Najnowsza zainstalowana **wersja poprawki** zestawu SDK może być wydaniem lub w wersji wstępnej — najwyższa wersja usługi WINS. W przypadku programu .NET Core 2,1 lub nowszego **wersje poprawek** niższe niż określona **wersja poprawki** są ignorowane w wyborze zestawu SDK.
  - Jeśli nie można znaleźć określonej wersji zestawu SDK i odpowiedniej **wersji poprawki** zestawu SDK, zostanie zgłoszony błąd.

Wersja zestawu SDK składa się z następujących części:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Wersja funkcji** zestaw .NET Core SDK jest reprezentowana przez pierwszą cyfrę (`x`) w ostatniej części liczby (`xyz`) dla wersji zestawu SDK 2.1.100 i wyższych. Ogólnie rzecz biorąc zestaw .NET Core SDK ma szybszy cykl wydawniczy niż .NET Core.

**Wersja poprawki** jest definiowana przez ostatnie dwie cyfry (`yz`) w ostatniej części liczby (`xyz`) dla wersji zestawu SDK 2.1.100 i wyższych. Na przykład jeśli określisz `2.1.300` jako wersję zestawu SDK, wybranie zestawu SDK znajdzie do `2.1.399`, ale `2.1.400` nie jest traktowane jako wersja poprawki dla `2.1.300`.

Zestaw .NET Core SDK wersje `2.1.100` przez `2.1.201` zostały wydane podczas przejścia między schematami numerów wersji i nie obsługują poprawnie notacji `xyz`. Zdecydowanie zalecamy, aby określić te wersje w pliku *Global. JSON* , że określone wersje znajdują się na komputerach docelowych.

---

## <a name="troubleshoot-build-warnings"></a>Rozwiązywanie problemów z ostrzeżeniami kompilacji

* Poniższe ostrzeżenie wskazuje, że projekt został skompilowany przy użyciu wstępnej wersji zestaw .NET Core SDK:

  > Pracujesz z wersją zapoznawczą zestaw .NET Core SDK. Możesz zdefiniować wersję zestawu SDK za pośrednictwem pliku Global. JSON w bieżącym projekcie. Więcej informacji na <https://go.microsoft.com/fwlink/?linkid=869452>.

  Wersje zestaw .NET Core SDK mają historię i zobowiązanie o wysokiej jakości. Jeśli jednak nie chcesz używać wersji wstępnej, Sprawdź różne strategie, których można użyć z zestawem SDK .NET Core 3,0 lub nowszą wersją w sekcji [allowPrerelease](#allowprerelease) . W przypadku maszyn, na których nigdy nie zainstalowano platformy .NET Core 3,0 lub nowszego lub zestawu SDK, należy utworzyć plik *Global. JSON* i określić dokładną wersję, która ma być używana.

* Poniższe ostrzeżenie wskazuje, że projekt jest ukierunkowany na EF Core 1,0 lub 1,1, co nie jest zgodne z zestawem SDK .NET Core 2,1 i nowszymi wersjami:

  > Projekt startowy "{startupProject}" wskazuje platformę ". NETCoreApp "wersja" {targetFrameworkVersion} ". Ta wersja narzędzi wiersza polecenia Entity Framework Core .NET obsługuje tylko wersję 2,0 lub nowszą. Aby uzyskać informacje na temat używania starszych wersji narzędzi, zobacz <https://go.microsoft.com/fwlink/?linkid=871254>.

  Począwszy od zestawu .NET Core 2,1 SDK (wersja 2.1.300), polecenie `dotnet ef` znajduje się w zestawie SDK. Aby skompilować projekt, zainstaluj na komputerze zestaw SDK programu .NET Core 2,0 (wersja 2.1.201) lub wcześniejszy i zdefiniuj żądaną wersję zestawu SDK przy użyciu pliku *Global. JSON* . Aby uzyskać więcej informacji na temat polecenia `dotnet ef`, zobacz [EF Core narzędzia wiersza polecenia platformy .NET](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Zobacz też

- [Jak są rozwiązywane zestawy SDK projektu](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
