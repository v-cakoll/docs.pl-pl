---
title: Eksportowanie do programu .NET Core z .NET Framework
description: Zrozumieć proces przenoszenia i Odkryj narzędzia, które mogą być przydatne podczas przenoszenia projektu .NET Framework i .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: d273b3abe46de59aa55b5b9a531d3c572a065124
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835395"
---
# <a name="porting-to-net-core-from-net-framework"></a><span data-ttu-id="ae015-103">Eksportowanie do programu .NET Core z .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae015-103">Porting to .NET Core from .NET Framework</span></span>

<span data-ttu-id="ae015-104">Jeśli masz kod uruchomiony w środowisku .NET Framework, może Cię zainteresować uruchamianie kodu na platformy .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="ae015-104">If you've got code running on the .NET Framework, you may be interested in running your code on .NET Core 1.0.</span></span>  <span data-ttu-id="ae015-105">W tym artykule opisano przebieg procesu przenoszenia oraz listę narzędzi, które mogą być przydatne w przypadku przenoszenia do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae015-105">This article covers an overview of the porting process and a list of the tools you may find helpful when porting to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="ae015-106">Omówienie procesu przenoszenia</span><span class="sxs-lookup"><span data-stu-id="ae015-106">Overview of the Porting Process</span></span>

<span data-ttu-id="ae015-107">Zalecany proces przenoszenia następuje poniższą sekwencję czynności.</span><span class="sxs-lookup"><span data-stu-id="ae015-107">The recommended process for porting follows the following series of steps.</span></span>  <span data-ttu-id="ae015-108">Każdy z tych elementów, proces zostały omówione bardziej szczegółowo w dalszej artykułów.</span><span class="sxs-lookup"><span data-stu-id="ae015-108">Each of these parts of the process are covered in more detail in further articles.</span></span>

1. <span data-ttu-id="ae015-109">Identyfikuj i uwzględnić zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="ae015-109">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="ae015-110">Działania te obejmują zrozumienie, jakie zależności innych firm są, jak zależeć na ich, w jaki sposób, aby sprawdzić, czy działają one również na platformy .NET Core i kroki można wykonać, jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="ae015-110">This will involve understanding what your third-party dependencies are, how you depend on them, how to see if they also run on .NET Core, and steps you can take if they don't.</span></span>
   
2. <span data-ttu-id="ae015-111">Przekieruj wszystkie projekty, które chcesz dodać port do środowiska .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="ae015-111">Retarget all projects you wish to port to target .NET Framework 4.6.2.</span></span>

   <span data-ttu-id="ae015-112">Daje to gwarancję, że można użyć interfejsu API alternatyw dla celów specyficzne dla platformy .NET Framework w przypadkach, w której platformy .NET Core nie obsługuje określony interfejs API.</span><span class="sxs-lookup"><span data-stu-id="ae015-112">This ensures that you can use API alternatives for .NET Framework-specific targets in the cases where .NET Core can't support a particular API.</span></span>
   
3. <span data-ttu-id="ae015-113">Użyj [narzędzia .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) do analizowania zestawów i opracować plan do portu, na podstawie jej wyników.</span><span class="sxs-lookup"><span data-stu-id="ae015-113">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="ae015-114">Narzędzie Analizator przenośności interfejsu API analizy skompilowanych zestawów i Generowanie raportu, który przedstawia podsumowanie wysokiego poziomu przenośność i podział każdy interfejs API używasz, nie jest dostępna na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae015-114">The API Portability Analyzer tool will analyze your compiled assemblies and generate a report which shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span>  <span data-ttu-id="ae015-115">Możesz użyć tego raportu, wraz z analizą Twojej bazy kodu, aby opracować plan dla jak Twój kod będzie portu za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="ae015-115">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>
   
4. <span data-ttu-id="ae015-116">Przyłącz kod testów.</span><span class="sxs-lookup"><span data-stu-id="ae015-116">Port your tests code.</span></span>

   <span data-ttu-id="ae015-117">Eksportowanie do programu .NET Core jest naprawdę spora zmiana bazie kodu, ma zdecydowanie zaleca uzyskać przenoszone, aby uruchomić testy zgodnie z portu kodu przez testy.</span><span class="sxs-lookup"><span data-stu-id="ae015-117">Because porting to .NET Core is such a big change to your codebase, it's highly recommended to get your tests ported so that you can run tests as you port code over.</span></span>  <span data-ttu-id="ae015-118">MSTest, xUnit i NUnit platformy .NET Core 1.0 już obsługę linuksa.</span><span class="sxs-lookup"><span data-stu-id="ae015-118">MSTest, xUnit, and NUnit all support .NET Core 1.0 today.</span></span>
   
6. <span data-ttu-id="ae015-119">Wykonaj swój plan w celu przenoszenia!</span><span class="sxs-lookup"><span data-stu-id="ae015-119">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="ae015-120">Narzędzia ułatwiające</span><span class="sxs-lookup"><span data-stu-id="ae015-120">Tools to help</span></span>

<span data-ttu-id="ae015-121">Poniżej przedstawiono krótką listę narzędzi, które będzie pomocne:</span><span class="sxs-lookup"><span data-stu-id="ae015-121">Here's a short list of the tools you'll find helpful:</span></span>

* <span data-ttu-id="ae015-122">NuGet — [klienta programu Nuget](https://dist.nuget.org/index.html) lub [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Menedżer pakietów firmy Microsoft dla implementacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ae015-122">NuGet - [Nuget Client](https://dist.nuget.org/index.html) or [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft's package manager for .NET implementations.</span></span>
* <span data-ttu-id="ae015-123">Analizator przenośności interfejsu API — [narzędzia wiersza polecenia](https://github.com/Microsoft/dotnet-apiport/releases) lub [rozszerzenie programu Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), łańcuch narzędzi, który można wygenerować raport jak przenośny kod jest między .NET Framework i .NET Core za pomocą zestaw, zestaw z rozbiciem na poszczególne problemy.</span><span class="sxs-lookup"><span data-stu-id="ae015-123">Api Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span>  <span data-ttu-id="ae015-124">Zobacz [narzędzia ułatwiające procesu](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ae015-124">See [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) for more information.</span></span>
* <span data-ttu-id="ae015-125">Odwrócone wyszukiwanie pakietu - A [usługi sieci web przydatne](https://packagesearch.azurewebsites.net) umożliwiająca wyszukiwania dla typu i znajdowania pakiety zawierające tego typu.</span><span class="sxs-lookup"><span data-stu-id="ae015-125">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ae015-126">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ae015-126">Next steps</span></span>

[<span data-ttu-id="ae015-127">Analizowanie zależności innych firm.</span><span class="sxs-lookup"><span data-stu-id="ae015-127">Analyzing your third-party dependencies.</span></span>](third-party-deps.md)
   
