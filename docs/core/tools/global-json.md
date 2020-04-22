---
title: global.json — omówienie
description: Dowiedz się, jak ustawić wersję zestawu .NET Core SDK za pomocą pliku global.json podczas uruchamiania poleceń interfejsu wiersza polecenia .NET Core.
ms.date: 04/21/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 5384b59cccb629a5409d26a8df7c81b3999fc95f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021349"
---
# <a name="globaljson-overview"></a>global.json — omówienie

**Ten artykuł dotyczy:** ✔️.NET Core 2.0 SDK i nowszych wersjach

Plik *global.json* umożliwia zdefiniowanie, która wersja .NET Core SDK jest używana podczas uruchamiania poleceń .NET Core CLI. Wybranie .NET Core SDK jest niezależne od określania środowiska uruchomieniowego docelowego projektu. Wersja .NET Core SDK wskazuje, które wersje interfejsu wiersza polecenia .NET Core jest używany.

Ogólnie rzecz biorąc, chcesz użyć najnowszej wersji narzędzi zestawu SDK, więc nie jest potrzebny plik *global.json.* W niektórych zaawansowanych scenariuszach można kontrolować wersję narzędzi zestawu SDK, a w tym artykule wyjaśniono, jak to zrobić.

Aby uzyskać więcej informacji na temat określania środowiska uruchomieniowego zamiast tego, zobacz [struktury docelowe](../../standard/frameworks.md).

.NET Core SDK wyszukuje plik *global.json* w bieżącym katalogu roboczym (który niekoniecznie jest taki sam jak katalog projektu) lub jeden z jego katalogów nadrzędnych.

## <a name="globaljson-schema"></a>schemat global.json

### <a name="sdk"></a>sdk

Typu:`object`

Określa informacje o sdk .NET Core do wyboru.

#### <a name="version"></a>version

- Typu:`string`

- Dostępne od: .NET Core 1.0 SDK.

Wersja .NET Core SDK do użycia.

To pole:

- Nie ma obsługi symboli wieloznacznych, oznacza to, że należy określić pełny numer wersji.
- Nie obsługuje zakresów wersji.

#### <a name="allowprerelease"></a>allowPrerelease

- Typu:`boolean`

- Dostępne od: .NET Core 3.0 SDK.

Wskazuje, czy program rozpoznawania nazw SDK należy wziąć pod uwagę wersje wersji wstępnej podczas wybierania wersji SDK do użycia.

Jeśli ta wartość nie zostanie jawnie ustawiona, wartość domyślna zależy od tego, czy jest uruchomiony program Visual Studio:

- Jeśli **nie** jesteś w programie Visual Studio, wartością domyślną jest `true`.
- Jeśli jesteś w programie Visual Studio, używa żądanego stanu wstępnego. Oznacza to, że jeśli używasz wersji zapoznawczej programu Visual Studio lub ustaw **opcję Użyj podglądu zestawu SDK .NET Core** (w obszarze**Funkcje podglądu****środowiska opcje** > **Environment** >  **narzędzi),** > domyślną wartością jest `true`; w `false`przeciwnym razie , .

#### <a name="rollforward"></a>rollForward (do tyłu)

- Typu:`string`

- Dostępne od: .NET Core 3.0 SDK.

Zasady do przekazywania rolowania do użycia podczas wybierania wersji SDK, jako rezerwowy, gdy brakuje określonej wersji SDK lub jako dyrektywy do korzystania z wyższej wersji. [Wersja](#version) musi być określona z wartością, `rollForward` chyba `latestMajor`że ustawiasz ją na .

Aby zrozumieć dostępne zasady i ich zachowanie, należy wziąć pod uwagę `x.y.znn`następujące definicje dla wersji SDK w formacie:

- `x`jest główną wersją.
- `y`jest wersją pomocniczą.
- `z`jest pasmem fabularnym.
- `nn`jest wersją poprawki.

W poniższej tabeli przedstawiono możliwe wartości klucza: `rollForward`

| Wartość         | Zachowanie |
| ------------- | ---------- |
| `patch`       | Używa określonej wersji. <br> Jeśli nie zostanie znaleziony, przesunie się do najnowszego poziomu poprawki. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. <br><br> Ta wartość jest starsze zachowanie z wcześniejszych wersji SDK. |
| `feature`     | Używa najnowszego poziomu poprawki dla określonego zespołu głównych, pomocniczych i pasma funkcji. <br> Jeśli nie zostanie znaleziony, przesunie się do następnego wyższego pasma funkcji w obrębie tego samego dużego/pomocniczego i użyje najnowszego poziomu poprawki dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `minor`       | Używa najnowszego poziomu poprawki dla określonego zespołu głównych, pomocniczych i pasma funkcji. <br> Jeśli nie zostanie znaleziony, przeskakuje do następnego wyższego pasma funkcji w tej samej wersji głównej/pomocniczej i używa najnowszego poziomu poprawki dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, przesunie się do następnego wyższego zespołu pomocniczego i pasma funkcji w obrębie tego samego majora i używa najnowszego poziomu poprawki dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `major`       | Używa najnowszego poziomu poprawki dla określonego zespołu głównych, pomocniczych i pasma funkcji. <br> Jeśli nie zostanie znaleziony, przeskakuje do następnego wyższego pasma funkcji w tej samej wersji głównej/pomocniczej i używa najnowszego poziomu poprawki dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, przesunie się do następnego wyższego zespołu pomocniczego i pasma funkcji w obrębie tego samego majora i używa najnowszego poziomu poprawki dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, przesunie się do następnego wyższego zespołu głównego, pomocniczego i pasma funkcji i użyje najnowszego poziomu poprawki dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `latestPatch` | Używa najnowszego zainstalowanego poziomu poprawki, który pasuje do żądanego zespołu głównych, pomocniczych i funkcji z poziomem poprawki i który jest większy lub równy określonej wartości. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `latestFeature` | Używa najwyższego zainstalowanego pasma operacji i poziomu poprawek, który pasuje do żądanego dużego i pomocniczego z pasmem funkcji, który jest większy lub równy określonej wartości. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `latestMinor` | Używa najwyższego zainstalowanego pomocniczego, pasma funkcji i poziomu poprawki, który pasuje do żądanego majora z pomocniczym, który jest większy lub równy określonej wartości. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `latestMajor` | Używa najwyższego zainstalowanego sdk .NET Core z głównym, który jest większy lub równy z określoną wartością. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `disable`     | Nie toczy się do przodu. Wymagane dopasowanie ścisłe. |

## <a name="examples"></a>Przykłady

W poniższym przykładzie pokazano, jak nie używać wersji wstępnej:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

W poniższym przykładzie pokazano, jak używać zainstalowanej najwyższej wersji, która jest większa lub równa określonej wersji:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

W poniższym przykładzie pokazano, jak używać dokładnie określonej wersji:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

W poniższym przykładzie pokazano, jak używać najnowszej wersji pasma funkcji i poprawek zainstalowanych w określonej wersji głównej i pomocniczej:

```json
{
  "sdk": {
    "version": "3.1.000",
    "rollForward": "latestFeature"
  }
}
```

Poniższy przykład pokazuje, jak używać najwyższej wersji poprawki zainstalowanej określonej wersji (w formularzu 3.1.1xx):

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json i .NET Core CLI

Warto wiedzieć, które wersje zestawu SDK są zainstalowane na komputerze, aby ustawić jedną z nich w pliku *global.json.* Aby uzyskać więcej informacji na temat tego, jak to zrobić, zobacz [Jak sprawdzić, czy program .NET Core jest już zainstalowany.](../install/how-to-detect-installed-versions.md#check-sdk-versions)

Aby zainstalować na komputerze dodatkowe wersje pakietu .NET Core SDK, odwiedź stronę [Pobierz program .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

Nowy plik *global.json* można utworzyć w bieżącym katalogu, wykonując nowe polecenie [dotnet,](dotnet-new.md) podobnie jak w poniższym przykładzie:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Reguły dopasowywania

> [!NOTE]
> Reguły dopasowywania `dotnet.exe` są regulowane przez punkt wejścia, który jest wspólny dla wszystkich zainstalowanych uruchomień zainstalowanych .NET Core. Reguły dopasowywania dla najnowszej zainstalowanej wersji środowiska uruchomieniowego .NET Core są używane, gdy masz zainstalowane wiele uruchomień obok siebie.

## <a name="net-core-3x"></a>[.NET Rdzeń 3.x](#tab/netcore3x)

Począwszy od .NET Core 3.0, przy określaniu, która wersja sdk ma być używana, mają być stosowane następujące reguły:

- Jeśli nie zostanie znaleziony żaden plik *global.json* lub *global.json* nie `allowPrerelease` określi wersji SDK ani wartości, używana `rollForward` jest `latestMajor`najwyższa zainstalowana wersja SDK (odpowiednik ustawienia ). Czy wersje SDK wersji wstępnej są `dotnet` brane pod uwagę zależy od sposobu wywoływania.
  - Jeśli **nie** jesteś w programie Visual Studio, wersje wersji wstępnej są brane pod uwagę.
  - Jeśli jesteś w programie Visual Studio, używa żądanego stanu wstępnego. Oznacza to, że jeśli używasz wersji preview programu Visual Studio lub ustaw **podglądy .NET Core SDK** opcji (w obszarze**Funkcje** > **podglądu****środowiska** > opcje **narzędzi),** > wersje wersji wstępnej są brane pod uwagę; w przeciwnym razie uwzględniane są tylko wersje wydania.
- Jeśli zostanie znaleziony plik *global.json,* który nie określa wersji SDK, ale określa wartość, używana jest najwyższa `allowPrerelease` zainstalowana wersja SDK (odpowiednik ustawienia `rollForward` `latestMajor`). To, czy najnowsza wersja SDK może zostać wydana, czy wstępna, zależy od wartości pliku `allowPrerelease`. `true`wskazuje, że wersje wstępne są brane pod uwagę; `false` wskazuje, że uwzględniane są tylko wersje wydania.
- Jeśli zostanie znaleziony plik *global.json* i określa wersję SDK:

  - Jeśli `rollFoward` żadna wartość nie `latestPatch` jest ustawiona, używa jako zasady domyślnej. `rollForward` W przeciwnym razie sprawdź każdą wartość i ich zachowanie w sekcji [rollForward.](#rollforward)
  - Czy wersje wersji wstępnej są brane pod `allowPrerelease` uwagę i jakie jest zachowanie domyślne, gdy nie jest ustawiona jest opisana w [allowPrerelease](#allowprerelease) sekcji.

## <a name="net-core-2x"></a>[.NET Rdzeń 2.x](#tab/netcore2x)

W pliku .NET Core 2.x SDK przy określaniu, która wersja sdk ma być używana, mają być stosowane następujące reguły:

- Jeśli nie zostanie znaleziony żaden plik *global.json* lub *global.json* nie określi wersji SDK, używana jest najnowsza zainstalowana wersja SDK. Najnowsza wersja zestawu SDK może być wydana lub wstępna — wygrywana jest najwyższa liczba wersji.
- Jeśli *plik global.json* określa wersję SDK:
  - Jeśli określona wersja SDK znajduje się na komputerze, ta dokładna wersja jest używana.
  - Jeśli nie można znaleźć określonej wersji SDK na komputerze, używana jest najnowsza zainstalowana **wersja poprawki** SDK tej wersji. Najnowsza zainstalowana **wersja poprawki** SDK może być wydana lub wstępna — wygrywa najwyższy numer wersji. W .NET Core 2.1 i **nowszych wersjach poprawek niższych** niż **określona wersja poprawki** są ignorowane w wyborze SDK.
  - Jeśli nie można odnaleźć określonej wersji SDK i odpowiedniej **wersji poprawki** SDK, zostanie wyświetlony błąd.

Wersja SDK składa się z następujących części:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Wersja funkcji** zestawu .NET Core SDK jest reprezentowana`x`przez pierwszą cyfrę`xyz`( ) w ostatniej części liczby ( ) dla zestawu SDK w wersji 2.1.100 i nowszej. Ogólnie rzecz biorąc. .NET Core SDK ma szybszy cykl wydania niż .NET Core.

**Wersja poprawki** jest definiowana przez dwie`yz`ostatnie cyfry ( )`xyz`w ostatniej części liczby ( ) dla zestawu SDK w wersji 2.1.100 i nowszej. Na przykład, jeśli `2.1.300` określisz jako wersję SDK, wybór `2.1.399` `2.1.400` SDK znajdzie do `2.1.300`wersji poprawki, ale nie jest uważany za wersję poprawki dla .

Wersje `2.1.100` zestawu SDK `2.1.201` .NET Core zostały wydane podczas przejścia między schematami `xyz` numerów wersji i nie obsługują poprawnie notacji. Zdecydowanie zaleca się, jeśli określisz te wersje w pliku *global.json,* upewnij się, że określone wersje znajdują się na komputerach docelowych.

---

## <a name="troubleshoot-build-warnings"></a>Rozwiązywanie problemów z ostrzeżeniami dotyczącymi kompilacji

* Następujące ostrzeżenie wskazuje, że projekt został skompilowany przy użyciu wersji wstępnej sdk .NET Core:

  > Pracujesz z wersją zapoznawczą sdk .NET Core. Wersję SDK można zdefiniować za pomocą pliku global.json w bieżącym projekcie. Więcej <https://go.microsoft.com/fwlink/?linkid=869452>na .

  Wersje .NET Core SDK mają historię i zobowiązanie do wysokiej jakości. Jeśli jednak nie chcesz używać wersji wstępnej, sprawdź różne strategie, których możesz użyć z sdk .NET Core 3.0 lub nowszą wersją w sekcji [allowPrerelease.](#allowprerelease) W przypadku maszyn, które nigdy nie miały zainstalowanego środowiska uruchomieniowego .NET Core 3.0 lub sdk, należy utworzyć plik *global.json* i określić dokładną wersję, której chcesz użyć.

* Następujące ostrzeżenie wskazuje, że projekt jest przeznaczony dla ef core 1.0 lub 1.1, który nie jest zgodny z .NET Core 2.1 SDK i nowszych wersjach:

  > Projekt startowy "{startupProject}" jest przeznaczony dla struktury ". Wersja NETCoreApp '{targetFrameworkVersion}'. Ta wersja narzędzia wiersza polecenia Core .NET programu Entity Framework obsługuje tylko wersję 2.0 lub nowszą. Aby uzyskać informacje na temat używania starszych wersji narzędzi, zobacz <https://go.microsoft.com/fwlink/?linkid=871254>.

  Począwszy od .NET Core 2.1 SDK (wersja 2.1.300), `dotnet ef` polecenie jest zawarte w zestawie SDK. Aby skompilować projekt, zainstaluj zestaw SDK programu .NET Core 2.0 (wersja 2.1.201) lub wcześniejszy na komputerze i zdefiniuj żądaną wersję SDK przy użyciu pliku *global.json.* Aby uzyskać więcej `dotnet ef` informacji na temat polecenia, zobacz [Narzędzia wiersza polecenia EF Core .NET](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Zobacz też

- [Jak rozwiązywane są rozwiązania dotyczące skusi SDK projektów](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
