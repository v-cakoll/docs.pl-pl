---
title: Wybierz wersję języka Visual Basic
description: Skonfiguruj kompilatora przeprowadzić weryfikacji składni przy użyciu określonej wersji kompilatora.
ms.date: 05/24/2018
ms.openlocfilehash: 3b6d8055dbf64f2a5c38f46b6d66794fc48a1cea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797036"
---
# <a name="select-the-visual-basic-language-version"></a><span data-ttu-id="c3136-103">Wybierz wersję języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3136-103">Select the Visual Basic language version</span></span>

<span data-ttu-id="c3136-104">Domyślnie kompilator Visual Basic do najnowszej wersji głównej języka, która została zwolniona.</span><span class="sxs-lookup"><span data-stu-id="c3136-104">The Visual Basic compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="c3136-105">Można skompilować jakiegokolwiek projektu, przy użyciu nowej wersji punktu języka.</span><span class="sxs-lookup"><span data-stu-id="c3136-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="c3136-106">Wybieranie nowszą wersję języka umożliwia projekt tak, aby korzystać z najnowszych funkcji języków.</span><span class="sxs-lookup"><span data-stu-id="c3136-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="c3136-107">W innych sytuacjach może być konieczne sprawdzenie, czy projekt skompilowany bez błędów, gdy używasz starszej wersji języka.</span><span class="sxs-lookup"><span data-stu-id="c3136-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="c3136-108">Ta funkcja oddziela decyzję, aby zainstalować nowe wersje zestawu SDK i narzędzi w środowisku programistycznym z decyzji, aby wprowadzić nowe funkcje języka w projekcie.</span><span class="sxs-lookup"><span data-stu-id="c3136-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="c3136-109">Na komputerze kompilacji, można zainstalować najnowszy zestaw SDK oraz narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c3136-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="c3136-110">Każdy projekt można skonfigurować do użytku z określoną wersją języka jego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c3136-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="c3136-111">Istnieją trzy sposoby ustawiania wersji języka:</span><span class="sxs-lookup"><span data-stu-id="c3136-111">There are three ways to set the language version:</span></span>

- <span data-ttu-id="c3136-112">Ręcznie Edytuj swoje [ **.vbproj** pliku](#edit-the-vbproj-file)</span><span class="sxs-lookup"><span data-stu-id="c3136-112">Manually edit your [**.vbproj** file](#edit-the-vbproj-file)</span></span>
- <span data-ttu-id="c3136-113">Ustawianie wersji języka [dla wielu projektów w podkatalogu](#configure-multiple-projects)</span><span class="sxs-lookup"><span data-stu-id="c3136-113">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects)</span></span>
- <span data-ttu-id="c3136-114">Konfigurowanie [ `-langversion` — opcja kompilatora](#set-the-langversion-compiler-option)</span><span class="sxs-lookup"><span data-stu-id="c3136-114">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option)</span></span>

## <a name="edit-the-vbproj-file"></a><span data-ttu-id="c3136-115">Edytowanie pliku vbproj</span><span class="sxs-lookup"><span data-stu-id="c3136-115">Edit the vbproj file</span></span>

<span data-ttu-id="c3136-116">Wersja językowa można ustawić w swojej **.vbproj** pliku.</span><span class="sxs-lookup"><span data-stu-id="c3136-116">You can set the language version in your **.vbproj** file.</span></span> <span data-ttu-id="c3136-117">Dodaj następujący element:</span><span class="sxs-lookup"><span data-stu-id="c3136-117">Add the following element:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="c3136-118">Wartość `latest` korzysta z najnowszej wersji pomocniczej języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3136-118">The value `latest` uses the latest minor version of the Visual Basic language.</span></span> <span data-ttu-id="c3136-119">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="c3136-119">Valid values are:</span></span>

|<span data-ttu-id="c3136-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="c3136-120">Value</span></span>|<span data-ttu-id="c3136-121">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="c3136-121">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="c3136-122">default</span><span class="sxs-lookup"><span data-stu-id="c3136-122">default</span></span>|<span data-ttu-id="c3136-123">Kompilator akceptuje wszystkie składni języka prawidłowy z najnowszej wersji głównej, która może obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="c3136-123">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="c3136-124">9</span><span class="sxs-lookup"><span data-stu-id="c3136-124">9</span></span>|<span data-ttu-id="c3136-125">Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku Visual Basic 9.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="c3136-125">The compiler accepts only syntax that is included in Visual Basic 9.0 or lower.</span></span>|
|<span data-ttu-id="c3136-126">10</span><span class="sxs-lookup"><span data-stu-id="c3136-126">10</span></span>|<span data-ttu-id="c3136-127">Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku Visual Basic 10.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="c3136-127">The compiler accepts only syntax that is included in Visual Basic 10.0 or lower.</span></span>|
|<span data-ttu-id="c3136-128">11</span><span class="sxs-lookup"><span data-stu-id="c3136-128">11</span></span>|<span data-ttu-id="c3136-129">Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku Visual Basic 11.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="c3136-129">The compiler accepts only syntax that is included in Visual Basic 11.0 or lower.</span></span>|
|<span data-ttu-id="c3136-130">12</span><span class="sxs-lookup"><span data-stu-id="c3136-130">12</span></span>|<span data-ttu-id="c3136-131">Kompilator akceptuje tylko w przypadku składni, która jest zawarty w Visual Basic 12.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="c3136-131">The compiler accepts only syntax that is included in Visual Basic 12.0 or lower.</span></span>|
|<span data-ttu-id="c3136-132">14</span><span class="sxs-lookup"><span data-stu-id="c3136-132">14</span></span>|<span data-ttu-id="c3136-133">Kompilator akceptuje tylko w przypadku składni, która jest zawarty w języku Visual Basic 14.0 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="c3136-133">The compiler accepts only syntax that is included in Visual Basic 14.0 or lower.</span></span>|
|<span data-ttu-id="c3136-134">15</span><span class="sxs-lookup"><span data-stu-id="c3136-134">15</span></span>|<span data-ttu-id="c3136-135">Kompilator akceptuje tylko w przypadku składni, która jest dostępne w ramach 15.0 programu Visual Basic lub niższą.</span><span class="sxs-lookup"><span data-stu-id="c3136-135">The compiler accepts only syntax that is included in Visual Basic 15.0 or lower.</span></span>|
|<span data-ttu-id="c3136-136">15.3</span><span class="sxs-lookup"><span data-stu-id="c3136-136">15.3</span></span>|<span data-ttu-id="c3136-137">Kompilator akceptuje tylko w przypadku składni, która jest zawarty w Visual Basic 15.3 lub niższą.</span><span class="sxs-lookup"><span data-stu-id="c3136-137">The compiler accepts only syntax that is included in Visual Basic 15.3 or lower.</span></span>|
|<span data-ttu-id="c3136-138">15.5</span><span class="sxs-lookup"><span data-stu-id="c3136-138">15.5</span></span>|<span data-ttu-id="c3136-139">Kompilator akceptuje tylko w przypadku składni, która jest dostępna w wersji 15.5 programu Visual Basic lub niższy.</span><span class="sxs-lookup"><span data-stu-id="c3136-139">The compiler accepts only syntax that is included in Visual Basic 15.5 or lower.</span></span>|
|<span data-ttu-id="c3136-140">najnowsza</span><span class="sxs-lookup"><span data-stu-id="c3136-140">latest</span></span>|<span data-ttu-id="c3136-141">Kompilator akceptuje wszystkie składni obowiązujący język, który może obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="c3136-141">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="c3136-142">Ciągi specjalne `default` i `latest` rozwiązania do najnowszej wersji głównych i pomocniczych język zainstalowany na komputerze kompilacji, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c3136-142">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="c3136-143">Konfigurowanie wielu projektów</span><span class="sxs-lookup"><span data-stu-id="c3136-143">Configure multiple projects</span></span>

<span data-ttu-id="c3136-144">Możesz utworzyć **Directory.build.props** pliku, który zawiera `<LangVersion>` element, aby skonfigurować wiele katalogów.</span><span class="sxs-lookup"><span data-stu-id="c3136-144">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="c3136-145">Należy zwykle to zrobić w katalogu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c3136-145">You typically do that in your solution directory.</span></span> <span data-ttu-id="c3136-146">Dodaj następujące polecenie, aby **Directory.build.props** pliku w katalogu rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="c3136-146">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="c3136-147">Teraz kompilacje w każdym podkatalogu katalogu zawierającego ten plik będzie używać składni w wersji 15.5 programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3136-147">Now, builds in every subdirectory of the directory containing that file will use Visual Basic version 15.5 syntax.</span></span> <span data-ttu-id="c3136-148">Aby uzyskać więcej informacji, zobacz artykuł [Dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="c3136-148">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="c3136-149">Ustaw langversion — opcja kompilatora</span><span class="sxs-lookup"><span data-stu-id="c3136-149">Set the langversion compiler option</span></span>

<span data-ttu-id="c3136-150">Możesz użyć `-langversion` opcji wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c3136-150">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="c3136-151">Aby uzyskać więcej informacji, zobacz artykuł [- langversion](../reference/command-line-compiler/langversion.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c3136-151">For more information, see the article on the [-langversion](../reference/command-line-compiler/langversion.md) compiler option.</span></span> <span data-ttu-id="c3136-152">Możesz wyświetlić listę prawidłowych wartości, wpisując `vbc -langversion:?` .</span><span class="sxs-lookup"><span data-stu-id="c3136-152">You can see a list of the valid values by typing  `vbc -langversion:?` .</span></span>
