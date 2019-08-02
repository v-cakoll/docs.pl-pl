---
title: Kompilowanie projektu międzyoperacyjnego
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 153df821b0dacccdcbf279bd20bfb106580f3392
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733422"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="f55e9-102">Kompilowanie projektu międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="f55e9-102">Compiling an Interop Project</span></span>

<span data-ttu-id="f55e9-103">Projekty międzyoperacyjności modelu COM, które odwołują się do co najmniej jednego zestawu zawierającego zaimportowane typy COM, są kompilowane jak każdy inny projekt zarządzany.</span><span class="sxs-lookup"><span data-stu-id="f55e9-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="f55e9-104">Można odwoływać się do zestawów międzyoperacyjnych w środowisku deweloperskim, takim jak Visual Studio, lub można się do nich odwoływać przy użyciu kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f55e9-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="f55e9-105">W obu przypadkach w celu poprawnego skompilowania zestaw międzyoperacyjny musi znajdować się w tym samym katalogu co inne pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="f55e9-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="f55e9-106">Istnieją dwa sposoby odwoływania się do zestawów międzyoperacyjnych:</span><span class="sxs-lookup"><span data-stu-id="f55e9-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="f55e9-107">Osadzone typy międzyoperacyjnych: Począwszy od .NET Framework 4 i programu Visual Studio 2010, można nakazać kompilatorowi osadzenie informacji o typie z zestawu międzyoperacyjnego do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="f55e9-107">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="f55e9-108">Jest to zalecana technika.</span><span class="sxs-lookup"><span data-stu-id="f55e9-108">This is the recommended technique.</span></span>

- <span data-ttu-id="f55e9-109">Wdrażanie zestawów międzyoperacyjnych: Można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f55e9-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="f55e9-110">W takim przypadku zestaw międzyoperacyjny musi zostać wdrożony wraz z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="f55e9-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="f55e9-111">Różnice między tymi dwoma technikami zostały omówione bardziej szczegółowo w temacie [Korzystanie z typów com w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f55e9-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="f55e9-112">Osadzanie typów międzyoperacyjnych w programie Visual Studio jest [zademonstrowane w przewodniku: Typy osadzania z zestawów zarządzanych w programie Visual StudioC#(](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)) i [wskazówki: Osadzanie typów z zestawów zarządzanych w programie Visual Studio (Visual Basic](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)).</span><span class="sxs-lookup"><span data-stu-id="f55e9-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), and [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span></span>

 <span data-ttu-id="f55e9-113">Aby odwołać się do zestawu międzyoperacyjnego przy użyciu kompilatora wiersza polecenia i informacje o typie osadzania w plikach wykonywalnych, należy użyć [opcji/link (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub/ [/lub/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) kompilatora i określić nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f55e9-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="f55e9-114">Aplikacje C++ wizualne nie mogą osadzić informacji o typie, ale mogą współdziałać z aplikacjami lub dodatkami, które wykonują operacje.</span><span class="sxs-lookup"><span data-stu-id="f55e9-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="f55e9-115">Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny podczas jego wdrażania, użyj przełącznika kompilatora **/Reference** i określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f55e9-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="f55e9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f55e9-116">See also</span></span>

- [<span data-ttu-id="f55e9-117">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f55e9-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="f55e9-118">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="f55e9-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="f55e9-119">[Używanie typów COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f55e9-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="f55e9-120">Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual StudioC#()</span><span class="sxs-lookup"><span data-stu-id="f55e9-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="f55e9-121">Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f55e9-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="f55e9-122">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="f55e9-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
