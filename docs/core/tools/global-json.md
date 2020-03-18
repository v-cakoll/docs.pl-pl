---
title: global.json — omówienie
description: Dowiedz się, jak ustawić wersję zestawu SDK .NET Core podczas uruchamiania poleceń cli .NET Core za pomocą pliku global.json.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 70257566e1ff30f5c97212a5e0e3c308c27738b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625998"
---
# <a name="globaljson-overview"></a>global.json — omówienie

**Ten artykuł dotyczy:** ✔️ .NET Core 2.0 SDK i nowszych wersji

Plik *global.json* umożliwia określenie, która wersja sdk programu .NET Core jest używana podczas uruchamiania poleceń cli .NET Core. Wybranie sdk .NET Core jest niezależne od określania czasu wykonywania obiektów docelowych projektu. Wersja SDK .NET Core wskazuje, które wersje .NET Core CLI jest używany.

Ogólnie rzecz biorąc, chcesz użyć najnowszej wersji narzędzi SDK, więc nie jest potrzebny plik *global.json.* W niektórych zaawansowanych scenariuszach można kontrolować wersję narzędzi SDK, a w tym artykule wyjaśniono, jak to zrobić.

Aby uzyskać więcej informacji na temat określania czasu wykonywania zamiast tego, zobacz [platformy docelowe](../../standard/frameworks.md).

.NET Core SDK szuka pliku *global.json* w bieżącym katalogu roboczym (który niekoniecznie jest taki sam jak katalog projektu) lub jednego z jego katalogów nadrzędnych.

## <a name="globaljson-schema"></a>schemat global.json

### <a name="sdk"></a>sdk

Typu:`object`

Określa informacje o sdk .NET Core do wybrania.

#### <a name="version"></a>version

- Typu:`string`

- Dostępne od: .NET Core 1.0 SDK.

Wersja sdk .NET Core do użycia.

To pole:

- Nie ma obsługi symboli wieloznacznych, oznacza to, że należy określić pełny numer wersji.
- Nie obsługuje zakresów wersji.

#### <a name="allowprerelease"></a>zezwalaj Przedpremierownie

- Typu:`boolean`

- Dostępne od: .NET Core 3.0 SDK.

Wskazuje, czy program rozpoznawania nazw zestawów SDK powinien uwzględniać wersje wstępne podczas wybierania wersji sdk do użycia.

Jeśli ta wartość nie zostanie ustawiona jawnie, wartość domyślna zależy od tego, czy używasz programu Visual Studio:

- Jeśli **nie** jesteś w programie Visual Studio, wartością domyślną jest `true`wartość .
- Jeśli jesteś w programie Visual Studio, używa żądanego stanu wersji wstępnej. Oznacza to, że jeśli używasz wersji w wersji zapoznawczej programu Visual Studio lub **ustawisz użyj podglądu .NET Core SDK** opcji (w obszarze **Narzędzia** > **Opcje** > **Funkcje podglądu środowiska),** > **Preview Features**wartość domyślna jest `true`; w `false`przeciwnym razie .

#### <a name="rollforward"></a>przerzucanie do przodu

- Typu:`string`

- Dostępne od: .NET Core 3.0 SDK.

Zasady roll-forward do użycia podczas wybierania wersji sdk, albo jako rezerwowy, gdy brakuje określonej wersji sdk lub jako dyrektywy do korzystania z wyższej wersji. [Wersja](#version) musi być określona `rollForward` z wartością, chyba że `latestMajor`ustawiasz ją na .

Aby zrozumieć dostępne zasady i ich zachowanie, należy wziąć pod uwagę `x.y.znn`następujące definicje wersji sdk w formacie:

- `x`jest główną wersją.
- `y`jest wersją pomocniczą.
- `z`jest pasmem funkcji.
- `nn`jest wersja patch.

W poniższej tabeli przedstawiono `rollForward` możliwe wartości klucza:

| Wartość         | Zachowanie |
| ------------- | ---------- |
| `patch`       | Używa określonej wersji. <br> Jeśli nie zostanie znaleziony, przetoczy się do najnowszego poziomu poprawki. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. <br><br> Ta wartość jest starsze zachowanie z wcześniejszych wersji sdk. |
| `feature`     | Używa najnowszego poziomu poprawek dla określonego głównego, pomocniczego i pasma funkcji. <br> Jeśli nie zostanie znaleziony, przetoczy się do następnego wyższego pasma funkcji w ramach tego samego głównego /pomocniczego i używa najnowszego poziomu poprawek dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `minor`       | Używa najnowszego poziomu poprawek dla określonego głównego, pomocniczego i pasma funkcji. <br> Jeśli nie zostanie znaleziony, przetoczy się do następnego wyższego pasma funkcji w tej samej wersji głównej/pomocniczej i użyje najnowszego poziomu poprawek dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, przetoczy się do następnego wyższego pomocniczego i pasma funkcji w ramach tego samego głównego i używa najnowszego poziomu poprawek dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `major`       | Używa najnowszego poziomu poprawek dla określonego głównego, pomocniczego i pasma funkcji. <br> Jeśli nie zostanie znaleziony, przetoczy się do następnego wyższego pasma funkcji w tej samej wersji głównej/pomocniczej i użyje najnowszego poziomu poprawek dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, przetoczy się do następnego wyższego pomocniczego i pasma funkcji w ramach tego samego głównego i używa najnowszego poziomu poprawek dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, przetoczy się do następnego wyższego dużego, pomocniczego i pasma funkcji i użyje najnowszego poziomu poprawek dla tego pasma funkcji. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `latestPatch` | Używa najnowszego zainstalowanego poziomu poprawek, który pasuje do żądanego głównego, pomocniczego i pasma funkcji z poziomem poprawki i który jest większy lub równy określonej wartości. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `latestFeature` | Używa najwyższego zainstalowanego pasma funkcji i poziomu poprawek, który pasuje do żądanego głównego i pomocniczego z pasmem funkcji większym lub równym niż określona wartość. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `latestMinor` | Używa najwyższego zainstalowanego pomocniczego, pasma funkcji i poziomu poprawek, który pasuje do żądanego głównego z wartością pomocniczą, która jest większa lub równa określonej wartości. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `latestMajor` | Używa najwyższego zainstalowanego sdk .NET Core z głównym, który jest większy lub równy niż określona wartość. <br> Jeśli nie zostanie znaleziony, nie powiedzie się. |
| `disable`     | Nie toczy się do przodu. Wymagana dokładna dopasowanie. |

## <a name="examples"></a>Przykłady

W poniższym przykładzie pokazano, jak nie używać wersji wwersji wstępnej:

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

W poniższym przykładzie pokazano, jak używać najwyższej zainstalowanej wersji, która jest większa lub równa określonej wersji:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

W poniższym przykładzie pokazano, jak używać dokładnej określonej wersji:

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

W poniższym przykładzie pokazano, jak używać najwyższej wersji poprawki zainstalowanej w określonej wersji (w formularzu 3.1.1xx):

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json i .NET Core CLI

Warto wiedzieć, które wersje zestawu SDK są zainstalowane na komputerze, aby ustawić je w pliku *global.json.* Aby uzyskać więcej informacji na temat sposobu wykonywania tego celu, zobacz [Jak sprawdzić, czy program .NET Core jest już zainstalowany.](../install/how-to-detect-installed-versions.md#check-sdk-versions)

Aby zainstalować dodatkowe wersje sdk .NET Core na komputerze, odwiedź stronę [Pobieranie .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

Nowy plik *global.json* można utworzyć w bieżącym katalogu, wykonując nowe polecenie [dotnet,](dotnet-new.md) podobne do następującego przykładu:

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Reguły dopasowywania

> [!NOTE]
> Reguły dopasowywania są `dotnet.exe` regulowane przez punkt wejścia, który jest wspólny dla wszystkich zainstalowanych .NET Core zainstalowanych runi. Reguły dopasowywania dla najnowszej zainstalowanej wersji programu .NET Core Runtime są używane, gdy obok siebie jest zainstalowanych wiele runtimes.

## <a name="net-core-3x"></a>[.NET Core 3.x](#tab/netcore3x)

Począwszy od .NET Core 3.0, następujące reguły mają zastosowanie przy określaniu, której wersji sdk użyć:

- Jeśli nie zostanie znaleziony żaden plik *global.json* lub *global.json* nie `allowPrerelease` określa wersji sdk ani wartości, używana jest `rollForward` `latestMajor`najwyższa zainstalowana wersja SDK (odpowiednik ustawienia). To, czy wersje SDK `dotnet` wersji wstępnej są brane pod uwagę, zależy od sposobu wywoływania.
  - Jeśli **nie** jesteś w programie Visual Studio, wersje wstępne są brane pod uwagę.
  - Jeśli jesteś w programie Visual Studio, używa żądanego stanu wersji wstępnej. Oznacza to, że jeśli używasz wersji w wersji zapoznawczej programu Visual Studio lub ustawisz użyj podglądu opcji **.NET Core SDK** (w obszarze **Narzędzia** > **Opcje** > **Funkcje podglądu środowiska),** > **Preview Features**wersje wstępne są brane pod uwagę; w przeciwnym razie uwzględniane są tylko wersje wydania.
- Jeśli zostanie znaleziony plik *global.json,* który nie określa wersji sdk, ale określa `allowPrerelease` wartość, używana jest najwyższa `rollForward` `latestMajor`zainstalowana wersja SDK (odpowiednik ustawienia ). To, czy najnowsza wersja SDK może zostać `allowPrerelease`wydana, czy wstępna, zależy od wartości . `true`wskazuje, że wersje wstępne są brane pod uwagę; `false` wskazuje, że uwzględniane są tylko wersje wydania.
- Jeśli zostanie znaleziony plik *global.json* i określa wersję sdk:

  - Jeśli `rollFoward` żadna wartość nie `latestPatch` jest ustawiona, używa jako zasady domyślnej. `rollForward` W przeciwnym razie sprawdź każdą wartość i ich zachowanie w sekcji [rollForward.](#rollforward)
  - Określa, czy wersje wstępne są brane `allowPrerelease` pod uwagę i jakie jest domyślne zachowanie, gdy nie jest ustawiona, jest opisane w sekcji [allowPrerelease.](#allowprerelease)

## <a name="net-core-2x"></a>[.NET Core 2.x](#tab/netcore2x)

W sdk .NET Core 2.x podczas określania, której wersji sdk ma być używany:

- Jeśli nie zostanie znaleziony żaden plik *global.json* lub *global.json* nie określi wersji sdk, używana jest najnowsza zainstalowana wersja SDK. Najnowsza wersja SDK może być wydana lub wwersji wstępnej - wygrywa najwyższy numer wersji.
- Jeśli *global.json* określi wersję sdk:
  - Jeśli określona wersja sdk znajduje się na komputerze, ta dokładna wersja jest używana.
  - Jeśli nie można odnaleźć określonej wersji sdk na komputerze, używana jest najnowsza zainstalowana **wersja poprawek** SDK tej wersji. Najnowsza zainstalowana **wersja poprawki** SDK może być wydana lub wyjściowa - wygrywa najwyższy numer wersji. W .NET Core 2.1 i nowszych **wersje poprawek** niższe niż określona **wersja poprawki** są ignorowane w wyborze sdk.
  - Jeśli nie można odnaleźć określonej wersji sdk i odpowiedniej **wersji poprawki** SDK, zostanie wyrzucony błąd.

Wersja SDK składa się z następujących części:

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

**Wersja funkcji** .NET Core SDK jest reprezentowana przez`x`pierwszą cyfrę (`xyz`) w ostatniej części liczby ( ) dla wersji SDK 2.1.100 i wyższej. Ogólnie rzecz biorąc .NET Core SDK ma szybszy cykl wydania niż .NET Core.

**Wersja poprawki** jest definiowana przez dwie`yz`ostatnie cyfry ( )`xyz`w ostatniej części liczby ( ) dla wersji SDK 2.1.100 lub wyższej. Na przykład jeśli `2.1.300` określisz jako wersję sdk, `2.1.399` wybór `2.1.400` sdk znajdzie się, ale nie jest uważany za wersję poprawki dla `2.1.300`.

Wersje `2.1.100` SDK .NET Core zostały `2.1.201` wydane podczas przejścia między schematami numerów `xyz` wersji i nie obsługują poprawnie notacji. Zdecydowanie zaleca się, jeśli określisz te wersje w pliku *global.json,* aby upewnić się, że określone wersje znajdują się na komputerach docelowych.

---

## <a name="troubleshoot-build-warnings"></a>Rozwiązywanie problemów z ostrzeżeniami kompilacji

* Następujące ostrzeżenie wskazuje, że projekt został skompilowany przy użyciu wersji wstępnej sdk .NET Core:

  > Pracujesz z wersją zapoznawczą sdk .NET Core. Wersję sdk można zdefiniować za pomocą pliku global.json w bieżącym projekcie. Więcej <https://go.microsoft.com/fwlink/?linkid=869452>na .

  Wersje SDK .NET Core mają historię i zaangażowanie w wysoką jakość. Jeśli jednak nie chcesz używać wersji wstępnej, sprawdź różne strategie, których możesz użyć z zestawem SDK .NET Core 3.0 lub nowszą wersją w sekcji [allowPrerelease.](#allowprerelease) W przypadku komputerów, które nigdy nie miały zainstalowanego programu .NET Core 3.0 lub nowszego programu Runtime lub SDK, należy utworzyć plik *global.json* i określić dokładną wersję, której chcesz użyć.

* Następujące ostrzeżenie wskazuje, że projekt jest przeznaczony dla ef core 1.0 lub 1.1, który nie jest zgodny z .NET Core 2.1 SDK i nowszych wersjach:

  > Projekt startowy "{startupProject}" jest przeznaczony dla struktury ". NETCoreApp" wersja "{targetFrameworkVersion}". Ta wersja narzędzia wiersza polecenia entity framework .NET obsługuje tylko wersję 2.0 lub nowszą. Aby uzyskać informacje na temat korzystania <https://go.microsoft.com/fwlink/?linkid=871254>ze starszych wersji narzędzi, zobacz .

  Począwszy od .NET Core 2.1 SDK (wersja 2.1.300), `dotnet ef` polecenie jest zawarte w zestawie SDK. Aby skompilować projekt, zainstaluj zestaw SDK .NET Core 2.0 (wersja 2.1.201) lub wcześniejszy na komputerze i zdefiniuj żądaną wersję sdk przy użyciu pliku *global.json.* Aby uzyskać więcej `dotnet ef` informacji na temat polecenia, zobacz [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Zobacz też

- [Jak są rozwiązywane zestawy SDK projektu](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
