---
title: Biblioteki SourceLink i platformy .NET
description: Najlepszym rozwiązaniem, zalecenia dotyczące używania SourceLink w celu debugowania bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: be97f868e2fcfc6c45e4bbac45b033f8914f4d99
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333541"
---
# <a name="sourcelink"></a><span data-ttu-id="b87d9-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="b87d9-103">SourceLink</span></span>

<span data-ttu-id="b87d9-104">SourceLink to technologia, która umożliwia debugowanie kodu źródłowego .NET zestawów z pakietu NuGet przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="b87d9-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="b87d9-105">SourceLink jest wykonywany podczas tworzenia pakietu NuGet i osadza metadanych kontroli źródła wewnątrz zespołów i pakietu.</span><span class="sxs-lookup"><span data-stu-id="b87d9-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="b87d9-106">Deweloperzy, którzy pobrać pakiet oraz mieć włączone w programie Visual Studio SourceLink wejść do jego kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="b87d9-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="b87d9-107">SourceLink udostępnia metadane kontroli źródła do utworzenia doskonałe środowisko debugowania.</span><span class="sxs-lookup"><span data-stu-id="b87d9-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="b87d9-108">SourceLink demo</span><span class="sxs-lookup"><span data-stu-id="b87d9-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="b87d9-109">Za pomocą SourceLink</span><span class="sxs-lookup"><span data-stu-id="b87d9-109">Using SourceLink</span></span>

<span data-ttu-id="b87d9-110">Instrukcje dotyczące korzystania z SourceLink znajduje się na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="b87d9-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="b87d9-111">Możesz użyć [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby upewnić się, że metadane SourceLink zostały pomyślnie osadzonego w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="b87d9-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="b87d9-112">Sprawdź `Repository` metadanych znajduje się za pomocą identyfikatora komentarz, a pliki .pdb znajdują się za pomocą .dll w każdym obiekcie docelowym.</span><span class="sxs-lookup"><span data-stu-id="b87d9-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="b87d9-113">![SourceLink w Eksploratorze pakietu NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink w Eksploratorze pakietu NuGet")</span><span class="sxs-lookup"><span data-stu-id="b87d9-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="b87d9-114">**ROZWAŻ ✔️** używanie SourceLink do dodawania metadanych do kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="b87d9-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="b87d9-115">Przez dodanie atrybutów debugera do typów, może dodatkowo ulepszyć środowisko debugowania dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="b87d9-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="b87d9-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> można dostosować, jak klasa lub pole jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="b87d9-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="b87d9-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> Nakazuje debugerowi, aby przejść przez kod zamiast Przechodzenie do kodu.</span><span class="sxs-lookup"><span data-stu-id="b87d9-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="b87d9-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Określa, czy członek jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="b87d9-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="b87d9-119">**ROZWAŻ ✔️** publikowania plików symboli (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="b87d9-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="b87d9-120">Aby uzyskać więcej informacji na temat plików symboli i pakiety symboli, zobacz [symboli pakietów](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="b87d9-120">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b87d9-121">[Poprzednie](dependencies.md)
>[dalej](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="b87d9-121">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
