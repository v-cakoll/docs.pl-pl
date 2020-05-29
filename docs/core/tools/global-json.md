---
title: global.json — omówienie
description: Dowiedz się, jak używać pliku Global. JSON do ustawiania wersji zestaw .NET Core SDK podczas uruchamiania poleceń interfejs wiersza polecenia platformy .NET Core.
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 5078bc03056c23bccf02e027441de72c69072c7d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202028"
---
# <a name="globaljson-overview"></a><span data-ttu-id="41c52-103">global.json — omówienie</span><span class="sxs-lookup"><span data-stu-id="41c52-103">global.json overview</span></span>

<span data-ttu-id="41c52-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="41c52-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="41c52-105">Plik *Global. JSON* pozwala określić, która wersja zestaw .NET Core SDK jest używana podczas uruchamiania poleceń interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41c52-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="41c52-106">Wybór zestaw .NET Core SDK jest niezależny od określania środowiska uruchomieniowego projektu.</span><span class="sxs-lookup"><span data-stu-id="41c52-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="41c52-107">Wersja zestaw .NET Core SDK wskazuje, które wersje interfejs wiersza polecenia platformy .NET Core są używane.</span><span class="sxs-lookup"><span data-stu-id="41c52-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="41c52-108">Ogólnie rzecz biorąc, chcesz użyć najnowszej wersji narzędzi zestawu SDK, więc nie jest potrzebny plik *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="41c52-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="41c52-109">W niektórych zaawansowanych scenariuszach możesz chcieć kontrolować wersję narzędzi zestawu SDK, a w tym artykule wyjaśniono, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="41c52-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="41c52-110">Aby uzyskać więcej informacji na temat określania środowiska uruchomieniowego, zobacz [platforme docelowe](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="41c52-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="41c52-111">Zestaw .NET Core SDK szuka pliku *Global. JSON* w bieżącym katalogu roboczym (który nie musi być taki sam jak katalog projektu) lub jednego z jego katalogów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="41c52-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="41c52-112">Global. JSON — schemat</span><span class="sxs-lookup"><span data-stu-id="41c52-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="41c52-113">sdk</span><span class="sxs-lookup"><span data-stu-id="41c52-113">sdk</span></span>

<span data-ttu-id="41c52-114">Wprowadź`object`</span><span class="sxs-lookup"><span data-stu-id="41c52-114">Type: `object`</span></span>

<span data-ttu-id="41c52-115">Określa informacje o zestaw .NET Core SDK do wybrania.</span><span class="sxs-lookup"><span data-stu-id="41c52-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="41c52-116">version</span><span class="sxs-lookup"><span data-stu-id="41c52-116">version</span></span>

- <span data-ttu-id="41c52-117">Wprowadź`string`</span><span class="sxs-lookup"><span data-stu-id="41c52-117">Type: `string`</span></span>

- <span data-ttu-id="41c52-118">Dostępne od: .NET Core 1,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="41c52-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="41c52-119">Wersja zestaw .NET Core SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="41c52-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="41c52-120">To pole:</span><span class="sxs-lookup"><span data-stu-id="41c52-120">This field:</span></span>

- <span data-ttu-id="41c52-121">Nie ma obsługi symboli wieloznacznych, czyli należy określić pełny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="41c52-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="41c52-122">Nie obsługuje zakresów wersji.</span><span class="sxs-lookup"><span data-stu-id="41c52-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="41c52-123">allowPrerelease</span><span class="sxs-lookup"><span data-stu-id="41c52-123">allowPrerelease</span></span>

- <span data-ttu-id="41c52-124">Wprowadź`boolean`</span><span class="sxs-lookup"><span data-stu-id="41c52-124">Type: `boolean`</span></span>

- <span data-ttu-id="41c52-125">Dostępne od: .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="41c52-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="41c52-126">Wskazuje, czy program rozpoznawania SDK powinien wziąć pod uwagę wersje wstępne podczas wybierania wersji zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="41c52-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="41c52-127">Jeśli ta wartość nie zostanie jawnie ustawiona, wartość domyślna zależy od tego, czy korzystasz z programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="41c52-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="41c52-128">Jeśli **nie** Jesteś w programie Visual Studio, wartość domyślna to `true` .</span><span class="sxs-lookup"><span data-stu-id="41c52-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="41c52-129">Jeśli używasz programu Visual Studio, zostanie użyty żądany stan wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="41c52-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="41c52-130">Oznacza to, że jeśli korzystasz z wersji zapoznawczej programu Visual Studio lub ustawisz opcję Użyj podglądu opcji **zestaw .NET Core SDK** (w obszarze **Narzędzia**  >  **Opcje**  >  **środowiska**w  >  **wersji zapoznawczej**), wartość domyślna to `true` ; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="41c52-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="41c52-131">Przeniesienia</span><span class="sxs-lookup"><span data-stu-id="41c52-131">rollForward</span></span>

- <span data-ttu-id="41c52-132">Wprowadź`string`</span><span class="sxs-lookup"><span data-stu-id="41c52-132">Type: `string`</span></span>

- <span data-ttu-id="41c52-133">Dostępne od: .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="41c52-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="41c52-134">Zasady przyciągania do przodu, które mają być używane podczas wybierania wersji zestawu SDK, jako rezerwy w przypadku braku określonej wersji zestawu SDK lub jako dyrektywy do korzystania z nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="41c52-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="41c52-135">Należy określić [wersję](#version) o `rollForward` wartości, chyba że jest ona ustawiana na `latestMajor` .</span><span class="sxs-lookup"><span data-stu-id="41c52-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="41c52-136">Aby zrozumieć dostępne zasady i ich zachowanie, należy wziąć pod uwagę następujące definicje wersji zestawu SDK w formacie `x.y.znn` :</span><span class="sxs-lookup"><span data-stu-id="41c52-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="41c52-137">`x`jest wersją główną.</span><span class="sxs-lookup"><span data-stu-id="41c52-137">`x` is the major version.</span></span>
- <span data-ttu-id="41c52-138">`y`jest wersją pomocniczą.</span><span class="sxs-lookup"><span data-stu-id="41c52-138">`y` is the minor version.</span></span>
- <span data-ttu-id="41c52-139">`z`jest paskiem funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-139">`z` is the feature band.</span></span>
- <span data-ttu-id="41c52-140">`nn`jest wersją poprawki.</span><span class="sxs-lookup"><span data-stu-id="41c52-140">`nn` is the patch version.</span></span>

<span data-ttu-id="41c52-141">W poniższej tabeli przedstawiono możliwe wartości `rollForward` klucza:</span><span class="sxs-lookup"><span data-stu-id="41c52-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="41c52-142">Wartość</span><span class="sxs-lookup"><span data-stu-id="41c52-142">Value</span></span>         | <span data-ttu-id="41c52-143">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="41c52-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="41c52-144">Używa określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="41c52-144">Uses the specified version.</span></span> <br> <span data-ttu-id="41c52-145">Jeśli nie zostanie znaleziony, przenosi do przodu do najnowszego poziomu poprawki.</span><span class="sxs-lookup"><span data-stu-id="41c52-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="41c52-146">Jeśli nie zostanie znaleziony, kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41c52-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="41c52-147">Ta wartość to starsze zachowanie z wcześniejszych wersji zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="41c52-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="41c52-148">Używa najnowszego poziomu poprawek dla określonych głównych, pomocniczych i grup funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="41c52-149">Jeśli nie zostanie znaleziony, przenosi dalej do kolejnej wyższej grupy funkcji w ramach tego samego elementu głównego/pomocniczego i używa najnowszego poziomu poprawek dla tej grupy funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="41c52-150">Jeśli nie zostanie znaleziony, kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41c52-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="41c52-151">Używa najnowszego poziomu poprawek dla określonych głównych, pomocniczych i grup funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="41c52-152">Jeśli nie zostanie znaleziony, przenosi dalej do kolejnej wyższej grupy funkcji w tej samej wersji głównej/pomocniczej i używa najnowszego poziomu poprawek dla tej grupy funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="41c52-153">Jeśli nie zostanie znaleziony, przenosi dalej do następnego wyższego elementu pomocniczego i grupy funkcji w ramach tego samego elementu głównego i używa najnowszego poziomu poprawek dla tej grupy funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="41c52-154">Jeśli nie zostanie znaleziony, kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41c52-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="41c52-155">Używa najnowszego poziomu poprawek dla określonych głównych, pomocniczych i grup funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="41c52-156">Jeśli nie zostanie znaleziony, przenosi dalej do kolejnej wyższej grupy funkcji w tej samej wersji głównej/pomocniczej i używa najnowszego poziomu poprawek dla tej grupy funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="41c52-157">Jeśli nie zostanie znaleziony, przenosi dalej do następnego wyższego elementu pomocniczego i grupy funkcji w ramach tego samego elementu głównego i używa najnowszego poziomu poprawek dla tej grupy funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="41c52-158">Jeśli nie zostanie znaleziony, przenosi dalej do następnej wyższej, pomocniczej i funkcjonalnej grupy i używa najnowszego poziomu poprawek dla tej grupy funkcji.</span><span class="sxs-lookup"><span data-stu-id="41c52-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="41c52-159">Jeśli nie zostanie znaleziony, kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41c52-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="41c52-160">Używa najnowszego zainstalowanego poziomu poprawek, który jest zgodny z żądanym głównym, pomocniczym i grupą funkcji z poziomem poprawek, który jest większy lub równy określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="41c52-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="41c52-161">Jeśli nie zostanie znaleziony, kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41c52-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="41c52-162">Używa najwyższej zainstalowanej grupy funkcji i poziomu poprawek, które pasują do żądanego elementu głównego i pomocniczego za pomocą pasma funkcji, która jest większa lub równa określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="41c52-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="41c52-163">Jeśli nie zostanie znaleziony, kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41c52-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="41c52-164">Używa najwyższej zainstalowanej pomocniczej, pasma funkcji i poziomu poprawek, który jest zgodny z zażądaną główną wartością pomocniczą, która jest większa lub równa określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="41c52-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="41c52-165">Jeśli nie zostanie znaleziony, kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41c52-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="41c52-166">Używa największej zainstalowanej zestaw .NET Core SDK, która jest większa lub równa określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="41c52-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="41c52-167">Jeśli nie zostanie znaleziona, kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41c52-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="41c52-168">Nie jest rzutowany do przodu.</span><span class="sxs-lookup"><span data-stu-id="41c52-168">Doesn't roll forward.</span></span> <span data-ttu-id="41c52-169">Dokładne dopasowanie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="41c52-169">Exact match required.</span></span> |

### <a name="msbuild-sdks"></a><span data-ttu-id="41c52-170">MSBuild — zestawy SDK</span><span class="sxs-lookup"><span data-stu-id="41c52-170">msbuild-sdks</span></span>

<span data-ttu-id="41c52-171">Wprowadź`object`</span><span class="sxs-lookup"><span data-stu-id="41c52-171">Type: `object`</span></span>

<span data-ttu-id="41c52-172">Pozwala kontrolować wersję zestawu SDK projektu w jednym miejscu, a nie w każdym projekcie.</span><span class="sxs-lookup"><span data-stu-id="41c52-172">Lets you control the project SDK version in one place rather than in each individual project.</span></span> <span data-ttu-id="41c52-173">Aby uzyskać więcej informacji, zobacz [jak są rozpoznawane zestawy SDK projektu](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span><span class="sxs-lookup"><span data-stu-id="41c52-173">For more information, see [How project SDKs are resolved](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span></span>

## <a name="examples"></a><span data-ttu-id="41c52-174">Przykłady</span><span class="sxs-lookup"><span data-stu-id="41c52-174">Examples</span></span>

<span data-ttu-id="41c52-175">Poniższy przykład pokazuje, jak nie używać wersji wstępnych:</span><span class="sxs-lookup"><span data-stu-id="41c52-175">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="41c52-176">Poniższy przykład pokazuje, jak używać zainstalowanej najwyższej wersji, która jest większa lub równa określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="41c52-176">The following example shows how to use the highest version installed that is greater or equal than the specified version.</span></span> <span data-ttu-id="41c52-177">W pokazanym kodzie JSON nie jest dozwolony żaden zestaw SDK wcześniejszy niż 2.2.200 i umożliwia 2.2.200 lub dowolną nowszą wersję, w tym 3.0.xxx i 3.1.xxx.</span><span class="sxs-lookup"><span data-stu-id="41c52-177">The JSON shown disallows any SDK version earlier than 2.2.200 and allows 2.2.200 or any later version, including 3.0.xxx and 3.1.xxx.</span></span>

```json
{
  "sdk": {
    "version": "2.2.200",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="41c52-178">Poniższy przykład pokazuje, jak używać dokładnej wersji:</span><span class="sxs-lookup"><span data-stu-id="41c52-178">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="41c52-179">Poniższy przykład pokazuje, jak używać najnowszej wersji i zainstalowanej wersji poprawki dla określonej głównej i pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="41c52-179">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version.</span></span> <span data-ttu-id="41c52-180">W pokazanym kodzie JSON nie jest dozwolony żaden zestaw SDK wcześniejszy niż 3.1.102 i umożliwia 3.1.102 lub dowolną nowszą wersję 3.1.xxx, taką jak 3.1.103 lub 3.1.200.</span><span class="sxs-lookup"><span data-stu-id="41c52-180">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.xxx version, such as 3.1.103 or 3.1.200.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="41c52-181">Poniższy przykład pokazuje, jak używać najnowszej wersji poprawki zainstalowanej w określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="41c52-181">The following example shows how to use the highest patch version installed of a specific version.</span></span> <span data-ttu-id="41c52-182">W pokazanym kodzie JSON nie jest dozwolony żaden zestaw SDK wcześniejszy niż 3.1.102 i umożliwia 3.1.102 lub jakąkolwiek nowszą wersję 3.1.1 XX, taką jak 3.1.103 lub 3.1.199.</span><span class="sxs-lookup"><span data-stu-id="41c52-182">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.1xx version, such as 3.1.103 or 3.1.199.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="41c52-183">Global. JSON i interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="41c52-183">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="41c52-184">Warto wiedzieć, które wersje zestawu SDK są zainstalowane na maszynie, aby ustawić je w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="41c52-184">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="41c52-185">Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [Jak sprawdzić, czy program .NET Core jest już zainstalowany](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="41c52-185">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="41c52-186">Aby zainstalować dodatkowe zestaw .NET Core SDK wersje na komputerze, odwiedź stronę [pobieranie platformy .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="41c52-186">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="41c52-187">Nowy plik *Global. JSON* można utworzyć w bieżącym katalogu, wykonując polecenie [dotnet New](dotnet-new.md) , podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="41c52-187">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="41c52-188">Reguły dopasowania</span><span class="sxs-lookup"><span data-stu-id="41c52-188">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="41c52-189">Reguły dopasowania podlegają `dotnet.exe` punktowi wejścia, który jest wspólny dla wszystkich zainstalowanych środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41c52-189">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="41c52-190">Reguły dopasowania dla najnowszej zainstalowanej wersji środowiska uruchomieniowego .NET Core są używane w przypadku, gdy wiele programów uruchomieniowych jest zainstalowanych równolegle.</span><span class="sxs-lookup"><span data-stu-id="41c52-190">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="41c52-191">.NET Core 3. x</span><span class="sxs-lookup"><span data-stu-id="41c52-191">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="41c52-192">Począwszy od platformy .NET Core 3,0, stosowane są następujące reguły podczas określania, która wersja zestawu SDK ma być używana:</span><span class="sxs-lookup"><span data-stu-id="41c52-192">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="41c52-193">Jeśli nie odnaleziono pliku *Global. JSON* lub plik *Global. JSON* nie określa wersji zestawu SDK ani `allowPrerelease` wartości, używana jest najwyższa zainstalowana wersja zestawu SDK (odpowiednik ustawienia `rollForward` do `latestMajor` ).</span><span class="sxs-lookup"><span data-stu-id="41c52-193">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="41c52-194">Czy wersje wstępne zestawu SDK są brane pod uwagę, zależy od tego, jak `dotnet` są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="41c52-194">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="41c52-195">Jeśli **nie** Jesteś w programie Visual Studio, są brane pod uwagę wersje wstępne.</span><span class="sxs-lookup"><span data-stu-id="41c52-195">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="41c52-196">Jeśli używasz programu Visual Studio, zostanie użyty żądany stan wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="41c52-196">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="41c52-197">Oznacza to, że jeśli korzystasz z wersji zapoznawczej programu Visual Studio lub ustawisz opcję Użyj podglądu opcji **zestaw .NET Core SDK** (w obszarze **Narzędzia**  >  **Opcje**  >  **środowiska**w  >  **wersji zapoznawczej**), są uwzględniane wersje wstępne. w przeciwnym razie są brane pod uwagę tylko wersje wydań.</span><span class="sxs-lookup"><span data-stu-id="41c52-197">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="41c52-198">Jeśli zostanie znaleziony plik *Global. JSON* , który nie określa wersji zestawu SDK, ale określa `allowPrerelease` wartość, używana jest najwyższa zainstalowana wersja zestawu SDK (odpowiednik ustawienia `rollForward` do `latestMajor` ).</span><span class="sxs-lookup"><span data-stu-id="41c52-198">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="41c52-199">Czy Najnowsza wersja zestawu SDK może być wykorzystana lub wersja wstępna zależy od wartości `allowPrerelease` .</span><span class="sxs-lookup"><span data-stu-id="41c52-199">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="41c52-200">`true`wskazuje wersje wstępne są brane pod uwagę; `false`wskazuje, że są brane pod uwagę tylko wersje wydań.</span><span class="sxs-lookup"><span data-stu-id="41c52-200">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="41c52-201">Jeśli zostanie znaleziony plik *Global. JSON* i określi on wersję zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="41c52-201">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="41c52-202">Jeśli `rollFoward` wartość nie jest ustawiona, zostanie użyta `latestPatch` jako `rollForward` zasady domyślne.</span><span class="sxs-lookup"><span data-stu-id="41c52-202">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="41c52-203">W przeciwnym razie Sprawdź każdą wartość i ich zachowanie w sekcji [przeniesienia](#rollforward) .</span><span class="sxs-lookup"><span data-stu-id="41c52-203">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="41c52-204">Określa, czy wersje wstępne są brane pod uwagę, co jest zachowaniem domyślnym, gdy `allowPrerelease` nie jest ustawione, w sekcji [allowPrerelease](#allowprerelease) .</span><span class="sxs-lookup"><span data-stu-id="41c52-204">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="41c52-205">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="41c52-205">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="41c52-206">W przypadku zestawu SDK platformy .NET Core 2. x następujące reguły są stosowane podczas określania, która wersja zestawu SDK ma być używana:</span><span class="sxs-lookup"><span data-stu-id="41c52-206">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="41c52-207">Jeśli nie odnaleziono pliku *Global. JSON* lub plik *Global. JSON* nie określa wersji zestawu SDK, zostanie użyta Najnowsza zainstalowana wersja zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="41c52-207">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="41c52-208">Najnowsza wersja zestawu SDK może być wydaniem lub w wersji wstępnej — najwyższa wersja usługi WINS.</span><span class="sxs-lookup"><span data-stu-id="41c52-208">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="41c52-209">Jeśli *Global. JSON* określi wersję zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="41c52-209">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="41c52-210">Jeśli określona wersja zestawu SDK zostanie znaleziona na komputerze, używana jest dokładna wersja.</span><span class="sxs-lookup"><span data-stu-id="41c52-210">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="41c52-211">Jeśli na maszynie nie można znaleźć określonej wersji zestawu SDK, zostanie użyta Najnowsza zainstalowana **wersja poprawki** zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="41c52-211">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="41c52-212">Najnowsza zainstalowana **wersja poprawki** zestawu SDK może być wydaniem lub w wersji wstępnej — najwyższa wersja usługi WINS.</span><span class="sxs-lookup"><span data-stu-id="41c52-212">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="41c52-213">W przypadku programu .NET Core 2,1 lub nowszego **wersje poprawek** niższe niż określona **wersja poprawki** są ignorowane w wyborze zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="41c52-213">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="41c52-214">Jeśli nie można znaleźć określonej wersji zestawu SDK i odpowiedniej **wersji poprawki** zestawu SDK, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="41c52-214">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="41c52-215">Wersja zestawu SDK składa się z następujących części:</span><span class="sxs-lookup"><span data-stu-id="41c52-215">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="41c52-216">**Wersja funkcji** zestaw .NET Core SDK jest reprezentowana przez pierwszą cyfrę ( `x` ) w ostatniej części cyfry ( `xyz` ) dla wersji zestawu SDK 2.1.100 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="41c52-216">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="41c52-217">Ogólnie rzecz biorąc zestaw .NET Core SDK ma szybszy cykl wydawniczy niż .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41c52-217">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="41c52-218">**Wersja poprawki** jest definiowana przez ostatnie dwie cyfry ( `yz` ) w ostatniej części cyfry ( `xyz` ) dla wersji zestawu SDK 2.1.100 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="41c52-218">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="41c52-219">Na przykład jeśli określisz `2.1.300` jako wersję zestawu SDK, wybór zestawu SDK znajdzie się do, `2.1.399` ale `2.1.400` nie jest traktowany jako wersja poprawki dla programu `2.1.300` .</span><span class="sxs-lookup"><span data-stu-id="41c52-219">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="41c52-220">Wersje zestaw .NET Core SDK `2.1.100` za pomocą `2.1.201` zostały wydane podczas przejścia między schematami numerów wersji i nie obsługują poprawnie `xyz` notacji.</span><span class="sxs-lookup"><span data-stu-id="41c52-220">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="41c52-221">Zdecydowanie zalecamy, aby określić te wersje w pliku *Global. JSON* , że określone wersje znajdują się na komputerach docelowych.</span><span class="sxs-lookup"><span data-stu-id="41c52-221">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="41c52-222">Rozwiązywanie problemów z ostrzeżeniami kompilacji</span><span class="sxs-lookup"><span data-stu-id="41c52-222">Troubleshoot build warnings</span></span>

* <span data-ttu-id="41c52-223">Poniższe ostrzeżenie wskazuje, że projekt został skompilowany przy użyciu wstępnej wersji zestaw .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="41c52-223">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="41c52-224">Pracujesz z wersją zapoznawczą zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="41c52-224">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="41c52-225">Możesz zdefiniować wersję zestawu SDK za pośrednictwem pliku Global. JSON w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="41c52-225">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="41c52-226">Więcej o <https://go.microsoft.com/fwlink/?linkid=869452> .</span><span class="sxs-lookup"><span data-stu-id="41c52-226">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="41c52-227">Wersje zestaw .NET Core SDK mają historię i zobowiązanie o wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="41c52-227">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="41c52-228">Jeśli jednak nie chcesz używać wersji wstępnej, Sprawdź różne strategie, których można użyć z zestawem SDK .NET Core 3,0 lub nowszą wersją w sekcji [allowPrerelease](#allowprerelease) .</span><span class="sxs-lookup"><span data-stu-id="41c52-228">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="41c52-229">W przypadku maszyn, na których nigdy nie zainstalowano platformy .NET Core 3,0 lub nowszego lub zestawu SDK, należy utworzyć plik *Global. JSON* i określić dokładną wersję, która ma być używana.</span><span class="sxs-lookup"><span data-stu-id="41c52-229">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="41c52-230">Poniższe ostrzeżenie wskazuje, że projekt jest ukierunkowany na EF Core 1,0 lub 1,1, co nie jest zgodne z zestawem SDK .NET Core 2,1 i nowszymi wersjami:</span><span class="sxs-lookup"><span data-stu-id="41c52-230">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="41c52-231">Projekt startowy "{startupProject}" wskazuje platformę ". NETCoreApp "wersja" {targetFrameworkVersion} ".</span><span class="sxs-lookup"><span data-stu-id="41c52-231">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="41c52-232">Ta wersja narzędzi wiersza polecenia Entity Framework Core .NET obsługuje tylko wersję 2,0 lub nowszą.</span><span class="sxs-lookup"><span data-stu-id="41c52-232">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="41c52-233">Aby uzyskać informacje na temat używania starszych wersji narzędzi, zobacz <https://go.microsoft.com/fwlink/?linkid=871254> .</span><span class="sxs-lookup"><span data-stu-id="41c52-233">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="41c52-234">Począwszy od zestawu SDK programu .NET Core 2,1 (wersja 2.1.300), `dotnet ef` polecenie znajduje się w zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="41c52-234">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="41c52-235">Aby skompilować projekt, zainstaluj na komputerze zestaw SDK programu .NET Core 2,0 (wersja 2.1.201) lub wcześniejszy i zdefiniuj żądaną wersję zestawu SDK przy użyciu pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="41c52-235">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="41c52-236">Aby uzyskać więcej informacji na temat tego `dotnet ef` polecenia, zobacz [EF Core narzędzia wiersza polecenia programu .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="41c52-236">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="41c52-237">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41c52-237">See also</span></span>

- [<span data-ttu-id="41c52-238">Jak są rozwiązywane zestawy SDK projektu</span><span class="sxs-lookup"><span data-stu-id="41c52-238">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
