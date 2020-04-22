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
# <a name="globaljson-overview"></a><span data-ttu-id="7f9ca-103">global.json — omówienie</span><span class="sxs-lookup"><span data-stu-id="7f9ca-103">global.json overview</span></span>

<span data-ttu-id="7f9ca-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="7f9ca-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="7f9ca-105">Plik *global.json* umożliwia zdefiniowanie, która wersja .NET Core SDK jest używana podczas uruchamiania poleceń .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="7f9ca-106">Wybranie .NET Core SDK jest niezależne od określania środowiska uruchomieniowego docelowego projektu.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="7f9ca-107">Wersja .NET Core SDK wskazuje, które wersje interfejsu wiersza polecenia .NET Core jest używany.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="7f9ca-108">Ogólnie rzecz biorąc, chcesz użyć najnowszej wersji narzędzi zestawu SDK, więc nie jest potrzebny plik *global.json.*</span><span class="sxs-lookup"><span data-stu-id="7f9ca-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="7f9ca-109">W niektórych zaawansowanych scenariuszach można kontrolować wersję narzędzi zestawu SDK, a w tym artykule wyjaśniono, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="7f9ca-110">Aby uzyskać więcej informacji na temat określania środowiska uruchomieniowego zamiast tego, zobacz [struktury docelowe](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="7f9ca-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="7f9ca-111">.NET Core SDK wyszukuje plik *global.json* w bieżącym katalogu roboczym (który niekoniecznie jest taki sam jak katalog projektu) lub jeden z jego katalogów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="7f9ca-112">schemat global.json</span><span class="sxs-lookup"><span data-stu-id="7f9ca-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="7f9ca-113">sdk</span><span class="sxs-lookup"><span data-stu-id="7f9ca-113">sdk</span></span>

<span data-ttu-id="7f9ca-114">Typu:`object`</span><span class="sxs-lookup"><span data-stu-id="7f9ca-114">Type: `object`</span></span>

<span data-ttu-id="7f9ca-115">Określa informacje o sdk .NET Core do wyboru.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="7f9ca-116">version</span><span class="sxs-lookup"><span data-stu-id="7f9ca-116">version</span></span>

- <span data-ttu-id="7f9ca-117">Typu:`string`</span><span class="sxs-lookup"><span data-stu-id="7f9ca-117">Type: `string`</span></span>

- <span data-ttu-id="7f9ca-118">Dostępne od: .NET Core 1.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="7f9ca-119">Wersja .NET Core SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="7f9ca-120">To pole:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-120">This field:</span></span>

- <span data-ttu-id="7f9ca-121">Nie ma obsługi symboli wieloznacznych, oznacza to, że należy określić pełny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="7f9ca-122">Nie obsługuje zakresów wersji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="7f9ca-123">allowPrerelease</span><span class="sxs-lookup"><span data-stu-id="7f9ca-123">allowPrerelease</span></span>

- <span data-ttu-id="7f9ca-124">Typu:`boolean`</span><span class="sxs-lookup"><span data-stu-id="7f9ca-124">Type: `boolean`</span></span>

- <span data-ttu-id="7f9ca-125">Dostępne od: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="7f9ca-126">Wskazuje, czy program rozpoznawania nazw SDK należy wziąć pod uwagę wersje wersji wstępnej podczas wybierania wersji SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="7f9ca-127">Jeśli ta wartość nie zostanie jawnie ustawiona, wartość domyślna zależy od tego, czy jest uruchomiony program Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="7f9ca-128">Jeśli **nie** jesteś w programie Visual Studio, wartością domyślną jest `true`.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="7f9ca-129">Jeśli jesteś w programie Visual Studio, używa żądanego stanu wstępnego.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="7f9ca-130">Oznacza to, że jeśli używasz wersji zapoznawczej programu Visual Studio lub ustaw **opcję Użyj podglądu zestawu SDK .NET Core** (w obszarze**Funkcje podglądu\*\*\*\*środowiska opcje** > **Environment** >  **narzędzi),** > domyślną wartością jest `true`; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="7f9ca-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="7f9ca-131">rollForward (do tyłu)</span><span class="sxs-lookup"><span data-stu-id="7f9ca-131">rollForward</span></span>

- <span data-ttu-id="7f9ca-132">Typu:`string`</span><span class="sxs-lookup"><span data-stu-id="7f9ca-132">Type: `string`</span></span>

- <span data-ttu-id="7f9ca-133">Dostępne od: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="7f9ca-134">Zasady do przekazywania rolowania do użycia podczas wybierania wersji SDK, jako rezerwowy, gdy brakuje określonej wersji SDK lub jako dyrektywy do korzystania z wyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="7f9ca-135">[Wersja](#version) musi być określona z wartością, `rollForward` chyba `latestMajor`że ustawiasz ją na .</span><span class="sxs-lookup"><span data-stu-id="7f9ca-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="7f9ca-136">Aby zrozumieć dostępne zasady i ich zachowanie, należy wziąć pod uwagę `x.y.znn`następujące definicje dla wersji SDK w formacie:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="7f9ca-137">`x`jest główną wersją.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-137">`x` is the major version.</span></span>
- <span data-ttu-id="7f9ca-138">`y`jest wersją pomocniczą.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-138">`y` is the minor version.</span></span>
- <span data-ttu-id="7f9ca-139">`z`jest pasmem fabularnym.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-139">`z` is the feature band.</span></span>
- <span data-ttu-id="7f9ca-140">`nn`jest wersją poprawki.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-140">`nn` is the patch version.</span></span>

<span data-ttu-id="7f9ca-141">W poniższej tabeli przedstawiono możliwe wartości klucza: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="7f9ca-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="7f9ca-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="7f9ca-142">Value</span></span>         | <span data-ttu-id="7f9ca-143">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="7f9ca-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="7f9ca-144">Używa określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-144">Uses the specified version.</span></span> <br> <span data-ttu-id="7f9ca-145">Jeśli nie zostanie znaleziony, przesunie się do najnowszego poziomu poprawki.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="7f9ca-146">Jeśli nie zostanie znaleziony, nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="7f9ca-147">Ta wartość jest starsze zachowanie z wcześniejszych wersji SDK.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="7f9ca-148">Używa najnowszego poziomu poprawki dla określonego zespołu głównych, pomocniczych i pasma funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="7f9ca-149">Jeśli nie zostanie znaleziony, przesunie się do następnego wyższego pasma funkcji w obrębie tego samego dużego/pomocniczego i użyje najnowszego poziomu poprawki dla tego pasma funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="7f9ca-150">Jeśli nie zostanie znaleziony, nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="7f9ca-151">Używa najnowszego poziomu poprawki dla określonego zespołu głównych, pomocniczych i pasma funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="7f9ca-152">Jeśli nie zostanie znaleziony, przeskakuje do następnego wyższego pasma funkcji w tej samej wersji głównej/pomocniczej i używa najnowszego poziomu poprawki dla tego pasma funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="7f9ca-153">Jeśli nie zostanie znaleziony, przesunie się do następnego wyższego zespołu pomocniczego i pasma funkcji w obrębie tego samego majora i używa najnowszego poziomu poprawki dla tego pasma funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="7f9ca-154">Jeśli nie zostanie znaleziony, nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="7f9ca-155">Używa najnowszego poziomu poprawki dla określonego zespołu głównych, pomocniczych i pasma funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="7f9ca-156">Jeśli nie zostanie znaleziony, przeskakuje do następnego wyższego pasma funkcji w tej samej wersji głównej/pomocniczej i używa najnowszego poziomu poprawki dla tego pasma funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="7f9ca-157">Jeśli nie zostanie znaleziony, przesunie się do następnego wyższego zespołu pomocniczego i pasma funkcji w obrębie tego samego majora i używa najnowszego poziomu poprawki dla tego pasma funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="7f9ca-158">Jeśli nie zostanie znaleziony, przesunie się do następnego wyższego zespołu głównego, pomocniczego i pasma funkcji i użyje najnowszego poziomu poprawki dla tego pasma funkcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="7f9ca-159">Jeśli nie zostanie znaleziony, nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="7f9ca-160">Używa najnowszego zainstalowanego poziomu poprawki, który pasuje do żądanego zespołu głównych, pomocniczych i funkcji z poziomem poprawki i który jest większy lub równy określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="7f9ca-161">Jeśli nie zostanie znaleziony, nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="7f9ca-162">Używa najwyższego zainstalowanego pasma operacji i poziomu poprawek, który pasuje do żądanego dużego i pomocniczego z pasmem funkcji, który jest większy lub równy określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="7f9ca-163">Jeśli nie zostanie znaleziony, nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="7f9ca-164">Używa najwyższego zainstalowanego pomocniczego, pasma funkcji i poziomu poprawki, który pasuje do żądanego majora z pomocniczym, który jest większy lub równy określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="7f9ca-165">Jeśli nie zostanie znaleziony, nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="7f9ca-166">Używa najwyższego zainstalowanego sdk .NET Core z głównym, który jest większy lub równy z określoną wartością.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="7f9ca-167">Jeśli nie zostanie znaleziony, nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="7f9ca-168">Nie toczy się do przodu.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-168">Doesn't roll forward.</span></span> <span data-ttu-id="7f9ca-169">Wymagane dopasowanie ścisłe.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-169">Exact match required.</span></span> |

## <a name="examples"></a><span data-ttu-id="7f9ca-170">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7f9ca-170">Examples</span></span>

<span data-ttu-id="7f9ca-171">W poniższym przykładzie pokazano, jak nie używać wersji wstępnej:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-171">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="7f9ca-172">W poniższym przykładzie pokazano, jak używać zainstalowanej najwyższej wersji, która jest większa lub równa określonej wersji:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-172">The following example shows how to use the highest version installed that is greater or equal than the specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="7f9ca-173">W poniższym przykładzie pokazano, jak używać dokładnie określonej wersji:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-173">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="7f9ca-174">W poniższym przykładzie pokazano, jak używać najnowszej wersji pasma funkcji i poprawek zainstalowanych w określonej wersji głównej i pomocniczej:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-174">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.000",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="7f9ca-175">Poniższy przykład pokazuje, jak używać najwyższej wersji poprawki zainstalowanej określonej wersji (w formularzu 3.1.1xx):</span><span class="sxs-lookup"><span data-stu-id="7f9ca-175">The following example shows how to use the highest patch version installed of a specific version (in the form, 3.1.1xx):</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="7f9ca-176">global.json i .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="7f9ca-176">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="7f9ca-177">Warto wiedzieć, które wersje zestawu SDK są zainstalowane na komputerze, aby ustawić jedną z nich w pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="7f9ca-177">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="7f9ca-178">Aby uzyskać więcej informacji na temat tego, jak to zrobić, zobacz [Jak sprawdzić, czy program .NET Core jest już zainstalowany.](../install/how-to-detect-installed-versions.md#check-sdk-versions)</span><span class="sxs-lookup"><span data-stu-id="7f9ca-178">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="7f9ca-179">Aby zainstalować na komputerze dodatkowe wersje pakietu .NET Core SDK, odwiedź stronę [Pobierz program .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="7f9ca-179">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="7f9ca-180">Nowy plik *global.json* można utworzyć w bieżącym katalogu, wykonując nowe polecenie [dotnet,](dotnet-new.md) podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-180">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="7f9ca-181">Reguły dopasowywania</span><span class="sxs-lookup"><span data-stu-id="7f9ca-181">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="7f9ca-182">Reguły dopasowywania `dotnet.exe` są regulowane przez punkt wejścia, który jest wspólny dla wszystkich zainstalowanych uruchomień zainstalowanych .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-182">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="7f9ca-183">Reguły dopasowywania dla najnowszej zainstalowanej wersji środowiska uruchomieniowego .NET Core są używane, gdy masz zainstalowane wiele uruchomień obok siebie.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-183">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="7f9ca-184">.NET Rdzeń 3.x</span><span class="sxs-lookup"><span data-stu-id="7f9ca-184">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="7f9ca-185">Począwszy od .NET Core 3.0, przy określaniu, która wersja sdk ma być używana, mają być stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-185">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="7f9ca-186">Jeśli nie zostanie znaleziony żaden plik *global.json* lub *global.json* nie `allowPrerelease` określi wersji SDK ani wartości, używana `rollForward` jest `latestMajor`najwyższa zainstalowana wersja SDK (odpowiednik ustawienia ).</span><span class="sxs-lookup"><span data-stu-id="7f9ca-186">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="7f9ca-187">Czy wersje SDK wersji wstępnej są `dotnet` brane pod uwagę zależy od sposobu wywoływania.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-187">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="7f9ca-188">Jeśli **nie** jesteś w programie Visual Studio, wersje wersji wstępnej są brane pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-188">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="7f9ca-189">Jeśli jesteś w programie Visual Studio, używa żądanego stanu wstępnego.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-189">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="7f9ca-190">Oznacza to, że jeśli używasz wersji preview programu Visual Studio lub ustaw **podglądy .NET Core SDK** opcji (w obszarze**Funkcje** > **podglądu\*\*\*\*środowiska** > opcje **narzędzi),** > wersje wersji wstępnej są brane pod uwagę; w przeciwnym razie uwzględniane są tylko wersje wydania.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-190">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="7f9ca-191">Jeśli zostanie znaleziony plik *global.json,* który nie określa wersji SDK, ale określa wartość, używana jest najwyższa `allowPrerelease` zainstalowana wersja SDK (odpowiednik ustawienia `rollForward` `latestMajor`).</span><span class="sxs-lookup"><span data-stu-id="7f9ca-191">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="7f9ca-192">To, czy najnowsza wersja SDK może zostać wydana, czy wstępna, zależy od wartości pliku `allowPrerelease`.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-192">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="7f9ca-193">`true`wskazuje, że wersje wstępne są brane pod uwagę; `false` wskazuje, że uwzględniane są tylko wersje wydania.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-193">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="7f9ca-194">Jeśli zostanie znaleziony plik *global.json* i określa wersję SDK:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-194">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="7f9ca-195">Jeśli `rollFoward` żadna wartość nie `latestPatch` jest ustawiona, używa jako zasady domyślnej. `rollForward`</span><span class="sxs-lookup"><span data-stu-id="7f9ca-195">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="7f9ca-196">W przeciwnym razie sprawdź każdą wartość i ich zachowanie w sekcji [rollForward.](#rollforward)</span><span class="sxs-lookup"><span data-stu-id="7f9ca-196">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="7f9ca-197">Czy wersje wersji wstępnej są brane pod `allowPrerelease` uwagę i jakie jest zachowanie domyślne, gdy nie jest ustawiona jest opisana w [allowPrerelease](#allowprerelease) sekcji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-197">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="7f9ca-198">.NET Rdzeń 2.x</span><span class="sxs-lookup"><span data-stu-id="7f9ca-198">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="7f9ca-199">W pliku .NET Core 2.x SDK przy określaniu, która wersja sdk ma być używana, mają być stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-199">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="7f9ca-200">Jeśli nie zostanie znaleziony żaden plik *global.json* lub *global.json* nie określi wersji SDK, używana jest najnowsza zainstalowana wersja SDK.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-200">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="7f9ca-201">Najnowsza wersja zestawu SDK może być wydana lub wstępna — wygrywana jest najwyższa liczba wersji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-201">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="7f9ca-202">Jeśli *plik global.json* określa wersję SDK:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-202">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="7f9ca-203">Jeśli określona wersja SDK znajduje się na komputerze, ta dokładna wersja jest używana.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-203">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="7f9ca-204">Jeśli nie można znaleźć określonej wersji SDK na komputerze, używana jest najnowsza zainstalowana **wersja poprawki** SDK tej wersji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-204">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="7f9ca-205">Najnowsza zainstalowana **wersja poprawki** SDK może być wydana lub wstępna — wygrywa najwyższy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-205">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="7f9ca-206">W .NET Core 2.1 i **nowszych wersjach poprawek niższych** niż **określona wersja poprawki** są ignorowane w wyborze SDK.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-206">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="7f9ca-207">Jeśli nie można odnaleźć określonej wersji SDK i odpowiedniej **wersji poprawki** SDK, zostanie wyświetlony błąd.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-207">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="7f9ca-208">Wersja SDK składa się z następujących części:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-208">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="7f9ca-209">**Wersja funkcji** zestawu .NET Core SDK jest reprezentowana`x`przez pierwszą cyfrę`xyz`( ) w ostatniej części liczby ( ) dla zestawu SDK w wersji 2.1.100 i nowszej.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-209">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="7f9ca-210">Ogólnie rzecz biorąc. .NET Core SDK ma szybszy cykl wydania niż .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-210">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="7f9ca-211">**Wersja poprawki** jest definiowana przez dwie`yz`ostatnie cyfry ( )`xyz`w ostatniej części liczby ( ) dla zestawu SDK w wersji 2.1.100 i nowszej.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-211">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="7f9ca-212">Na przykład, jeśli `2.1.300` określisz jako wersję SDK, wybór `2.1.399` `2.1.400` SDK znajdzie do `2.1.300`wersji poprawki, ale nie jest uważany za wersję poprawki dla .</span><span class="sxs-lookup"><span data-stu-id="7f9ca-212">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="7f9ca-213">Wersje `2.1.100` zestawu SDK `2.1.201` .NET Core zostały wydane podczas przejścia między schematami `xyz` numerów wersji i nie obsługują poprawnie notacji.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-213">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="7f9ca-214">Zdecydowanie zaleca się, jeśli określisz te wersje w pliku *global.json,* upewnij się, że określone wersje znajdują się na komputerach docelowych.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-214">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="7f9ca-215">Rozwiązywanie problemów z ostrzeżeniami dotyczącymi kompilacji</span><span class="sxs-lookup"><span data-stu-id="7f9ca-215">Troubleshoot build warnings</span></span>

* <span data-ttu-id="7f9ca-216">Następujące ostrzeżenie wskazuje, że projekt został skompilowany przy użyciu wersji wstępnej sdk .NET Core:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-216">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="7f9ca-217">Pracujesz z wersją zapoznawczą sdk .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-217">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="7f9ca-218">Wersję SDK można zdefiniować za pomocą pliku global.json w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-218">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="7f9ca-219">Więcej <https://go.microsoft.com/fwlink/?linkid=869452>na .</span><span class="sxs-lookup"><span data-stu-id="7f9ca-219">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="7f9ca-220">Wersje .NET Core SDK mają historię i zobowiązanie do wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-220">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="7f9ca-221">Jeśli jednak nie chcesz używać wersji wstępnej, sprawdź różne strategie, których możesz użyć z sdk .NET Core 3.0 lub nowszą wersją w sekcji [allowPrerelease.](#allowprerelease)</span><span class="sxs-lookup"><span data-stu-id="7f9ca-221">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="7f9ca-222">W przypadku maszyn, które nigdy nie miały zainstalowanego środowiska uruchomieniowego .NET Core 3.0 lub sdk, należy utworzyć plik *global.json* i określić dokładną wersję, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-222">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="7f9ca-223">Następujące ostrzeżenie wskazuje, że projekt jest przeznaczony dla ef core 1.0 lub 1.1, który nie jest zgodny z .NET Core 2.1 SDK i nowszych wersjach:</span><span class="sxs-lookup"><span data-stu-id="7f9ca-223">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="7f9ca-224">Projekt startowy "{startupProject}" jest przeznaczony dla struktury ". Wersja NETCoreApp '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-224">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="7f9ca-225">Ta wersja narzędzia wiersza polecenia Core .NET programu Entity Framework obsługuje tylko wersję 2.0 lub nowszą.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-225">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="7f9ca-226">Aby uzyskać informacje na temat używania starszych wersji narzędzi, zobacz <https://go.microsoft.com/fwlink/?linkid=871254>.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-226">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="7f9ca-227">Począwszy od .NET Core 2.1 SDK (wersja 2.1.300), `dotnet ef` polecenie jest zawarte w zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="7f9ca-227">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="7f9ca-228">Aby skompilować projekt, zainstaluj zestaw SDK programu .NET Core 2.0 (wersja 2.1.201) lub wcześniejszy na komputerze i zdefiniuj żądaną wersję SDK przy użyciu pliku *global.json.*</span><span class="sxs-lookup"><span data-stu-id="7f9ca-228">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="7f9ca-229">Aby uzyskać więcej `dotnet ef` informacji na temat polecenia, zobacz [Narzędzia wiersza polecenia EF Core .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="7f9ca-229">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f9ca-230">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f9ca-230">See also</span></span>

- [<span data-ttu-id="7f9ca-231">Jak rozwiązywane są rozwiązania dotyczące skusi SDK projektów</span><span class="sxs-lookup"><span data-stu-id="7f9ca-231">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
