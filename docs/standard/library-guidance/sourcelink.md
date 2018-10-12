---
title: Biblioteki SourceLink i platformy .NET
description: Najlepszym rozwiązaniem, zalecenia dotyczące używania SourceLink w celu debugowania bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123875"
---
# <a name="sourcelink"></a><span data-ttu-id="60c4c-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="60c4c-103">SourceLink</span></span>

<span data-ttu-id="60c4c-104">SourceLink to technologia, która umożliwia debugowanie kodu źródłowego .NET zestawów z pakietu NuGet przez deweloperów.</span><span class="sxs-lookup"><span data-stu-id="60c4c-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="60c4c-105">SourceLink jest wykonywany podczas tworzenia pakietu NuGet i osadza metadanych kontroli źródła wewnątrz zespołów i pakietu.</span><span class="sxs-lookup"><span data-stu-id="60c4c-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="60c4c-106">Deweloperzy, którzy pobrać pakiet oraz mieć włączone w programie Visual Studio SourceLink wejść do jego kod źródłowy.</span><span class="sxs-lookup"><span data-stu-id="60c4c-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="60c4c-107">SourceLink udostępnia metadane kontroli źródła do utworzenia doskonałe środowisko debugowania.</span><span class="sxs-lookup"><span data-stu-id="60c4c-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="60c4c-108">Pokaz SourceLink</span><span class="sxs-lookup"><span data-stu-id="60c4c-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="60c4c-109">Za pomocą SourceLink</span><span class="sxs-lookup"><span data-stu-id="60c4c-109">Using SourceLink</span></span>

<span data-ttu-id="60c4c-110">Instrukcje dotyczące korzystania z SourceLink znajduje się na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="60c4c-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="60c4c-111">Możesz użyć [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aby upewnić się, że metadane SourceLink zostały pomyślnie osadzonego w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="60c4c-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="60c4c-112">Sprawdź `Repository` metadanych znajduje się za pomocą identyfikatora komentarz, a pliki .pdb znajdują się za pomocą .dll w każdym obiekcie docelowym.</span><span class="sxs-lookup"><span data-stu-id="60c4c-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="60c4c-113">![SourceLink w Eksploratorze pakietu NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink w Eksploratorze pakietu NuGet")</span><span class="sxs-lookup"><span data-stu-id="60c4c-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="60c4c-114">**ROZWAŻ ✔️** używanie SourceLink do dodawania metadanych kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="60c4c-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

<span data-ttu-id="60c4c-115">**ROZWAŻ ✔️** w tym pliki PDB w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="60c4c-115">**✔️ CONSIDER** including PDB files in the NuGet package.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="60c4c-116">[Poprzednie](./dependencies.md)
[dalej](./publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="60c4c-116">[Previous](./dependencies.md)
[Next](./publish-nuget-package.md)</span></span>
