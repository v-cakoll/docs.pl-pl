---
title: Omówienie Global.JSON
description: Dowiedz się, jak za pomocą plik global.json Ustaw wersję .NET Core SDK, podczas uruchamiania poleceń interfejsu wiersza polecenia platformy .NET Core.
ms.date: 12/03/2018
ms.custom: updateeachrelease, seodec18
ms.openlocfilehash: a3d90e39401ece8d106d89a7533b7c1e1e4433cd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632401"
---
# <a name="globaljson-overview"></a><span data-ttu-id="07b41-103">Omówienie Global.JSON</span><span class="sxs-lookup"><span data-stu-id="07b41-103">global.json overview</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

<span data-ttu-id="07b41-104">*Global.json* pliku umożliwia definiowanie, która wersja programu .NET Core SDK jest używany podczas uruchamiania poleceń interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07b41-104">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="07b41-105">Wybieranie zestawu .NET Core SDK jest niezależna od określając docelowy system operacyjny projektu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="07b41-105">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="07b41-106">Wersja zestawu SDK programu .NET Core wskazuje, które wersje narzędzi interfejsu wiersza polecenia platformy .NET Core są używane.</span><span class="sxs-lookup"><span data-stu-id="07b41-106">The .NET Core SDK version indicates which versions of the .NET Core CLI tools are used.</span></span> <span data-ttu-id="07b41-107">Ogólnie rzecz biorąc, do którego chcesz użyć najnowszej wersji narzędzia, więc nie *global.json* potrzebny jest plik.</span><span class="sxs-lookup"><span data-stu-id="07b41-107">In general, you want to use the latest version of the tools, so no *global.json* file is needed.</span></span>

<span data-ttu-id="07b41-108">Aby uzyskać więcej informacji na temat określania środowiska uruchomieniowego zamiast tego zobacz [ustalać platformy docelowe](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="07b41-108">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="07b41-109">Wyszukuje zestaw .NET core SDK *global.json* plik w bieżącym katalogu roboczym (co nie jest zawsze taki sam jak katalog projektu) lub jeden z jego katalogi nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="07b41-109">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="07b41-110">global.json schema</span><span class="sxs-lookup"><span data-stu-id="07b41-110">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="07b41-111">sdk</span><span class="sxs-lookup"><span data-stu-id="07b41-111">sdk</span></span>

<span data-ttu-id="07b41-112">Wpisz: Obiekt</span><span class="sxs-lookup"><span data-stu-id="07b41-112">Type: Object</span></span>

<span data-ttu-id="07b41-113">Określa informacje dotyczące zestawu .NET Core SDK, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="07b41-113">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="07b41-114">version</span><span class="sxs-lookup"><span data-stu-id="07b41-114">version</span></span>

<span data-ttu-id="07b41-115">Wpisz: String</span><span class="sxs-lookup"><span data-stu-id="07b41-115">Type: String</span></span>

<span data-ttu-id="07b41-116">Wersja zestawu .NET Core SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="07b41-116">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="07b41-117">Należy pamiętać, że w tym polu:</span><span class="sxs-lookup"><span data-stu-id="07b41-117">Note that this field:</span></span>

- <span data-ttu-id="07b41-118">Nie ma obsługi symboli wieloznacznych, oznacza to, że pełny numer wersji musi być określony.</span><span class="sxs-lookup"><span data-stu-id="07b41-118">Doesn't have globbing support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="07b41-119">Nie obsługuje zakresów wersji.</span><span class="sxs-lookup"><span data-stu-id="07b41-119">Doesn't support version ranges.</span></span>

<span data-ttu-id="07b41-120">W poniższym przykładzie pokazano zawartość *global.json* pliku:</span><span class="sxs-lookup"><span data-stu-id="07b41-120">The following example shows the contents of a *global.json* file:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="07b41-121">Global.JSON i zestawu .NET Core interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="07b41-121">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="07b41-122">Warto wiedzieć, które wersje są dostępne, aby ustawić jeden *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="07b41-122">It's helpful to know which versions are available in order to set one in the *global.json* file.</span></span> <span data-ttu-id="07b41-123">Można znaleźć pełną listę obsługiwanych dostępnych zestawów SDK na [pobiera .NET](https://www.microsoft.com/net/download/all) lokacji.</span><span class="sxs-lookup"><span data-stu-id="07b41-123">You can find the full list of supported available SDKs at the [.NET Downloads](https://www.microsoft.com/net/download/all) site.</span></span> <span data-ttu-id="07b41-124">Począwszy od zestawu SDK programu .NET Core 2.1 można uruchomić następujące polecenie, aby sprawdzić, które wersje zestawu SDK są już zainstalowane na komputerze:</span><span class="sxs-lookup"><span data-stu-id="07b41-124">Starting with .NET Core 2.1 SDK, you can run the following command to verify which SDK versions are already installed on your machine:</span></span>

```console
dotnet --list-sdks
```

<span data-ttu-id="07b41-125">Aby zainstalować dodatkowe wersje programu .NET Core SDK na maszynie, odwiedź stronę [pobiera .NET](https://www.microsoft.com/net/download/all) lokacji.</span><span class="sxs-lookup"><span data-stu-id="07b41-125">To install additional .NET Core SDK versions on your machine, visit the [.NET Downloads](https://www.microsoft.com/net/download/all) site.</span></span>

<span data-ttu-id="07b41-126">Można utworzyć nową *global.json* plik w bieżącym katalogu, wykonując [dotnet nowe](dotnet-new.md) polecenia podobnego do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="07b41-126">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```console
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a><span data-ttu-id="07b41-127">Reguł dopasowania</span><span class="sxs-lookup"><span data-stu-id="07b41-127">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="07b41-128">Reguł dopasowania podlegają apphost, który jest częścią środowiska uruchomieniowego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07b41-128">The matching rules are governed by the apphost, which is part of the .NET Core runtime.</span></span>
> <span data-ttu-id="07b41-129">Najnowszą wersję hosta jest używana, jeśli masz wiele środowisk uruchomieniowych zainstalowane obok siebie.</span><span class="sxs-lookup"><span data-stu-id="07b41-129">The latest version of the host is used when you have multiple runtimes installed side-by-side.</span></span>

<span data-ttu-id="07b41-130">Począwszy od programu .NET Core 2.0, obowiązują następujące reguły podczas ustalania, która wersja zestawu SDK do użycia:</span><span class="sxs-lookup"><span data-stu-id="07b41-130">Starting with .NET Core 2.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="07b41-131">Jeśli nie *global.json* znajduje się plik lub *global.json* nie określa wersji zestawu SDK, jego Najnowsza zainstalowana wersja zestawu SDK jest używany.</span><span class="sxs-lookup"><span data-stu-id="07b41-131">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="07b41-132">Najnowsza wersja zestawu SDK może być wersji lub wersji wstępnej — najwyższy wins numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="07b41-132">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>
- <span data-ttu-id="07b41-133">Jeśli *global.json* Określ wersję zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="07b41-133">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="07b41-134">Jeśli określonej wersji zestawu SDK znajduje się na komputerze, że dokładna wersja jest używana.</span><span class="sxs-lookup"><span data-stu-id="07b41-134">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="07b41-135">Jeśli nie można odnaleźć określonej wersji zestawu SDK na maszynie, najnowsze zainstalowany zestaw SDK **wersja poprawki zabezpieczeń** to wersja jest używana.</span><span class="sxs-lookup"><span data-stu-id="07b41-135">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="07b41-136">Najnowsze zainstalowany zestaw SDK **wersja poprawki zabezpieczeń** może być wersji lub wersji wstępnej — najwyższa wersja numeru wins.</span><span class="sxs-lookup"><span data-stu-id="07b41-136">Latest installed SDK **patch version** can be either release or pre-release - the highest version number wins.</span></span> <span data-ttu-id="07b41-137">W programie .NET Core 2.1 lub nowszym **poprawki wersji** niższa niż **wersja poprawki zabezpieczeń** określonego są ignorowane w zaznaczeniu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="07b41-137">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="07b41-138">Jeśli określona wersja zestawu SDK i właściwy zestaw SDK **wersja poprawki zabezpieczeń** nie zostanie znaleziony, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="07b41-138">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="07b41-139">Wersja zestawu SDK obecnie składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="07b41-139">The SDK version is currently composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="07b41-140">**Funkcji wersji** programu .NET Core SDK jest reprezentowany przez pierwszą (`x`) w ostatniej części numeru (`xyz`) dla wersji zestawu SDK 2.1.100 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="07b41-140">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="07b41-141">Ogólnie rzecz biorąc .NET Core SDK ma szybszy cyklu tworzenia wydań niż .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07b41-141">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="07b41-142">**Wersja poprawki zabezpieczeń** jest definiowany przez dwie ostatnie cyfry (`yz`) w ostatniej części numeru (`xyz`) dla wersji zestawu SDK 2.1.100 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="07b41-142">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="07b41-143">Na przykład, jeśli określisz `2.1.300` jako wersję zestawu SDK, wybór zestawu SDK znajduje się maksymalnie `2.1.399` , ale `2.1.400` nie jest uważany za wersję poprawki dla `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="07b41-143">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="07b41-144">Wersje programu .NET core SDK `2.1.100` za pośrednictwem `2.1.201` zostały wydane podczas przejścia między schematami numeru wersji i nie zapewnia prawidłowej obsługi `xyz` notacji.</span><span class="sxs-lookup"><span data-stu-id="07b41-144">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="07b41-145">Zdecydowanie zaleca się Jeśli określisz te wersje w *global.json* pliku, który można zapewnić, że określone wersje są na komputerach docelowych.</span><span class="sxs-lookup"><span data-stu-id="07b41-145">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

<span data-ttu-id="07b41-146">Przy użyciu zestawu SDK programu .NET Core 1.x, jeśli określona wersja i dokładnego dopasowania został znaleziony, użyto jego Najnowsza zainstalowana wersja zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="07b41-146">With .NET Core SDK 1.x, if you specified a version and no exact match was found, the latest installed SDK version was used.</span></span> <span data-ttu-id="07b41-147">Najnowsza wersja zestawu SDK może być wersji lub wersji wstępnej — najwyższy wins numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="07b41-147">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="07b41-148">Rozwiązywanie problemów z ostrzeżenia kompilacji</span><span class="sxs-lookup"><span data-stu-id="07b41-148">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="07b41-149">Pracujesz z wersję zapoznawczą programu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="07b41-149">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="07b41-150">Wersja zestawu SDK przy użyciu pliku global.json można zdefiniować w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="07b41-150">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="07b41-151">Więcej na stronie <https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="07b41-151">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="07b41-152">To ostrzeżenie wskazuje, że projekt jest kompilowany przy użyciu zestawu .NET Core SDK w wersji zapoznawczej zgodnie z objaśnieniem w [reguł dopasowania](#matching-rules) sekcji.</span><span class="sxs-lookup"><span data-stu-id="07b41-152">This warning indicates that your project is being compiled using a preview version of the .NET Core SDK, as explained in the [Matching rules](#matching-rules) section.</span></span> <span data-ttu-id="07b41-153">Wersje programu .NET core SDK ma historię i zaangażowanie on wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="07b41-153">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="07b41-154">Jeśli nie chcesz użyć wersji zapoznawczej, jednak dodać *global.json* pliku do struktury projektu hierarchii w celu określenia którą wersję zestawu SDK i wykorzystaj `dotnet --list-sdks` aby upewnić się, że na komputerze jest zainstalowana wersja.</span><span class="sxs-lookup"><span data-stu-id="07b41-154">However, if you don't want to use a preview version, add a *global.json* file to your project hierarchy structure to specify which SDK version to use, and use `dotnet --list-sdks` to confirm that the version is installed on your machine.</span></span> <span data-ttu-id="07b41-155">Po wydaniu nowej wersji do nowej wersji, albo usuń *global.json* pliku, lub zaktualizuj go do korzystania z nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="07b41-155">When a new version is released, to use the new version, either remove the *global.json* file or update it to use the newer version.</span></span>

> [!WARNING]
> <span data-ttu-id="07b41-156">Platformy elementy docelowe projektu "{Projekt startowy}" Uruchamianie ". Element NETCoreApp "wersja"{targetFrameworkVersion}".</span><span class="sxs-lookup"><span data-stu-id="07b41-156">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="07b41-157">Ta wersja narzędzia wiersza polecenia programu Entity Framework Core .NET obsługuje tylko w wersji 2.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="07b41-157">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="07b41-158">Aby uzyskać informacji na temat używania starszych wersji narzędzia Zobacz <https://go.microsoft.com/fwlink/?linkid=871254></span><span class="sxs-lookup"><span data-stu-id="07b41-158">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="07b41-159">Począwszy od .NET Core 2.1 SDK (wersja 2.1.300) `dotnet ef` polecenia jest uwzględniony w zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="07b41-159">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="07b41-160">To ostrzeżenie wskazuje, że projekt jest ukierunkowany EF Core 1.0 i 1.1, która nie jest zgodna z zestawu SDK programu .NET Core 2.1 i nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="07b41-160">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions.</span></span> <span data-ttu-id="07b41-161">Aby skompilować projekt, zainstaluj zestaw .NET Core 2.0 SDK (wersja 2.1.201) i starszych na Twojej maszynie i definiują żądany zestaw SDK w wersji przy użyciu *global.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="07b41-161">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="07b41-162">Aby uzyskać więcej informacji na temat `dotnet ef` polecenia, zobacz [narzędzia wiersza polecenia platformy .NET Core EF](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="07b41-162">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="07b41-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07b41-163">See also</span></span>

- [<span data-ttu-id="07b41-164">Jak są rozwiązywane projektów zestawów SDK</span><span class="sxs-lookup"><span data-stu-id="07b41-164">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
