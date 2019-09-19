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
# <a name="globaljson-overview"></a><span data-ttu-id="69bdf-103">global.json — omówienie</span><span class="sxs-lookup"><span data-stu-id="69bdf-103">global.json overview</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

<span data-ttu-id="69bdf-104">Plik *Global. JSON* pozwala określić, która wersja zestaw .NET Core SDK jest używana podczas uruchamiania poleceń interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69bdf-104">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="69bdf-105">Wybór zestaw .NET Core SDK jest niezależny od określania środowiska uruchomieniowego projektu.</span><span class="sxs-lookup"><span data-stu-id="69bdf-105">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="69bdf-106">Wersja zestaw .NET Core SDK wskazuje, które wersje narzędzi interfejs wiersza polecenia platformy .NET Core są używane.</span><span class="sxs-lookup"><span data-stu-id="69bdf-106">The .NET Core SDK version indicates which versions of the .NET Core CLI tools are used.</span></span> <span data-ttu-id="69bdf-107">Ogólnie rzecz biorąc, chcesz użyć najnowszej wersji narzędzi, dlatego plik *Global. JSON* nie jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="69bdf-107">In general, you want to use the latest version of the tools, so no *global.json* file is needed.</span></span>

<span data-ttu-id="69bdf-108">Aby uzyskać więcej informacji na temat określania środowiska uruchomieniowego, zobacz [platforme docelowe](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="69bdf-108">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="69bdf-109">Zestaw .NET Core SDK szuka pliku *Global. JSON* w bieżącym katalogu roboczym (który nie musi być taki sam jak katalog projektu) lub jednego z jego katalogów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="69bdf-109">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="69bdf-110">global.json schema</span><span class="sxs-lookup"><span data-stu-id="69bdf-110">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="69bdf-111">sdk</span><span class="sxs-lookup"><span data-stu-id="69bdf-111">sdk</span></span>

<span data-ttu-id="69bdf-112">Wpisz: Obiekt</span><span class="sxs-lookup"><span data-stu-id="69bdf-112">Type: Object</span></span>

<span data-ttu-id="69bdf-113">Określa informacje o zestaw .NET Core SDK do wybrania.</span><span class="sxs-lookup"><span data-stu-id="69bdf-113">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="69bdf-114">version</span><span class="sxs-lookup"><span data-stu-id="69bdf-114">version</span></span>

<span data-ttu-id="69bdf-115">Wpisz: String</span><span class="sxs-lookup"><span data-stu-id="69bdf-115">Type: String</span></span>

<span data-ttu-id="69bdf-116">Wersja zestaw .NET Core SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="69bdf-116">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="69bdf-117">Należy zauważyć, że to pole:</span><span class="sxs-lookup"><span data-stu-id="69bdf-117">Note that this field:</span></span>

- <span data-ttu-id="69bdf-118">Nie ma obsługi obsługi symboli wieloznacznych, czyli należy określić pełny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="69bdf-118">Doesn't have globbing support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="69bdf-119">Nie obsługuje zakresów wersji.</span><span class="sxs-lookup"><span data-stu-id="69bdf-119">Doesn't support version ranges.</span></span>

<span data-ttu-id="69bdf-120">Poniższy przykład pokazuje zawartość pliku *Global. JSON* :</span><span class="sxs-lookup"><span data-stu-id="69bdf-120">The following example shows the contents of a *global.json* file:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="69bdf-121">Global. JSON i interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="69bdf-121">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="69bdf-122">Warto wiedzieć, które wersje są dostępne w celu ustawienia jednej w pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="69bdf-122">It's helpful to know which versions are available in order to set one in the *global.json* file.</span></span> <span data-ttu-id="69bdf-123">Pełną listę obsługiwanych zestawów SDK można znaleźć na stronie [pobierania programu .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="69bdf-123">You can find the full list of supported available SDKs at the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span> <span data-ttu-id="69bdf-124">Począwszy od zestawu SDK platformy .NET Core 2,1, możesz uruchomić następujące polecenie, aby sprawdzić, które wersje zestawu SDK są już zainstalowane na maszynie:</span><span class="sxs-lookup"><span data-stu-id="69bdf-124">Starting with .NET Core 2.1 SDK, you can run the following command to verify which SDK versions are already installed on your machine:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="69bdf-125">Aby zainstalować dodatkowe zestaw .NET Core SDK wersje na komputerze, odwiedź stronę [pobieranie platformy .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="69bdf-125">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="69bdf-126">Nowy plik *Global. JSON* można utworzyć w bieżącym katalogu, wykonując polecenie [dotnet New](dotnet-new.md) , podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="69bdf-126">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a><span data-ttu-id="69bdf-127">Reguły dopasowania</span><span class="sxs-lookup"><span data-stu-id="69bdf-127">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="69bdf-128">Reguły dopasowania podlegają AppHost, który jest częścią środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69bdf-128">The matching rules are governed by the apphost, which is part of the .NET Core runtime.</span></span>
> <span data-ttu-id="69bdf-129">Najnowsza wersja hosta jest używana w przypadku, gdy wiele programów uruchomieniowych jest zainstalowanych obok siebie.</span><span class="sxs-lookup"><span data-stu-id="69bdf-129">The latest version of the host is used when you have multiple runtimes installed side-by-side.</span></span>

<span data-ttu-id="69bdf-130">Począwszy od platformy .NET Core 2,0, stosowane są następujące reguły podczas określania, która wersja zestawu SDK ma być używana:</span><span class="sxs-lookup"><span data-stu-id="69bdf-130">Starting with .NET Core 2.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="69bdf-131">Jeśli nie odnaleziono pliku *Global. JSON* lub plik *Global. JSON* nie określa wersji zestawu SDK, zostanie użyta Najnowsza zainstalowana wersja zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="69bdf-131">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="69bdf-132">Najnowsza wersja zestawu SDK może być wydaniem lub wersjami wstępnymi — numer najwyższej wersji usługi WINS.</span><span class="sxs-lookup"><span data-stu-id="69bdf-132">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>
- <span data-ttu-id="69bdf-133">Jeśli *Global. JSON* określi wersję zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="69bdf-133">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="69bdf-134">Jeśli określona wersja zestawu SDK zostanie znaleziona na komputerze, używana jest dokładna wersja.</span><span class="sxs-lookup"><span data-stu-id="69bdf-134">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="69bdf-135">Jeśli na maszynie nie można znaleźć określonej wersji zestawu SDK, zostanie użyta Najnowsza zainstalowana **wersja poprawki** zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="69bdf-135">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="69bdf-136">Najnowsza zainstalowana **wersja poprawki** zestawu SDK może być wydaniem lub w wersji wstępnej — najwyższa wersja usługi WINS.</span><span class="sxs-lookup"><span data-stu-id="69bdf-136">Latest installed SDK **patch version** can be either release or pre-release - the highest version number wins.</span></span> <span data-ttu-id="69bdf-137">W przypadku programu .NET Core 2,1 lub nowszego **wersje poprawek** niższe niż określona **wersja poprawki** są ignorowane w wyborze zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="69bdf-137">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="69bdf-138">Jeśli nie można znaleźć określonej wersji zestawu SDK i odpowiedniej **wersji poprawki** zestawu SDK, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="69bdf-138">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="69bdf-139">Wersja zestawu SDK składa się obecnie z następujących części:</span><span class="sxs-lookup"><span data-stu-id="69bdf-139">The SDK version is currently composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="69bdf-140">**Wersja funkcji** zestaw .NET Core SDK jest reprezentowana przez pierwszą cyfrę (`x`) w ostatniej części cyfry (`xyz`) dla wersji zestawu SDK 2.1.100 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="69bdf-140">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="69bdf-141">Ogólnie rzecz biorąc zestaw .NET Core SDK ma szybszy cykl wydawniczy niż .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69bdf-141">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="69bdf-142">**Wersja poprawki** jest definiowana przez ostatnie dwie cyfry (`yz`) w ostatniej części cyfry (`xyz`) dla wersji zestawu SDK 2.1.100 i wyższych.</span><span class="sxs-lookup"><span data-stu-id="69bdf-142">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="69bdf-143">`2.1.300` Na przykład jeśli określisz jako wersję zestawu SDK, wybór zestawu SDK znajdzie się do `2.1.399` , ale `2.1.400` nie jest traktowany jako `2.1.300`wersja poprawki dla programu.</span><span class="sxs-lookup"><span data-stu-id="69bdf-143">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="69bdf-144">Wersje `2.1.100` zestaw .NET Core SDK za `2.1.201` pomocą zostały wydane podczas przejścia między schematami numerów wersji `xyz` i nie obsługują poprawnie notacji.</span><span class="sxs-lookup"><span data-stu-id="69bdf-144">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="69bdf-145">Zdecydowanie zalecamy, aby określić te wersje w pliku *Global. JSON* , że określone wersje znajdują się na komputerach docelowych.</span><span class="sxs-lookup"><span data-stu-id="69bdf-145">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

<span data-ttu-id="69bdf-146">W przypadku wybrania wersji zestaw .NET Core SDK 1. x, jeśli określono wersję i nie znaleziono dokładnego dopasowania, użyto najnowszej zainstalowanej wersji zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="69bdf-146">With .NET Core SDK 1.x, if you specified a version and no exact match was found, the latest installed SDK version was used.</span></span> <span data-ttu-id="69bdf-147">Najnowsza wersja zestawu SDK może być wydaniem lub wersjami wstępnymi — numer najwyższej wersji usługi WINS.</span><span class="sxs-lookup"><span data-stu-id="69bdf-147">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="69bdf-148">Rozwiązywanie problemów z ostrzeżeniami kompilacji</span><span class="sxs-lookup"><span data-stu-id="69bdf-148">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="69bdf-149">Pracujesz z wersją zapoznawczą zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="69bdf-149">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="69bdf-150">Możesz zdefiniować wersję zestawu SDK za pośrednictwem pliku Global. JSON w bieżącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="69bdf-150">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="69bdf-151">Więcej o<https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="69bdf-151">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="69bdf-152">To ostrzeżenie wskazuje, że projekt jest kompilowany przy użyciu wersji zapoznawczej zestaw .NET Core SDK, zgodnie z opisem w sekcji [reguły dopasowywania](#matching-rules) .</span><span class="sxs-lookup"><span data-stu-id="69bdf-152">This warning indicates that your project is being compiled using a preview version of the .NET Core SDK, as explained in the [Matching rules](#matching-rules) section.</span></span> <span data-ttu-id="69bdf-153">Wersje zestaw .NET Core SDK mają historię i zobowiązanie o wysokiej jakości.</span><span class="sxs-lookup"><span data-stu-id="69bdf-153">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="69bdf-154">Jeśli jednak nie chcesz korzystać z wersji zapoznawczej, Dodaj plik *Global. JSON* do struktury hierarchii projektu, aby określić wersję zestawu SDK, która ma być używana, i `dotnet --list-sdks` potwierdzić, że wersja jest zainstalowana na maszynie.</span><span class="sxs-lookup"><span data-stu-id="69bdf-154">However, if you don't want to use a preview version, add a *global.json* file to your project hierarchy structure to specify which SDK version to use, and use `dotnet --list-sdks` to confirm that the version is installed on your machine.</span></span> <span data-ttu-id="69bdf-155">Po wydaniu nowej wersji, aby użyć nowej wersji, należy usunąć plik *Global. JSON* lub zaktualizować go tak, aby korzystał z nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="69bdf-155">When a new version is released, to use the new version, either remove the *global.json* file or update it to use the newer version.</span></span>

> [!WARNING]
> <span data-ttu-id="69bdf-156">Projekt startowy "{startupProject}" wskazuje platformę ". NETCoreApp "wersja" {targetFrameworkVersion} ".</span><span class="sxs-lookup"><span data-stu-id="69bdf-156">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="69bdf-157">Ta wersja narzędzi wiersza polecenia Entity Framework Core .NET obsługuje tylko wersję 2,0 lub nowszą.</span><span class="sxs-lookup"><span data-stu-id="69bdf-157">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="69bdf-158">Aby uzyskać informacje na temat używania starszych wersji narzędzi, zobacz.<https://go.microsoft.com/fwlink/?linkid=871254></span><span class="sxs-lookup"><span data-stu-id="69bdf-158">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="69bdf-159">Począwszy od zestawu SDK programu .NET Core 2,1 (wersja 2.1.300) `dotnet ef` , polecenie znajduje się w zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="69bdf-159">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="69bdf-160">To ostrzeżenie wskazuje, że projekt jest ukierunkowany na EF Core 1,0 lub 1,1, co nie jest zgodne z zestawem SDK .NET Core 2,1 i nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="69bdf-160">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions.</span></span> <span data-ttu-id="69bdf-161">Aby skompilować projekt, zainstaluj program .NET Core 2,0 SDK (wersja 2.1.201) i jego wcześniejszą wersję na maszynie i zdefiniuj żądaną wersja zestawu SDK przy użyciu pliku *Global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="69bdf-161">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="69bdf-162">Aby uzyskać więcej informacji na `dotnet ef` temat tego polecenia, zobacz [EF Core narzędzia wiersza polecenia programu .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="69bdf-162">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="69bdf-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69bdf-163">See also</span></span>

- [<span data-ttu-id="69bdf-164">Jak są rozwiązywane zestawy SDK projektu</span><span class="sxs-lookup"><span data-stu-id="69bdf-164">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
