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
ms.openlocfilehash: 4369ce9c9ce82ecdbf11d76f3b043778b8374d8b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489755"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="6da52-102">Kompilowanie projektu międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="6da52-102">Compiling an Interop Project</span></span>

<span data-ttu-id="6da52-103">COM projektów międzyoperacyjnych, które odwołują się jeden lub więcej zestawów, zawierające zaimportowane typy modelu COM są kompilowane takich jak zarządzanego projektu.</span><span class="sxs-lookup"><span data-stu-id="6da52-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="6da52-104">Możesz odwoływać się do zestawów międzyoperacyjnych w środowisku programowania, takiego jak Visual Studio lub można się odwołać je korzystając z wiersza polecenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6da52-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="6da52-105">W obu przypadkach aby skompilować poprawnie, zestaw międzyoperacyjny musi być w tym samym katalogu co innych plików projektów.</span><span class="sxs-lookup"><span data-stu-id="6da52-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="6da52-106">Istnieją dwa sposoby, aby odwoływać się do zestawów międzyoperacyjnych:</span><span class="sxs-lookup"><span data-stu-id="6da52-106">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="6da52-107">Osadzone typy międzyoperacyjne: Począwszy od programu .NET Framework 4 i Visual Studio 2010, można nakazać kompilatorowi do osadzenia informacji o typie z zestawu międzyoperacyjnego, w programie wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="6da52-107">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="6da52-108">Jest to zalecana technika.</span><span class="sxs-lookup"><span data-stu-id="6da52-108">This is the recommended technique.</span></span>

- <span data-ttu-id="6da52-109">Wdrażanie zestawów międzyoperacyjnych: Można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6da52-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="6da52-110">W tym przypadku zestaw międzyoperacyjny musi zostać wdrożony z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="6da52-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="6da52-111">Różnice między te dwie metody zostały omówione bardziej szczegółowo w [przy użyciu typów modelu COM w kodzie zarządzany](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6da52-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="6da52-112">Osadzanie typów międzyoperacyjnych z programem Visual Studio została przedstawiona w [instruktażu: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), i [instruktażu: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6da52-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), and [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).</span></span>

 <span data-ttu-id="6da52-113">Aby odwoływać się do zestawu międzyoperacyjnego, za pomocą kompilatora wiersza polecenia i osadzić informacje o typie w swoje pliki wykonywalne, użyj [/Link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) przełącznika kompilatora i Określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6da52-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="6da52-114">Aplikacje programu Visual C++ nie można osadzić informacje o typie, ale mogą współdziałać aplikacji lub dodatki, które wykonują.</span><span class="sxs-lookup"><span data-stu-id="6da52-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="6da52-115">Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny, gdy aplikacja jest wdrożona, użyj **/reference** kompilatora przełącznika i określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6da52-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="6da52-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6da52-116">See also</span></span>

- [<span data-ttu-id="6da52-117">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6da52-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="6da52-118">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="6da52-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="6da52-119">[Używanie typów modelu COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6da52-119">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="6da52-120">Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="6da52-120">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="6da52-121">Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6da52-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="6da52-122">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="6da52-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
