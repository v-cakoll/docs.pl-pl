---
title: Biblioteki Linku źródłowego i platformy .NET
description: Zalecane najlepsze w celu debugowania bibliotek platformy .NET przy użyciu Linku źródłowego.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 10596f589af7abee6ff7833ef25c606294337196
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910247"
---
# <a name="source-link"></a><span data-ttu-id="7cbc1-103">Link do źródła</span><span class="sxs-lookup"><span data-stu-id="7cbc1-103">Source Link</span></span>

<span data-ttu-id="7cbc1-104">Link źródłowy jest to technologia, która umożliwia debugowanie kodu źródłowego .NET zestawów z pakietu NuGet przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="7cbc1-105">Link źródłowy jest wykonywany podczas tworzenia pakietu NuGet i osadza metadanych kontroli źródła wewnątrz zespołów i pakietu.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="7cbc1-106">Deweloperzy, którzy pobrać pakiet oraz mieć Linku źródłowego włączone w programie Visual Studio można wkroczyć do jego kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="7cbc1-107">Link źródłowy udostępnia metadane kontroli źródła do utworzenia doskonałe środowisko debugowania.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="7cbc1-108">Pokaz Linku źródłowego</span><span class="sxs-lookup"><span data-stu-id="7cbc1-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="7cbc1-109">Przy użyciu Linku źródłowego</span><span class="sxs-lookup"><span data-stu-id="7cbc1-109">Using Source Link</span></span>

<span data-ttu-id="7cbc1-110">Instrukcje dotyczące przy użyciu Linku źródłowego znajduje się na [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="7cbc1-111">Możesz użyć [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby upewnić się, że metadane Link źródłowy został pomyślnie osadzonego w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="7cbc1-112">Sprawdź `Repository` metadanych znajduje się za pomocą identyfikatora komentarz, a pliki .pdb znajdują się za pomocą .dll w każdym obiekcie docelowym.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="7cbc1-113">![Źródło Link w Eksploratorze pakietu NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "źródła Link w Eksploratorze pakietu NuGet")</span><span class="sxs-lookup"><span data-stu-id="7cbc1-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="7cbc1-114">**ROZWAŻ ✔️** przy użyciu Linku źródłowego, aby dodać metadanych kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="7cbc1-115">Przez dodanie atrybutów debugera do typów, może dodatkowo ulepszyć środowisko debugowania dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="7cbc1-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> można dostosować, jak klasa lub pole jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="7cbc1-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> Nakazuje debugerowi, aby przejść przez kod zamiast Przechodzenie do kodu.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="7cbc1-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Określa, czy członek jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="7cbc1-119">**ROZWAŻ ✔️** publikowania plików symboli (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="7cbc1-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="7cbc1-120">Najlepszego środowiska debugowania biblioteki powinny pliki symboli pubish oraz przy użyciu Linku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="7cbc1-120">For the best debugging experience your library should pubish symbol files as well as use Source Link.</span></span> <span data-ttu-id="7cbc1-121">Aby uzyskać więcej informacji na temat plików symboli i pakiety symboli, zobacz [symboli pakietów](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="7cbc1-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7cbc1-122">[Poprzednie](dependencies.md)
>[dalej](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="7cbc1-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
