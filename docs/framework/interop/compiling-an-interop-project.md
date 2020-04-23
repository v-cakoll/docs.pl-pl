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
ms.openlocfilehash: 32102910ae674a97e941e1346a1898585f503527
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123683"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="8e48d-102">Kompilowanie projektu międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="8e48d-102">Compiling an Interop Project</span></span>

<span data-ttu-id="8e48d-103">Projekty międzyoperacyjności modelu COM, które odwołują się do co najmniej jednego zestawu zawierającego zaimportowane typy COM, są kompilowane jak każdy inny projekt zarządzany.</span><span class="sxs-lookup"><span data-stu-id="8e48d-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="8e48d-104">Można odwoływać się do zestawów międzyoperacyjnych w środowisku deweloperskim, takim jak Visual Studio, lub można się do nich odwoływać przy użyciu kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8e48d-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="8e48d-105">W obu przypadkach w celu poprawnego skompilowania zestaw międzyoperacyjny musi znajdować się w tym samym katalogu co inne pliki projektu.</span><span class="sxs-lookup"><span data-stu-id="8e48d-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="8e48d-106">Istnieją dwa sposoby odwoływania się do zestawów międzyoperacyjnych:</span><span class="sxs-lookup"><span data-stu-id="8e48d-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="8e48d-107">Osadzone typy międzyoperacyjnych: począwszy od .NET Framework 4 i programu Visual Studio 2010, można wydać kompilatorowi możliwość osadzenia informacji o typie z zestawu międzyoperacyjnego w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="8e48d-107">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="8e48d-108">Jest to zalecana technika.</span><span class="sxs-lookup"><span data-stu-id="8e48d-108">This is the recommended technique.</span></span>

- <span data-ttu-id="8e48d-109">Wdrażanie zestawów międzyoperacyjnych: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8e48d-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="8e48d-110">W takim przypadku zestaw międzyoperacyjny musi zostać wdrożony wraz z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="8e48d-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="8e48d-111">Różnice między tymi dwoma technikami zostały omówione bardziej szczegółowo w temacie [Korzystanie z typów com w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8e48d-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="8e48d-112">Osadzanie typów międzyoperacyjnych w programie Visual Studio jest zademonstrowane w [przewodniku: osadzanie typów z zestawów zarządzanych w programie Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="8e48d-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="8e48d-113">Aby odwołać się do zestawu międzyoperacyjnego przy użyciu kompilatora wiersza polecenia i osadzić informacje o typie w plikach wykonywalnych, użyj [linku (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub przełącznika [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) kompilatora i określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8e48d-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="8e48d-114">Aplikacje Visual C++ nie mogą osadzić informacji o typie, ale mogą współdziałać z aplikacjami lub dodatkami, które wykonują operacje.</span><span class="sxs-lookup"><span data-stu-id="8e48d-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="8e48d-115">Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny podczas jego wdrażania, użyj przełącznika kompilatora **/Reference** i określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8e48d-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e48d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e48d-116">See also</span></span>

- [<span data-ttu-id="8e48d-117">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="8e48d-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="8e48d-118">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="8e48d-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="8e48d-119">[Używanie typów COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8e48d-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="8e48d-120">Przewodnik: osadzanie typów z zarządzanych zestawów w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8e48d-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="8e48d-121">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="8e48d-121">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
