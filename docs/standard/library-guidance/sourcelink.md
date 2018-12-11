---
title: Biblioteki SourceLink i platformy .NET
description: Najlepszym rozwiązaniem, zalecenia dotyczące używania SourceLink w celu debugowania bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 3bc72e158a5773b656095f9ce58b442469f91e67
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128933"
---
# <a name="sourcelink"></a><span data-ttu-id="0395f-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="0395f-103">SourceLink</span></span>

<span data-ttu-id="0395f-104">SourceLink to technologia, która umożliwia debugowanie kodu źródłowego .NET zestawów z pakietu NuGet przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="0395f-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="0395f-105">SourceLink jest wykonywany podczas tworzenia pakietu NuGet i osadza metadanych kontroli źródła wewnątrz zespołów i pakietu.</span><span class="sxs-lookup"><span data-stu-id="0395f-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="0395f-106">Deweloperzy, którzy pobrać pakiet oraz mieć włączone w programie Visual Studio SourceLink wejść do jego kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="0395f-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="0395f-107">SourceLink udostępnia metadane kontroli źródła do utworzenia doskonałe środowisko debugowania.</span><span class="sxs-lookup"><span data-stu-id="0395f-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="0395f-108">Pokaz SourceLink</span><span class="sxs-lookup"><span data-stu-id="0395f-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="0395f-109">Za pomocą SourceLink</span><span class="sxs-lookup"><span data-stu-id="0395f-109">Using SourceLink</span></span>

<span data-ttu-id="0395f-110">Instrukcje dotyczące korzystania z SourceLink znajduje się na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="0395f-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="0395f-111">Możesz użyć [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby upewnić się, że metadane SourceLink zostały pomyślnie osadzonego w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="0395f-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="0395f-112">Sprawdź `Repository` metadanych znajduje się za pomocą identyfikatora komentarz, a pliki .pdb znajdują się za pomocą .dll w każdym obiekcie docelowym.</span><span class="sxs-lookup"><span data-stu-id="0395f-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="0395f-113">![SourceLink w Eksploratorze pakietu NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink w Eksploratorze pakietu NuGet")</span><span class="sxs-lookup"><span data-stu-id="0395f-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="0395f-114">**ROZWAŻ ✔️** używanie SourceLink do dodawania metadanych do kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="0395f-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="0395f-115">Przez dodanie atrybutów debugera do typów, może dodatkowo ulepszyć środowisko debugowania dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="0395f-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="0395f-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> można dostosować, jak klasa lub pole jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="0395f-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="0395f-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> Nakazuje debugerowi, aby przejść przez kod zamiast Przechodzenie do kodu.</span><span class="sxs-lookup"><span data-stu-id="0395f-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="0395f-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Określa, czy członek jest wyświetlana w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="0395f-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="0395f-119">**ROZWAŻ ✔️** w tym pliki symboli (`*.pdb`) w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="0395f-119">**✔️ CONSIDER** including symbol files (`*.pdb`) in the NuGet package.</span></span>

> <span data-ttu-id="0395f-120">Zazwyczaj chcesz opublikować pliki symboli w [pakiet symboli](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="0395f-120">Ordinarily, you'd publish symbol files in a [symbol package](./nuget.md#symbol-packages).</span></span> <span data-ttu-id="0395f-121">Obecnie głównym gospodarzem publicznych pakietów symboli nie obsługuje plików przenośnych symboli (`*.pdb`) utworzone przez projektów w stylu zestawu SDK i pakiety symboli nie są użyteczne.</span><span class="sxs-lookup"><span data-stu-id="0395f-121">Currently the main public host for symbol packages doesn't support the portable symbol files (`*.pdb`) created by SDK-style projects, and symbol packages aren't useful.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0395f-122">[Poprzednie](dependencies.md)
>[dalej](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="0395f-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>