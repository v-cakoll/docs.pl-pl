---
title: Link źródłowy i biblioteki .NET
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących używania linku źródłowego w celu usprawnienia debugowania bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 7530c984ce4bbe9e40362bd550bec57ac585a550
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928990"
---
# <a name="source-link"></a><span data-ttu-id="0612c-103">Link do źródła</span><span class="sxs-lookup"><span data-stu-id="0612c-103">Source Link</span></span>

<span data-ttu-id="0612c-104">Link źródłowy to technologia, która umożliwia debugowanie kodu źródłowego zestawów .NET z narzędzia NuGet przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="0612c-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="0612c-105">Łącze źródłowe jest wykonywane podczas tworzenia pakietu NuGet i osadza metadane kontroli źródła wewnątrz zestawów i pakietu.</span><span class="sxs-lookup"><span data-stu-id="0612c-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="0612c-106">Deweloperzy, którzy pobierają pakiet i łącze do źródła włączone w programie Visual Studio, mogą przejść do jego kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0612c-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="0612c-107">Link źródłowy udostępnia metadane kontroli źródła w celu utworzenia doskonałego środowiska debugowania.</span><span class="sxs-lookup"><span data-stu-id="0612c-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="0612c-108">Pokaz linku źródłowego</span><span class="sxs-lookup"><span data-stu-id="0612c-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="0612c-109">Używanie linku źródłowego</span><span class="sxs-lookup"><span data-stu-id="0612c-109">Using Source Link</span></span>

<span data-ttu-id="0612c-110">Instrukcje dotyczące korzystania z linku źródłowego znajdują się w repozytorium [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="0612c-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="0612c-111">Możesz użyć [Eksploratora pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) , aby potwierdzić, że metadane linku źródłowego zostały pomyślnie osadzone w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="0612c-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="0612c-112">Sprawdź, `Repository` czy metadane są dostępne z identyfikatorem komentarza i czy pliki. pdb znajdują się w pliku. dll każdego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0612c-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="0612c-113">![Link źródłowy w Eksploratorze pakietów NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Link źródłowy w Eksploratorze pakietów NuGet")</span><span class="sxs-lookup"><span data-stu-id="0612c-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="0612c-114">**✔️ rozważyć** użycie linku źródłowego w celu dodania metadanych kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="0612c-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="0612c-115">Możesz bardziej usprawnić środowisko debugowania dewelopera, dodając do swoich typów atrybuty debugera.</span><span class="sxs-lookup"><span data-stu-id="0612c-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="0612c-116"><xref:System.Diagnostics.DebuggerDisplayAttribute>można dostosować sposób wyświetlania klasy lub pola w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="0612c-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="0612c-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute>nakazuje debugerowi przechodzenie przez kod, a nie krokowe przechodzenie do kodu.</span><span class="sxs-lookup"><span data-stu-id="0612c-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="0612c-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute>Określa, czy element członkowski jest wyświetlany w oknach zmiennych debugera.</span><span class="sxs-lookup"><span data-stu-id="0612c-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="0612c-119">**✔️ Rozważ** opublikowanie plików symboli`*.pdb`().</span><span class="sxs-lookup"><span data-stu-id="0612c-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="0612c-120">W celu uzyskania najlepszego środowiska debugowania biblioteka powinna publikować pliki symboli, a także używać linku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0612c-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="0612c-121">Aby uzyskać więcej informacji na temat plików symboli i pakietów symboli, zobacz [pakiety symboli](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="0612c-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0612c-122">[Poprzedni](dependencies.md)Następny
>[](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="0612c-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
