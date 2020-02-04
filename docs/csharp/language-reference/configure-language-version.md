---
title: C#Obsługa wersji języka — C# Przewodnik
description: Dowiedz się, C# w jaki sposób wersja językowa jest określana na podstawie projektu, i różne wartości, które można dostosować ręcznie do programu.
ms.date: 07/10/2019
ms.openlocfilehash: 3c1035d983660ea0a945e4d4b7b72c69736c90cb
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980135"
---
# <a name="c-language-versioning"></a><span data-ttu-id="d25e4-103">C#przechowywanie wersji języka</span><span class="sxs-lookup"><span data-stu-id="d25e4-103">C# language versioning</span></span>

<span data-ttu-id="d25e4-104">Najnowszy C# kompilator Określa domyślną wersję językową opartą na docelowej platformie lub strukturach projektu.</span><span class="sxs-lookup"><span data-stu-id="d25e4-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="d25e4-105">Jest to spowodowane tym C# , że język może mieć funkcje, które są zależne od typów lub składników środowiska uruchomieniowego, które nie są dostępne w każdej implementacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="d25e4-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="d25e4-106">Zapewnia to również, że dla każdego elementu docelowego projektu jest tworzona z myślą o największej zgodnej wersji językowej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="d25e4-107">Reguły w tym artykule mają zastosowanie do kompilatora dostarczonego z programem Visual Studio 2019 lub zestawem SDK programu .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d25e4-107">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="d25e4-108">C# Kompilatory, które są częścią instalacji programu Visual Studio 2017 lub starszej wersji zestaw .NET Core SDK C# wersje Target 7,0 domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d25e4-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="d25e4-109">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="d25e4-109">Defaults</span></span>

<span data-ttu-id="d25e4-110">Kompilator określa wartość domyślną na podstawie następujących reguł:</span><span class="sxs-lookup"><span data-stu-id="d25e4-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="d25e4-111">Platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="d25e4-111">Target framework</span></span>|<span data-ttu-id="d25e4-112">Wersja programu</span><span class="sxs-lookup"><span data-stu-id="d25e4-112">version</span></span>|<span data-ttu-id="d25e4-113">C#domyślna wersja języka</span><span class="sxs-lookup"><span data-stu-id="d25e4-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="d25e4-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d25e4-114">.NET Core</span></span>|<span data-ttu-id="d25e4-115">wersji</span><span class="sxs-lookup"><span data-stu-id="d25e4-115">3.x</span></span>|<span data-ttu-id="d25e4-116">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="d25e4-116">C# 8.0</span></span>|
|<span data-ttu-id="d25e4-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d25e4-117">.NET Core</span></span>|<span data-ttu-id="d25e4-118">2.x</span><span class="sxs-lookup"><span data-stu-id="d25e4-118">2.x</span></span>|<span data-ttu-id="d25e4-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d25e4-119">C# 7.3</span></span>|
|<span data-ttu-id="d25e4-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="d25e4-120">.NET Standard</span></span>|<span data-ttu-id="d25e4-121">2.1</span><span class="sxs-lookup"><span data-stu-id="d25e4-121">2.1</span></span>|<span data-ttu-id="d25e4-122">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="d25e4-122">C# 8.0</span></span>|
|<span data-ttu-id="d25e4-123">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="d25e4-123">.NET Standard</span></span>|<span data-ttu-id="d25e4-124">2.0</span><span class="sxs-lookup"><span data-stu-id="d25e4-124">2.0</span></span>|<span data-ttu-id="d25e4-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d25e4-125">C# 7.3</span></span>|
|<span data-ttu-id="d25e4-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="d25e4-126">.NET Standard</span></span>|<span data-ttu-id="d25e4-127">1.x</span><span class="sxs-lookup"><span data-stu-id="d25e4-127">1.x</span></span>|<span data-ttu-id="d25e4-128">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d25e4-128">C# 7.3</span></span>|
|<span data-ttu-id="d25e4-129">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d25e4-129">.NET Framework</span></span>|<span data-ttu-id="d25e4-130">wszystkie</span><span class="sxs-lookup"><span data-stu-id="d25e4-130">all</span></span>|<span data-ttu-id="d25e4-131">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d25e4-131">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="d25e4-132">Domyślnie dla wersji zapoznawczych</span><span class="sxs-lookup"><span data-stu-id="d25e4-132">Default for previews</span></span>

<span data-ttu-id="d25e4-133">Jeśli projekt jest przeznaczony dla platformy wersji zapoznawczej, która ma odpowiednią wersję języka wersji zapoznawczej, używana jest wersja języka w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-133">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="d25e4-134">Dzięki temu można korzystać z najnowszych funkcji, które są gwarantowane do pracy z tą wersją zapoznawczą w dowolnym środowisku bez wpływu na projekty przeznaczone dla wydanej wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d25e4-134">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="d25e4-135">Zastąp wartość domyślną</span><span class="sxs-lookup"><span data-stu-id="d25e4-135">Override a default</span></span>

<span data-ttu-id="d25e4-136">Jeśli musisz określić C# wersję jawnie, możesz to zrobić na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="d25e4-136">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="d25e4-137">Edytuj ręcznie [plik projektu](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="d25e4-137">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="d25e4-138">Ustaw wersję językową [dla wielu projektów w podkatalogu](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="d25e4-138">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="d25e4-139">Skonfiguruj [opcję kompilatora`-langversion`](compiler-options/langversion-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d25e4-139">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="d25e4-140">Edytuj plik projektu</span><span class="sxs-lookup"><span data-stu-id="d25e4-140">Edit the project file</span></span>

<span data-ttu-id="d25e4-141">Możesz ustawić wersję językową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d25e4-141">You can set the language version in your project file.</span></span> <span data-ttu-id="d25e4-142">Jeśli na przykład jawnie chcesz uzyskać dostęp do funkcji w wersji zapoznawczej, Dodaj element podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="d25e4-142">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="d25e4-143">Wartość `preview` używa najnowszej dostępnej wersji języka zapoznawczej C# obsługiwanej przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d25e4-143">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="d25e4-144">Konfigurowanie wielu projektów</span><span class="sxs-lookup"><span data-stu-id="d25e4-144">Configure multiple projects</span></span>

<span data-ttu-id="d25e4-145">Aby skonfigurować wiele projektów, można utworzyć plik **Directory. Build. props** , który zawiera element `<LangVersion>`.</span><span class="sxs-lookup"><span data-stu-id="d25e4-145">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="d25e4-146">Zwykle jest to wykonywane w katalogu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d25e4-146">You typically do that in your solution directory.</span></span> <span data-ttu-id="d25e4-147">Dodaj następujący element do pliku **Directory. Build. props** w katalogu rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="d25e4-147">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="d25e4-148">Teraz kompilacje w każdym podkatalogu katalogu zawierającego ten plik będą korzystać z wersji zapoznawczej C# .</span><span class="sxs-lookup"><span data-stu-id="d25e4-148">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="d25e4-149">Aby uzyskać więcej informacji, zobacz artykuł na temat [dostosowywania kompilacji](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="d25e4-149">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="d25e4-150">C#dokumentacja wersji języka</span><span class="sxs-lookup"><span data-stu-id="d25e4-150">C# language version reference</span></span>

<span data-ttu-id="d25e4-151">W poniższej tabeli przedstawiono wszystkie bieżące C# wersje językowe.</span><span class="sxs-lookup"><span data-stu-id="d25e4-151">The following table shows all current C# language versions.</span></span> <span data-ttu-id="d25e4-152">Kompilator może niekoniecznie zrozumieć każdą wartość, jeśli jest starszy.</span><span class="sxs-lookup"><span data-stu-id="d25e4-152">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="d25e4-153">Jeśli zainstalujesz program .NET Core 3,0, będziesz mieć dostęp do wszystkich elementów na liście.</span><span class="sxs-lookup"><span data-stu-id="d25e4-153">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="d25e4-154">Wartość</span><span class="sxs-lookup"><span data-stu-id="d25e4-154">Value</span></span>|<span data-ttu-id="d25e4-155">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="d25e4-155">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="d25e4-156">wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="d25e4-156">preview</span></span>|<span data-ttu-id="d25e4-157">Kompilator akceptuje całą poprawną składnię języka od najnowszej wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-157">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="d25e4-158">latest</span><span class="sxs-lookup"><span data-stu-id="d25e4-158">latest</span></span>|<span data-ttu-id="d25e4-159">Kompilator akceptuje składnię z najnowszej wydanej wersji kompilatora (w tym wersji pomocniczej).</span><span class="sxs-lookup"><span data-stu-id="d25e4-159">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="d25e4-160">latestMajor</span><span class="sxs-lookup"><span data-stu-id="d25e4-160">latestMajor</span></span>|<span data-ttu-id="d25e4-161">Kompilator akceptuje składnię z najnowszej wydanej wersji głównej kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d25e4-161">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="d25e4-162">8.0</span><span class="sxs-lookup"><span data-stu-id="d25e4-162">8.0</span></span>|<span data-ttu-id="d25e4-163">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 8,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-163">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="d25e4-164">7.3</span><span class="sxs-lookup"><span data-stu-id="d25e4-164">7.3</span></span>|<span data-ttu-id="d25e4-165">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,3 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-165">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="d25e4-166">7.2</span><span class="sxs-lookup"><span data-stu-id="d25e4-166">7.2</span></span>|<span data-ttu-id="d25e4-167">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,2 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-167">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="d25e4-168">7.1</span><span class="sxs-lookup"><span data-stu-id="d25e4-168">7.1</span></span>|<span data-ttu-id="d25e4-169">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,1 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-169">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="d25e4-170">7</span><span class="sxs-lookup"><span data-stu-id="d25e4-170">7</span></span>|<span data-ttu-id="d25e4-171">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-171">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="d25e4-172">6</span><span class="sxs-lookup"><span data-stu-id="d25e4-172">6</span></span>|<span data-ttu-id="d25e4-173">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 6,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-173">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="d25e4-174">5</span><span class="sxs-lookup"><span data-stu-id="d25e4-174">5</span></span>|<span data-ttu-id="d25e4-175">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 5,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-175">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="d25e4-176">4</span><span class="sxs-lookup"><span data-stu-id="d25e4-176">4</span></span>|<span data-ttu-id="d25e4-177">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 4,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-177">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="d25e4-178">3</span><span class="sxs-lookup"><span data-stu-id="d25e4-178">3</span></span>|<span data-ttu-id="d25e4-179">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 3,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="d25e4-179">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="d25e4-180">ISO-2</span><span class="sxs-lookup"><span data-stu-id="d25e4-180">ISO-2</span></span>|<span data-ttu-id="d25e4-181">Kompilator akceptuje tylko składnię zawartą w normie ISO/ C# IEC 23270:2006 (2,0).</span><span class="sxs-lookup"><span data-stu-id="d25e4-181">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0).</span></span> |
|<span data-ttu-id="d25e4-182">ISO-1</span><span class="sxs-lookup"><span data-stu-id="d25e4-182">ISO-1</span></span>|<span data-ttu-id="d25e4-183">Kompilator akceptuje tylko składnię zawartą w ISO/IEC 23270:2003 C# (1.0/1.2).</span><span class="sxs-lookup"><span data-stu-id="d25e4-183">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2).</span></span> |
