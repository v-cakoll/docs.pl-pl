---
title: Wybierz C# wersję językową — przewodnik C#
description: Konfigurowanie kompilatora do sprawdzania poprawności składni przy użyciu wersji określonego kompilatora
ms.date: 05/24/2018
ms.openlocfilehash: 9b91e62168ced0f373e1a55def8b279dc64833d8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208383"
---
# <a name="select-the-c-language-version"></a><span data-ttu-id="9c96d-103">Wybierz wersję języka C#</span><span class="sxs-lookup"><span data-stu-id="9c96d-103">Select the C# language version</span></span>

<span data-ttu-id="9c96d-104">Kompilator języka C# domyślnie przyjmowana jest najnowsza wersja główna języka, który został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="9c96d-104">The C# compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="9c96d-105">Można skompilować żadnego projektu przy użyciu nowej wersji punkt języka.</span><span class="sxs-lookup"><span data-stu-id="9c96d-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="9c96d-106">Wybieranie nowszej wersji języka umożliwia projektu korzystać z najnowszych funkcji języka.</span><span class="sxs-lookup"><span data-stu-id="9c96d-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="9c96d-107">W innych sytuacjach konieczne może zweryfikować, czy czysto kompiluje projektu przy użyciu starszej wersji języka.</span><span class="sxs-lookup"><span data-stu-id="9c96d-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="9c96d-108">Ta funkcja zapewnia oddzielenie decyzję, aby zainstalować nowe wersje zestawu SDK i narzędzia w środowisku projektowania z decyzji, aby włączyć nowe funkcje językowe w projekcie.</span><span class="sxs-lookup"><span data-stu-id="9c96d-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="9c96d-109">Najnowsze narzędzia i zestawu SDK można zainstalować na komputerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c96d-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="9c96d-110">Każdy projekt można skonfigurować do korzystania z określonej wersji języka dla jego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c96d-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="9c96d-111">Istnieje kilka sposobów, aby ustawić wersję językową:</span><span class="sxs-lookup"><span data-stu-id="9c96d-111">There are several ways to set the language version:</span></span>

- <span data-ttu-id="9c96d-112">Zależne od [szybkie działanie programu Visual Studio](#visual-studio-quick-action).</span><span class="sxs-lookup"><span data-stu-id="9c96d-112">Rely on a [Visual Studio quick action](#visual-studio-quick-action).</span></span>
- <span data-ttu-id="9c96d-113">Ustaw wersję językową [interfejsu użytkownika programu Visual Studio](#set-the-language-version-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="9c96d-113">Set the language version in the [Visual Studio UI](#set-the-language-version-in-visual-studio).</span></span>
- <span data-ttu-id="9c96d-114">Ręcznie Edytuj Twojej [ **.csproj** pliku](#edit-the-csproj-file).</span><span class="sxs-lookup"><span data-stu-id="9c96d-114">Manually edit your [**.csproj** file](#edit-the-csproj-file).</span></span>
- <span data-ttu-id="9c96d-115">Ustaw wersję językową [dla wielu projektów w podkatalogu](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="9c96d-115">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="9c96d-116">Skonfiguruj [ `-langversion` — opcja kompilatora](#set-the-langversion-compiler-option).</span><span class="sxs-lookup"><span data-stu-id="9c96d-116">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

## <a name="visual-studio-quick-action"></a><span data-ttu-id="9c96d-117">Visual Studio szybkich akcji.</span><span class="sxs-lookup"><span data-stu-id="9c96d-117">Visual Studio quick action</span></span>

<span data-ttu-id="9c96d-118">Visual Studio ułatwia określenie wersji językowej, które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="9c96d-118">Visual Studio helps you determine the language version you need.</span></span> <span data-ttu-id="9c96d-119">Jeśli używasz funkcji języka, który nie jest dostępny dla aktualnie skonfigurowana wersja programu Visual Studio zawiera potencjalne rozwiązania można zaktualizować wersji językowej dla projektu.</span><span class="sxs-lookup"><span data-stu-id="9c96d-119">If you use a language feature that is not available for the currently configured version, Visual Studio shows a potential fix to update the language version for the project.</span></span>

## <a name="set-the-language-version-in-visual-studio"></a><span data-ttu-id="9c96d-120">Ustaw wersja językowa programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c96d-120">Set the language version in Visual Studio</span></span>

<span data-ttu-id="9c96d-121">Wersja można ustawić w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c96d-121">You can set the version in Visual Studio.</span></span> <span data-ttu-id="9c96d-122">Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9c96d-122">Right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="9c96d-123">Wybierz **kompilacji** i wybierz **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9c96d-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="9c96d-124">Na liście rozwijanej wybierz wersję.</span><span class="sxs-lookup"><span data-stu-id="9c96d-124">In the dropdown, select the version.</span></span> <span data-ttu-id="9c96d-125">Na poniższej ilustracji przedstawiono ustawienie "najnowszej":</span><span class="sxs-lookup"><span data-stu-id="9c96d-125">The following image shows the "latest" setting:</span></span>

![Zrzut ekranu przedstawiający ustawienia zaawansowane kompilacji, w którym można określić wersji językowej](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> <span data-ttu-id="9c96d-127">Jeśli używasz programu Visual Studio IDE do aktualizacji plików csproj IDE tworzy osobne węzły dla każdej konfiguracji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c96d-127">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="9c96d-128">Będzie zazwyczaj wartość taka sama we wszystkich konfiguracjach kompilacji, ale należy jawnie ustaw dla każdej konfiguracji kompilacji, lub wybierz opcję "Wszystkie konfiguracje" po zmodyfikowaniu tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="9c96d-128">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="9c96d-129">W pliku csproj, pojawi się następujące:</span><span class="sxs-lookup"><span data-stu-id="9c96d-129">You'll see the following in your csproj file:</span></span>
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a><span data-ttu-id="9c96d-130">Edytuj plik csproj</span><span class="sxs-lookup"><span data-stu-id="9c96d-130">Edit the csproj file</span></span>

<span data-ttu-id="9c96d-131">Można ustawić w wersji językowej programu **.csproj** pliku.</span><span class="sxs-lookup"><span data-stu-id="9c96d-131">You can set the language version in your **.csproj** file.</span></span> <span data-ttu-id="9c96d-132">Dodaj element podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="9c96d-132">Add an element like the following:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="9c96d-133">Wartość `latest` korzysta z najnowszej wersji pomocniczej języka C#.</span><span class="sxs-lookup"><span data-stu-id="9c96d-133">The value `latest` uses the latest minor version of the C# language.</span></span> <span data-ttu-id="9c96d-134">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="9c96d-134">Valid values are:</span></span>

|<span data-ttu-id="9c96d-135">Wartość</span><span class="sxs-lookup"><span data-stu-id="9c96d-135">Value</span></span>|<span data-ttu-id="9c96d-136">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="9c96d-136">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="9c96d-137">default</span><span class="sxs-lookup"><span data-stu-id="9c96d-137">default</span></span>|<span data-ttu-id="9c96d-138">Kompilator akceptuje wszystkie składni języka prawidłowe z najnowszej wersji głównych, który może obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="9c96d-138">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="9c96d-139">ISO-1</span><span class="sxs-lookup"><span data-stu-id="9c96d-139">ISO-1</span></span>|<span data-ttu-id="9c96d-140">Kompilator akceptuje tylko składni, który znajduje się w 23270:2003 ISO/IEC C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="9c96d-140">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
|<span data-ttu-id="9c96d-141">ISO-2</span><span class="sxs-lookup"><span data-stu-id="9c96d-141">ISO-2</span></span>|<span data-ttu-id="9c96d-142">Kompilator akceptuje tylko składni, który znajduje się w 23270:2006 ISO/IEC C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="9c96d-142">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="9c96d-143">3</span><span class="sxs-lookup"><span data-stu-id="9c96d-143">3</span></span>|<span data-ttu-id="9c96d-144">Kompilator akceptuje tylko składnię, która jest dostępna w C# 3.0 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="9c96d-144">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="9c96d-145">4</span><span class="sxs-lookup"><span data-stu-id="9c96d-145">4</span></span>|<span data-ttu-id="9c96d-146">Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 4.0 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="9c96d-146">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="9c96d-147">5</span><span class="sxs-lookup"><span data-stu-id="9c96d-147">5</span></span>|<span data-ttu-id="9c96d-148">Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 5.0 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="9c96d-148">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="9c96d-149">6</span><span class="sxs-lookup"><span data-stu-id="9c96d-149">6</span></span>|<span data-ttu-id="9c96d-150">Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 6.0 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="9c96d-150">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="9c96d-151">7</span><span class="sxs-lookup"><span data-stu-id="9c96d-151">7</span></span>|<span data-ttu-id="9c96d-152">Kompilator akceptuje tylko składnię, która jest dostępna w C# w wersji 7.0 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="9c96d-152">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="9c96d-153">7.1</span><span class="sxs-lookup"><span data-stu-id="9c96d-153">7.1</span></span>|<span data-ttu-id="9c96d-154">Kompilator akceptuje tylko składnię, która jest dostępna w C# 7.1 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="9c96d-154">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="9c96d-155">7.2</span><span class="sxs-lookup"><span data-stu-id="9c96d-155">7.2</span></span>|<span data-ttu-id="9c96d-156">Kompilator akceptuje tylko składnię, która jest dostępna w C# 7.2 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="9c96d-156">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="9c96d-157">7.3</span><span class="sxs-lookup"><span data-stu-id="9c96d-157">7.3</span></span>|<span data-ttu-id="9c96d-158">Kompilator akceptuje tylko składnię, która jest dostępna w C# 7.3 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="9c96d-158">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="9c96d-159">najnowsze</span><span class="sxs-lookup"><span data-stu-id="9c96d-159">latest</span></span>|<span data-ttu-id="9c96d-160">Kompilator akceptuje wszystkie składni odpowiedni język, który może obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="9c96d-160">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="9c96d-161">Ciągi specjalne `default` i `latest` rozpoznać najnowszej głównej (C# 7.0) i pomocnicza wersji językowych (C# 7.3) odpowiednio zainstalowana na maszynie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c96d-161">The special strings `default` and `latest` resolve to the latest major (C# 7.0) and minor (C# 7.3) language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="9c96d-162">Konfigurowanie wielu projektów</span><span class="sxs-lookup"><span data-stu-id="9c96d-162">Configure multiple projects</span></span>

<span data-ttu-id="9c96d-163">Można utworzyć **Directory.build.props** plik zawierający `<LangVersion>` element, aby skonfigurować wiele katalogów.</span><span class="sxs-lookup"><span data-stu-id="9c96d-163">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="9c96d-164">Można zwykle to zrobić w katalogu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9c96d-164">You typically do that in your solution directory.</span></span> <span data-ttu-id="9c96d-165">Dodaj następujący kod do **Directory.build.props** pliku w katalogu rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="9c96d-165">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="9c96d-166">Teraz kompilacje w każdym podkatalogu do katalogu zawierającego plik użyje wersji 7.3 składni języka C#.</span><span class="sxs-lookup"><span data-stu-id="9c96d-166">Now, builds in every subdirectory of the directory containing that file will use C# version 7.3 syntax.</span></span> <span data-ttu-id="9c96d-167">Aby uzyskać więcej informacji, zobacz artykuł na [Dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="9c96d-167">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="9c96d-168">Ustaw langversion — opcja kompilatora</span><span class="sxs-lookup"><span data-stu-id="9c96d-168">Set the langversion compiler option</span></span>

<span data-ttu-id="9c96d-169">Można użyć `-langversion` opcji wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c96d-169">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="9c96d-170">Aby uzyskać więcej informacji, zobacz artykuł na [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9c96d-170">For more information, see the article on the [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) compiler option.</span></span> <span data-ttu-id="9c96d-171">Można wyświetlić listę prawidłowych wartości, wpisując `csc -langversion:?`.</span><span class="sxs-lookup"><span data-stu-id="9c96d-171">You can see a list of the valid values by typing  `csc -langversion:?`.</span></span>
