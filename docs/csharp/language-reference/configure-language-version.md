---
title: C#przechowywanie wersji języka — C# przewodnik
description: Dowiedz się więcej o tym, jak C# wersja językowa jest określana na podstawie projektu i różne wartości możesz ręcznie dostosować go do.
ms.date: 07/10/2019
ms.openlocfilehash: e35fdf2bcdb1a31b752c760f3f6df59232e498a4
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236093"
---
# <a name="c-language-versioning"></a><span data-ttu-id="4995d-103">C#przechowywanie wersji języka</span><span class="sxs-lookup"><span data-stu-id="4995d-103">C# language versioning</span></span>

<span data-ttu-id="4995d-104">C# Kompilator określa domyślną wersję języka na podstawie platformy docelowej projektu lub struktury.</span><span class="sxs-lookup"><span data-stu-id="4995d-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="4995d-105">Jest to spowodowane C# język może mieć funkcje, które zależą od typów lub składniki środowiska uruchomieniowego, które nie są dostępne w każdej implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="4995d-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="4995d-106">Dzięki temu, niezależnie od docelowego, projekt został skompilowany przed uzyskasz najwyższa wersja zgodna język domyślny.</span><span class="sxs-lookup"><span data-stu-id="4995d-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

## <a name="defaults"></a><span data-ttu-id="4995d-107">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4995d-107">Defaults</span></span>

<span data-ttu-id="4995d-108">Kompilator Określa domyślny na podstawie tych reguł:</span><span class="sxs-lookup"><span data-stu-id="4995d-108">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="4995d-109">Platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="4995d-109">Target framework</span></span>|<span data-ttu-id="4995d-110">version</span><span class="sxs-lookup"><span data-stu-id="4995d-110">version</span></span>|<span data-ttu-id="4995d-111">C#Domyślna wersja języka</span><span class="sxs-lookup"><span data-stu-id="4995d-111">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="4995d-112">.NET Core</span><span class="sxs-lookup"><span data-stu-id="4995d-112">.NET Core</span></span>|<span data-ttu-id="4995d-113">3.x</span><span class="sxs-lookup"><span data-stu-id="4995d-113">3.x</span></span>|<span data-ttu-id="4995d-114">C#8.0</span><span class="sxs-lookup"><span data-stu-id="4995d-114">C# 8.0</span></span>|
|<span data-ttu-id="4995d-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="4995d-115">.NET Core</span></span>|<span data-ttu-id="4995d-116">2.x</span><span class="sxs-lookup"><span data-stu-id="4995d-116">2.x</span></span>|<span data-ttu-id="4995d-117">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="4995d-117">C# 7.3</span></span>|
|<span data-ttu-id="4995d-118">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="4995d-118">.NET Standard</span></span>|<span data-ttu-id="4995d-119">wszystkie</span><span class="sxs-lookup"><span data-stu-id="4995d-119">all</span></span>|<span data-ttu-id="4995d-120">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="4995d-120">C# 7.3</span></span>|
|<span data-ttu-id="4995d-121">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="4995d-121">.NET Framework</span></span>|<span data-ttu-id="4995d-122">wszystkie</span><span class="sxs-lookup"><span data-stu-id="4995d-122">all</span></span>|<span data-ttu-id="4995d-123">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="4995d-123">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="4995d-124">Domyślne dla wersji zapoznawczych</span><span class="sxs-lookup"><span data-stu-id="4995d-124">Default for previews</span></span>

<span data-ttu-id="4995d-125">Jeśli projekt jest przeznaczony dla framework w wersji zapoznawczej, która jest odpowiednia wersja językowa (wersja zapoznawcza), wersja językowa, używana jest wersja językowa (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="4995d-125">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="4995d-126">Gwarantuje to, czy można użyć najnowsze funkcje, które mogą pracować w dowolnym środowisku w tej wersji zapoznawczej bez wywierania wpływu na swoje projekty przeznaczone wydanej wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4995d-126">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="overriding-a-default"></a><span data-ttu-id="4995d-127">Zastępowanie domyślnego</span><span class="sxs-lookup"><span data-stu-id="4995d-127">Overriding a default</span></span>

<span data-ttu-id="4995d-128">Jeśli trzeba określić swoje C# wersji jawnie, możesz to zrobić na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="4995d-128">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="4995d-129">Ręcznie Edytuj swoje [pliku projektu](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="4995d-129">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="4995d-130">Ustawianie wersji języka [dla wielu projektów w podkatalogu](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="4995d-130">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="4995d-131">Konfigurowanie [ `-langversion` — opcja kompilatora](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="4995d-131">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="4995d-132">Edytuj plik projektu</span><span class="sxs-lookup"><span data-stu-id="4995d-132">Edit the project file</span></span>

<span data-ttu-id="4995d-133">Wersja językowa można ustawić w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="4995d-133">You can set the language version in your project file.</span></span> <span data-ttu-id="4995d-134">Na przykład jeżeli chcesz jawnie dostęp do funkcji w wersji zapoznawczej, można dodać elementu następująco:</span><span class="sxs-lookup"><span data-stu-id="4995d-134">For example, if you explicitly wanted access to preview features, you could do add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="4995d-135">Wartość `preview` najnowsza wersja zapoznawcza C# język, który kompilator obsługuje.</span><span class="sxs-lookup"><span data-stu-id="4995d-135">The value `preview` uses the latest available preview C# language that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="4995d-136">Konfigurowanie wielu projektów</span><span class="sxs-lookup"><span data-stu-id="4995d-136">Configure multiple projects</span></span>

<span data-ttu-id="4995d-137">Możesz utworzyć **Directory.Build.props** pliku, który zawiera `<LangVersion>` element, aby skonfigurować wiele katalogów.</span><span class="sxs-lookup"><span data-stu-id="4995d-137">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="4995d-138">Należy zwykle to zrobić w katalogu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4995d-138">You typically do that in your solution directory.</span></span> <span data-ttu-id="4995d-139">Dodaj następujące polecenie, aby **Directory.Build.props** pliku w katalogu rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="4995d-139">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="4995d-140">Teraz kompilacje w każdym podkatalogu katalogu zawierającego ten plik będzie używać wersji zapoznawczej C# wersji.</span><span class="sxs-lookup"><span data-stu-id="4995d-140">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="4995d-141">Aby uzyskać więcej informacji, zobacz artykuł [Dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="4995d-141">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="4995d-142">C#Dokumentacja wersji języka</span><span class="sxs-lookup"><span data-stu-id="4995d-142">C# language version reference</span></span>

<span data-ttu-id="4995d-143">W poniższej tabeli przedstawiono wszystkie bieżące C# wersji językowych.</span><span class="sxs-lookup"><span data-stu-id="4995d-143">The following table shows all current C# language versions.</span></span> <span data-ttu-id="4995d-144">Kompilator nie może zawsze zrozumieć każda wartość, jeżeli jest starszy.</span><span class="sxs-lookup"><span data-stu-id="4995d-144">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="4995d-145">Po zainstalowaniu programu .NET Core 3.0, będą mieć dostęp do wszystkiego, na liście.</span><span class="sxs-lookup"><span data-stu-id="4995d-145">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="4995d-146">Wartość</span><span class="sxs-lookup"><span data-stu-id="4995d-146">Value</span></span>|<span data-ttu-id="4995d-147">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="4995d-147">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="4995d-148">wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="4995d-148">preview</span></span>|<span data-ttu-id="4995d-149">Kompilator akceptuje wszystkie składni języka prawidłowy z najnowszej wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="4995d-149">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="4995d-150">najnowsza</span><span class="sxs-lookup"><span data-stu-id="4995d-150">latest</span></span>|<span data-ttu-id="4995d-151">Kompilator akceptuje składni z najnowszej wersji, kompilator (w tym wersja pomocnicza).</span><span class="sxs-lookup"><span data-stu-id="4995d-151">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="4995d-152">latestMajor</span><span class="sxs-lookup"><span data-stu-id="4995d-152">latestMajor</span></span>|<span data-ttu-id="4995d-153">Kompilator akceptuje składnię najnowszej głównej wersji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="4995d-153">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="4995d-154">8.0</span><span class="sxs-lookup"><span data-stu-id="4995d-154">8.0</span></span>|<span data-ttu-id="4995d-155">Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 8.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="4995d-155">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="4995d-156">7.3</span><span class="sxs-lookup"><span data-stu-id="4995d-156">7.3</span></span>|<span data-ttu-id="4995d-157">Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.3 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="4995d-157">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="4995d-158">7.2</span><span class="sxs-lookup"><span data-stu-id="4995d-158">7.2</span></span>|<span data-ttu-id="4995d-159">Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.2 lub niższy.</span><span class="sxs-lookup"><span data-stu-id="4995d-159">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="4995d-160">7.1</span><span class="sxs-lookup"><span data-stu-id="4995d-160">7.1</span></span>|<span data-ttu-id="4995d-161">Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.1 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="4995d-161">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="4995d-162">7</span><span class="sxs-lookup"><span data-stu-id="4995d-162">7</span></span>|<span data-ttu-id="4995d-163">Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="4995d-163">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="4995d-164">6</span><span class="sxs-lookup"><span data-stu-id="4995d-164">6</span></span>|<span data-ttu-id="4995d-165">Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 6.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="4995d-165">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="4995d-166">5</span><span class="sxs-lookup"><span data-stu-id="4995d-166">5</span></span>|<span data-ttu-id="4995d-167">Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 5.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="4995d-167">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="4995d-168">4</span><span class="sxs-lookup"><span data-stu-id="4995d-168">4</span></span>|<span data-ttu-id="4995d-169">Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 4.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="4995d-169">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="4995d-170">3</span><span class="sxs-lookup"><span data-stu-id="4995d-170">3</span></span>|<span data-ttu-id="4995d-171">Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 3.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="4995d-171">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="4995d-172">ISO-2</span><span class="sxs-lookup"><span data-stu-id="4995d-172">ISO-2</span></span>|<span data-ttu-id="4995d-173">Kompilator akceptuje tylko w przypadku składni, która znajduje się w 23270:2006 ISO/IEC C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="4995d-173">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="4995d-174">ISO-1</span><span class="sxs-lookup"><span data-stu-id="4995d-174">ISO-1</span></span>|<span data-ttu-id="4995d-175">Kompilator akceptuje tylko w przypadku składni, która znajduje się w 23270:2003 ISO/IEC C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="4995d-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
