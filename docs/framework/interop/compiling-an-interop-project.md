---
title: Kompilowanie projektu międzyoperacyjnego
description: Zapoznaj się z tematem kompilowania projektu międzyoperacyjnego modelu COM, który jest kompilowany jak projekty zarządzane, jeśli odwołują się do jednego lub większej liczby zestawów zawierających importowane typy COM.
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
ms.openlocfilehash: a8dfbeb88d0057eb3c9047b4435f021750ed86d2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620862"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="746a9-103">Kompilowanie projektu międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="746a9-103">Compiling an Interop Project</span></span>

<span data-ttu-id="746a9-104">Projekty międzyoperacyjności modelu COM, które odwołują się do co najmniej jednego zestawu zawierającego zaimportowane typy COM, są kompilowane jak każdy inny projekt zarządzany.</span><span class="sxs-lookup"><span data-stu-id="746a9-104">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="746a9-105">Można odwoływać się do zestawów międzyoperacyjnych w środowisku deweloperskim, takim jak Visual Studio, lub można się do nich odwoływać przy użyciu kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="746a9-105">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="746a9-106">W obu przypadkach w celu poprawnego skompilowania zestaw międzyoperacyjny musi znajdować się w tym samym katalogu co inne pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="746a9-106">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="746a9-107">Istnieją dwa sposoby odwoływania się do zestawów międzyoperacyjnych:</span><span class="sxs-lookup"><span data-stu-id="746a9-107">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="746a9-108">Osadzone typy międzyoperacyjnych: począwszy od .NET Framework 4 i programu Visual Studio 2010, można wydać kompilatorowi możliwość osadzenia informacji o typie z zestawu międzyoperacyjnego w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="746a9-108">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="746a9-109">Jest to zalecana technika.</span><span class="sxs-lookup"><span data-stu-id="746a9-109">This is the recommended technique.</span></span>

- <span data-ttu-id="746a9-110">Wdrażanie zestawów międzyoperacyjnych: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="746a9-110">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="746a9-111">W takim przypadku zestaw międzyoperacyjny musi zostać wdrożony wraz z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="746a9-111">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="746a9-112">Różnice między tymi dwoma technikami zostały omówione bardziej szczegółowo w temacie [Korzystanie z typów com w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="746a9-112">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="746a9-113">Osadzanie typów międzyoperacyjnych w programie Visual Studio jest zademonstrowane w [przewodniku: osadzanie typów z zestawów zarządzanych w programie Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="746a9-113">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="746a9-114">Aby odwołać się do zestawu międzyoperacyjnego przy użyciu kompilatora wiersza polecenia i osadzić informacje o typie w plikach wykonywalnych, użyj [linku (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub przełącznika [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) kompilatora i określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="746a9-114">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="746a9-115">Aplikacje Visual C++ nie mogą osadzić informacji o typie, ale mogą współdziałać z aplikacjami lub dodatkami, które wykonują operacje.</span><span class="sxs-lookup"><span data-stu-id="746a9-115">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="746a9-116">Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny podczas jego wdrażania, użyj przełącznika kompilatora **/Reference** i określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="746a9-116">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="746a9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="746a9-117">See also</span></span>

- [<span data-ttu-id="746a9-118">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="746a9-118">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="746a9-119">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="746a9-119">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="746a9-120">[Używanie typów COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="746a9-120">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="746a9-121">Przewodnik: osadzanie typów z zarządzanych zestawów w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="746a9-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="746a9-122">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="746a9-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
