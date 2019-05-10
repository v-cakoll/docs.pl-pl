---
title: Biblioteki Linku źródłowego i platformy .NET
description: Zalecane najlepsze w celu debugowania bibliotek platformy .NET przy użyciu Linku źródłowego.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 9d3e2b0b3aedbab150072bf6eebff4acb5f8a0b7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211674"
---
# <a name="source-link"></a><span data-ttu-id="c805c-103">Link do źródła</span><span class="sxs-lookup"><span data-stu-id="c805c-103">Source Link</span></span>

<span data-ttu-id="c805c-104">Link źródłowy jest to technologia, która umożliwia debugowanie kodu źródłowego .NET zestawów z pakietu NuGet przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="c805c-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="c805c-105">Link źródłowy jest wykonywany podczas tworzenia pakietu NuGet i osadza metadanych kontroli źródła wewnątrz zespołów i pakietu.</span><span class="sxs-lookup"><span data-stu-id="c805c-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="c805c-106">Deweloperzy, którzy pobrać pakiet oraz mieć Linku źródłowego włączone w programie Visual Studio można wkroczyć do jego kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="c805c-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="c805c-107">Link źródłowy udostępnia metadane kontroli źródła do utworzenia doskonałe środowisko debugowania.</span><span class="sxs-lookup"><span data-stu-id="c805c-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="c805c-108">Pokaz Linku źródłowego</span><span class="sxs-lookup"><span data-stu-id="c805c-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="c805c-109">Przy użyciu Linku źródłowego</span><span class="sxs-lookup"><span data-stu-id="c805c-109">Using Source Link</span></span>

<span data-ttu-id="c805c-110">Instrukcje dotyczące przy użyciu Linku źródłowego znajduje się na [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="c805c-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="c805c-111">Możesz użyć [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby upewnić się, że metadane Link źródłowy został pomyślnie osadzonego w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="c805c-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="c805c-112">Sprawdź `Repository` metadanych znajduje się za pomocą identyfikatora komentarz, a pliki .pdb znajdują się za pomocą .dll w każdym obiekcie docelowym.</span><span class="sxs-lookup"><span data-stu-id="c805c-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="c805c-113">![Źródło Link w Eksploratorze pakietu NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "źródła Link w Eksploratorze pakietu NuGet")</span><span class="sxs-lookup"><span data-stu-id="c805c-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="c805c-114">**ROZWAŻ ✔️** przy użyciu Linku źródłowego, aby dodać metadanych kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="c805c-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="c805c-115">Przez dodanie atrybutów debugera do typów, może dodatkowo ulepszyć środowisko debugowania dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="c805c-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="c805c-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> można dostosować, jak klasa lub pole jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="c805c-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="c805c-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> Nakazuje debugerowi, aby przejść przez kod zamiast Przechodzenie do kodu.</span><span class="sxs-lookup"><span data-stu-id="c805c-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="c805c-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Określa, czy członek jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="c805c-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="c805c-119">**ROZWAŻ ✔️** publikowania plików symboli (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="c805c-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="c805c-120">Najlepszego środowiska debugowania biblioteki należy opublikować pliki symboli oraz przy użyciu Linku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="c805c-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="c805c-121">Aby uzyskać więcej informacji na temat plików symboli i pakiety symboli, zobacz [symboli pakietów](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="c805c-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c805c-122">[Poprzednie](dependencies.md)
>[dalej](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="c805c-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
