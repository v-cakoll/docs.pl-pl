---
title: Łącze źródłowe i biblioteki .NET
description: Najlepsze zalecenia dotyczące używania łącza źródłowego w celu poprawy debugowania bibliotek .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744542"
---
# <a name="source-link"></a><span data-ttu-id="666b6-103">Link do źródła</span><span class="sxs-lookup"><span data-stu-id="666b6-103">Source Link</span></span>

<span data-ttu-id="666b6-104">Source Link to technologia, która umożliwia debugowanie kodu źródłowego zestawów .NET z NuGet przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="666b6-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="666b6-105">Łącze źródłowe jest wykonywane podczas tworzenia pakietu NuGet i osadza metadane kontroli źródła wewnątrz zestawów i pakietu.</span><span class="sxs-lookup"><span data-stu-id="666b6-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="666b6-106">Deweloperzy, którzy pobierają pakiet i mają łącze źródłowe włączone w programie Visual Studio, mogą wkroczyć do jego kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="666b6-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="666b6-107">Łącze źródłowe udostępnia metadane kontroli źródła, aby utworzyć doskonałe środowisko debugowania.</span><span class="sxs-lookup"><span data-stu-id="666b6-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="666b6-108">Wersja demonstracyjna Source Link</span><span class="sxs-lookup"><span data-stu-id="666b6-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="666b6-109">Korzystanie z łącza źródłowego</span><span class="sxs-lookup"><span data-stu-id="666b6-109">Using Source Link</span></span>

<span data-ttu-id="666b6-110">Instrukcje dotyczące korzystania z łącza źródłowego można znaleźć w repozytorium GitHub [dotnet/sourcelink.](https://github.com/dotnet/sourcelink/blob/master/README.md)</span><span class="sxs-lookup"><span data-stu-id="666b6-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="666b6-111">Można użyć [NuGet Package Explorer,](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby potwierdzić, że metadane łącza źródłowego został pomyślnie osadzony w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="666b6-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="666b6-112">Sprawdź, `Repository` czy metadane są obecne z identyfikatorem zatwierdzenia i czy pliki .pdb znajdują się z dll każdego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="666b6-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="666b6-113">![Łącze źródłowe w Eksploratorze pakietów NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Łącze źródłowe w Eksploratorze pakietów NuGet")</span><span class="sxs-lookup"><span data-stu-id="666b6-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="666b6-114">✔️ ZAPOMOCĄ łącza źródłowego, aby dodać metadane kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="666b6-114">✔️ CONSIDER using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="666b6-115">Można dodatkowo zwiększyć środowisko debugowania dewelopera, dodając atrybuty debugera do swoich typów.</span><span class="sxs-lookup"><span data-stu-id="666b6-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="666b6-116"><xref:System.Diagnostics.DebuggerDisplayAttribute>można dostosować sposób wyświetlania klasy lub pola w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="666b6-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="666b6-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute>instruuje debugera, aby krok po kroku kodu zamiast przechodzenia do kodu.</span><span class="sxs-lookup"><span data-stu-id="666b6-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="666b6-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute>określa, czy element członkowski jest wyświetlany w oknach zmiennej debugera.</span><span class="sxs-lookup"><span data-stu-id="666b6-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="666b6-119">✔️ ROZWAŻ OPUBLIKOWANIE`*.pdb`plików symboli ( ).</span><span class="sxs-lookup"><span data-stu-id="666b6-119">✔️ CONSIDER publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="666b6-120">Aby uzyskać najlepsze środowisko debugowania, biblioteka powinna publikować pliki symboli, a także używać łącza źródłowego.</span><span class="sxs-lookup"><span data-stu-id="666b6-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="666b6-121">Aby uzyskać więcej informacji na temat plików symboli i pakietów symboli, zobacz [Pakiety symboli](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="666b6-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="666b6-122">[Poprzedni](dependencies.md)
>[następny](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="666b6-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
