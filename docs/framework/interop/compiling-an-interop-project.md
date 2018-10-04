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
ms.openlocfilehash: 7088c7f7765f0c5cfc4d6151dcda6f57b8de10d2
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580014"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="38f8d-102">Kompilowanie projektu międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="38f8d-102">Compiling an Interop Project</span></span>

<span data-ttu-id="38f8d-103">COM projektów międzyoperacyjnych, które odwołują się jeden lub więcej zestawów, zawierające zaimportowane typy modelu COM są kompilowane takich jak zarządzanego projektu.</span><span class="sxs-lookup"><span data-stu-id="38f8d-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="38f8d-104">Możesz odwoływać się do zestawów międzyoperacyjnych w środowisku programowania, takiego jak Visual Studio lub można się odwołać je korzystając z wiersza polecenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="38f8d-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="38f8d-105">W obu przypadkach aby skompilować poprawnie, zestaw międzyoperacyjny musi być w tym samym katalogu co innych plików projektów.</span><span class="sxs-lookup"><span data-stu-id="38f8d-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="38f8d-106">Istnieją dwa sposoby, aby odwoływać się do zestawów międzyoperacyjnych:</span><span class="sxs-lookup"><span data-stu-id="38f8d-106">There are two ways to reference interop assemblies:</span></span>

-   <span data-ttu-id="38f8d-107">Osadzone typy współdziałania: począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] i Visual Studio 2010, można nakazać kompilatorowi osadzanie informacji o typie z zestawu międzyoperacyjnego, w programie wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="38f8d-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="38f8d-108">Jest to zalecana technika.</span><span class="sxs-lookup"><span data-stu-id="38f8d-108">This is the recommended technique.</span></span>

-   <span data-ttu-id="38f8d-109">Wdrażanie zestawów międzyoperacyjnych: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="38f8d-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="38f8d-110">W tym przypadku zestaw międzyoperacyjny musi zostać wdrożony z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="38f8d-110">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="38f8d-111">Różnice między te dwie metody zostały omówione bardziej szczegółowo w [przy użyciu typów modelu COM w kodzie zarządzany](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="38f8d-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span></span>

 <span data-ttu-id="38f8d-112">Osadzanie typów międzyoperacyjnych z programem Visual Studio została przedstawiona w [wskazówki: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) i [wskazówki: osadzanie typów z zarządzanych zestawów](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="38f8d-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) and [Walkthrough: Embedding Types from Managed Assemblies](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>

 <span data-ttu-id="38f8d-113">Aby odwoływać się do zestawu międzyoperacyjnego, za pomocą kompilatora wiersza polecenia i osadzić informacje o typie w swoje pliki wykonywalne, użyj [/Link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) przełącznika kompilatora i Określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="38f8d-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="38f8d-114">Aplikacje programu Visual C++ nie można osadzić informacje o typie, ale mogą współdziałać aplikacji lub dodatki, które wykonują.</span><span class="sxs-lookup"><span data-stu-id="38f8d-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="38f8d-115">Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny, gdy aplikacja jest wdrożona, użyj **/reference** kompilatora przełącznika i określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="38f8d-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="38f8d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38f8d-116">See Also</span></span>

- [<span data-ttu-id="38f8d-117">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38f8d-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="38f8d-118">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="38f8d-118">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="38f8d-119">[Używanie typów modelu COM w kodzie zarządzanym](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38f8d-119">[Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span></span>
- <span data-ttu-id="38f8d-120">[Przewodnik: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="38f8d-120">[Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span></span>
- [<span data-ttu-id="38f8d-121">Przewodnik: osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="38f8d-121">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)
- [<span data-ttu-id="38f8d-122">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="38f8d-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)