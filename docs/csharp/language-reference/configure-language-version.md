---
title: C#Obsługa wersji języka — C# Przewodnik
description: Dowiedz się, C# w jaki sposób wersja językowa jest określana na podstawie projektu, i różne wartości, które można dostosować ręcznie do programu.
ms.date: 07/10/2019
ms.openlocfilehash: fae36f5305e23fbfa1c55c5881e37391670f93ab
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040349"
---
# <a name="c-language-versioning"></a><span data-ttu-id="6f529-103">C#przechowywanie wersji języka</span><span class="sxs-lookup"><span data-stu-id="6f529-103">C# language versioning</span></span>

<span data-ttu-id="6f529-104">Najnowszy C# kompilator Określa domyślną wersję językową opartą na docelowej platformie lub strukturach projektu.</span><span class="sxs-lookup"><span data-stu-id="6f529-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="6f529-105">Jest to spowodowane tym C# , że język może mieć funkcje, które są zależne od typów lub składników środowiska uruchomieniowego, które nie są dostępne w każdej implementacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="6f529-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="6f529-106">Zapewnia to również, że dla każdego elementu docelowego projektu jest tworzona z myślą o największej zgodnej wersji językowej.</span><span class="sxs-lookup"><span data-stu-id="6f529-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="6f529-107">Reguły w tym artykule mają zastosowanie do kompilatora dostarczonego z programem Visual Studio 2019 lub zestawem SDK programu .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6f529-107">The rules in this article apply to the compiler delivered with Visual Studio 2019, or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="6f529-108">C# Kompilatory, które są częścią instalacji programu Visual Studio 2017 lub starszej wersji zestaw .NET Core SDK C# wersje Target 7,0 domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6f529-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="6f529-109">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="6f529-109">Defaults</span></span>

<span data-ttu-id="6f529-110">Kompilator określa wartość domyślną na podstawie następujących reguł:</span><span class="sxs-lookup"><span data-stu-id="6f529-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="6f529-111">Platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="6f529-111">Target framework</span></span>|<span data-ttu-id="6f529-112">version</span><span class="sxs-lookup"><span data-stu-id="6f529-112">version</span></span>|<span data-ttu-id="6f529-113">C#domyślna wersja języka</span><span class="sxs-lookup"><span data-stu-id="6f529-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="6f529-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="6f529-114">.NET Core</span></span>|<span data-ttu-id="6f529-115">wersji</span><span class="sxs-lookup"><span data-stu-id="6f529-115">3.x</span></span>|<span data-ttu-id="6f529-116">C#8,0</span><span class="sxs-lookup"><span data-stu-id="6f529-116">C# 8.0</span></span>|
|<span data-ttu-id="6f529-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="6f529-117">.NET Core</span></span>|<span data-ttu-id="6f529-118">2.x</span><span class="sxs-lookup"><span data-stu-id="6f529-118">2.x</span></span>|<span data-ttu-id="6f529-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="6f529-119">C# 7.3</span></span>|
|<span data-ttu-id="6f529-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="6f529-120">.NET Standard</span></span>|<span data-ttu-id="6f529-121">wszystkie</span><span class="sxs-lookup"><span data-stu-id="6f529-121">all</span></span>|<span data-ttu-id="6f529-122">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="6f529-122">C# 7.3</span></span>|
|<span data-ttu-id="6f529-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f529-123">.NET Framework</span></span>|<span data-ttu-id="6f529-124">wszystkie</span><span class="sxs-lookup"><span data-stu-id="6f529-124">all</span></span>|<span data-ttu-id="6f529-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="6f529-125">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="6f529-126">Domyślnie dla wersji zapoznawczych</span><span class="sxs-lookup"><span data-stu-id="6f529-126">Default for previews</span></span>

<span data-ttu-id="6f529-127">Jeśli projekt jest przeznaczony dla platformy wersji zapoznawczej, która ma odpowiednią wersję języka wersji zapoznawczej, używana jest wersja języka w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="6f529-127">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="6f529-128">Dzięki temu można korzystać z najnowszych funkcji, które są gwarantowane do pracy z tą wersją zapoznawczą w dowolnym środowisku bez wpływu na projekty przeznaczone dla wydanej wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f529-128">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="6f529-129">Zastąp wartość domyślną</span><span class="sxs-lookup"><span data-stu-id="6f529-129">Override a default</span></span>

<span data-ttu-id="6f529-130">Jeśli musisz określić C# wersję jawnie, możesz to zrobić na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="6f529-130">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="6f529-131">Edytuj ręcznie [plik projektu](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="6f529-131">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="6f529-132">Ustaw wersję językową [dla wielu projektów w podkatalogu](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="6f529-132">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="6f529-133">Skonfiguruj [opcję kompilatora `-langversion`](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="6f529-133">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="6f529-134">Edytuj plik projektu</span><span class="sxs-lookup"><span data-stu-id="6f529-134">Edit the project file</span></span>

<span data-ttu-id="6f529-135">Możesz ustawić wersję językową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6f529-135">You can set the language version in your project file.</span></span> <span data-ttu-id="6f529-136">Jeśli na przykład jawnie chcesz uzyskać dostęp do funkcji w wersji zapoznawczej, Dodaj element podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="6f529-136">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="6f529-137">Ta wartość `preview` używa najnowszej dostępnej wersji języka C# zapoznawczej obsługiwanej przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="6f529-137">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="6f529-138">Konfigurowanie wielu projektów</span><span class="sxs-lookup"><span data-stu-id="6f529-138">Configure multiple projects</span></span>

<span data-ttu-id="6f529-139">Można utworzyć plik **Directory. Build. props** , który zawiera `<LangVersion>` element umożliwiający skonfigurowanie wielu katalogów.</span><span class="sxs-lookup"><span data-stu-id="6f529-139">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="6f529-140">Zwykle jest to wykonywane w katalogu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6f529-140">You typically do that in your solution directory.</span></span> <span data-ttu-id="6f529-141">Dodaj następujący element do pliku **Directory. Build. props** w katalogu rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="6f529-141">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="6f529-142">Teraz kompilacje w każdym podkatalogu katalogu zawierającego ten plik będą korzystać z wersji zapoznawczej C# .</span><span class="sxs-lookup"><span data-stu-id="6f529-142">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="6f529-143">Aby uzyskać więcej informacji, zobacz artykuł na temat [dostosowywania kompilacji](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="6f529-143">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="6f529-144">C#dokumentacja wersji języka</span><span class="sxs-lookup"><span data-stu-id="6f529-144">C# language version reference</span></span>

<span data-ttu-id="6f529-145">W poniższej tabeli przedstawiono wszystkie bieżące C# wersje językowe.</span><span class="sxs-lookup"><span data-stu-id="6f529-145">The following table shows all current C# language versions.</span></span> <span data-ttu-id="6f529-146">Kompilator może niekoniecznie zrozumieć każdą wartość, jeśli jest starszy.</span><span class="sxs-lookup"><span data-stu-id="6f529-146">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="6f529-147">Jeśli zainstalujesz program .NET Core 3,0, będziesz mieć dostęp do wszystkich elementów na liście.</span><span class="sxs-lookup"><span data-stu-id="6f529-147">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="6f529-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="6f529-148">Value</span></span>|<span data-ttu-id="6f529-149">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="6f529-149">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="6f529-150">wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="6f529-150">preview</span></span>|<span data-ttu-id="6f529-151">Kompilator akceptuje całą poprawną składnię języka od najnowszej wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="6f529-151">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="6f529-152">najnowsza</span><span class="sxs-lookup"><span data-stu-id="6f529-152">latest</span></span>|<span data-ttu-id="6f529-153">Kompilator akceptuje składnię z najnowszej wydanej wersji kompilatora (w tym wersji pomocniczej).</span><span class="sxs-lookup"><span data-stu-id="6f529-153">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="6f529-154">latestMajor</span><span class="sxs-lookup"><span data-stu-id="6f529-154">latestMajor</span></span>|<span data-ttu-id="6f529-155">Kompilator akceptuje składnię z najnowszej wydanej wersji głównej kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6f529-155">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="6f529-156">8.0</span><span class="sxs-lookup"><span data-stu-id="6f529-156">8.0</span></span>|<span data-ttu-id="6f529-157">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 8,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="6f529-157">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="6f529-158">7.3</span><span class="sxs-lookup"><span data-stu-id="6f529-158">7.3</span></span>|<span data-ttu-id="6f529-159">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,3 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="6f529-159">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="6f529-160">7.2</span><span class="sxs-lookup"><span data-stu-id="6f529-160">7.2</span></span>|<span data-ttu-id="6f529-161">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,2 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="6f529-161">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="6f529-162">7.1</span><span class="sxs-lookup"><span data-stu-id="6f529-162">7.1</span></span>|<span data-ttu-id="6f529-163">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,1 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="6f529-163">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="6f529-164">7</span><span class="sxs-lookup"><span data-stu-id="6f529-164">7</span></span>|<span data-ttu-id="6f529-165">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="6f529-165">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="6f529-166">6</span><span class="sxs-lookup"><span data-stu-id="6f529-166">6</span></span>|<span data-ttu-id="6f529-167">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 6,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="6f529-167">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="6f529-168">5</span><span class="sxs-lookup"><span data-stu-id="6f529-168">5</span></span>|<span data-ttu-id="6f529-169">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 5,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="6f529-169">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="6f529-170">4</span><span class="sxs-lookup"><span data-stu-id="6f529-170">4</span></span>|<span data-ttu-id="6f529-171">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 4,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="6f529-171">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="6f529-172">3</span><span class="sxs-lookup"><span data-stu-id="6f529-172">3</span></span>|<span data-ttu-id="6f529-173">Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 3,0 lub niższej.</span><span class="sxs-lookup"><span data-stu-id="6f529-173">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="6f529-174">ISO-2</span><span class="sxs-lookup"><span data-stu-id="6f529-174">ISO-2</span></span>|<span data-ttu-id="6f529-175">Kompilator akceptuje tylko składnię zawartą w ISO/IEC 23270:2006 C# (2,0)</span><span class="sxs-lookup"><span data-stu-id="6f529-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="6f529-176">ISO-1</span><span class="sxs-lookup"><span data-stu-id="6f529-176">ISO-1</span></span>|<span data-ttu-id="6f529-177">Kompilator akceptuje tylko składnię zawartą w ISO/IEC 23270:2003 C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="6f529-177">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
