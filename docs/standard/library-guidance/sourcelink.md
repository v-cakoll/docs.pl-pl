---
title: Link źródłowy i biblioteki .NET
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących używania linku źródłowego w celu usprawnienia debugowania bibliotek platformy .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744542"
---
# <a name="source-link"></a><span data-ttu-id="d8243-103">Link do źródła</span><span class="sxs-lookup"><span data-stu-id="d8243-103">Source Link</span></span>

<span data-ttu-id="d8243-104">Link źródłowy to technologia, która umożliwia debugowanie kodu źródłowego zestawów .NET z narzędzia NuGet przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="d8243-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="d8243-105">Łącze źródłowe jest wykonywane podczas tworzenia pakietu NuGet i osadza metadane kontroli źródła wewnątrz zestawów i pakietu.</span><span class="sxs-lookup"><span data-stu-id="d8243-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="d8243-106">Deweloperzy, którzy pobierają pakiet i łącze do źródła włączone w programie Visual Studio, mogą przejść do jego kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d8243-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="d8243-107">Link źródłowy udostępnia metadane kontroli źródła w celu utworzenia doskonałego środowiska debugowania.</span><span class="sxs-lookup"><span data-stu-id="d8243-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="d8243-108">Pokaz linku źródłowego</span><span class="sxs-lookup"><span data-stu-id="d8243-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="d8243-109">Używanie linku źródłowego</span><span class="sxs-lookup"><span data-stu-id="d8243-109">Using Source Link</span></span>

<span data-ttu-id="d8243-110">Instrukcje dotyczące korzystania z linku źródłowego znajdują się w repozytorium [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="d8243-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="d8243-111">Możesz użyć [Eksploratora pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) , aby potwierdzić, że metadane linku źródłowego zostały pomyślnie osadzone w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="d8243-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="d8243-112">Sprawdź, czy metadane `Repository` są obecne w identyfikatorze zatwierdzenia i czy pliki. pdb znajdują się w pliku. dll każdego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d8243-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="d8243-113">![Link źródłowy w Eksploratorze pakietów NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Link źródłowy w Eksploratorze pakietów NuGet")</span><span class="sxs-lookup"><span data-stu-id="d8243-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="d8243-114">✔️ ROZWAŻYĆ użycie linku źródłowego w celu dodania metadanych kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="d8243-114">✔️ CONSIDER using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="d8243-115">Możesz bardziej usprawnić środowisko debugowania dewelopera, dodając do swoich typów atrybuty debugera.</span><span class="sxs-lookup"><span data-stu-id="d8243-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="d8243-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> można dostosować sposób wyświetlania klasy lub pola w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="d8243-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="d8243-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> nakazuje debugerowi przechodzenie przez kod, a nie krokowe przechodzenie do kodu.</span><span class="sxs-lookup"><span data-stu-id="d8243-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="d8243-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> kontroluje, czy element członkowski jest wyświetlany w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="d8243-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="d8243-119">✔️ Rozważ opublikowanie plików symboli (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="d8243-119">✔️ CONSIDER publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="d8243-120">W celu uzyskania najlepszego środowiska debugowania biblioteka powinna publikować pliki symboli, a także używać linku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d8243-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="d8243-121">Aby uzyskać więcej informacji na temat plików symboli i pakietów symboli, zobacz [pakiety symboli](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="d8243-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d8243-122">[Poprzedni](dependencies.md)
>[Następny](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="d8243-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
