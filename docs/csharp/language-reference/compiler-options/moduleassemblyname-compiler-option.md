---
title: -moduleassemblyname — (opcją kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 9e4768b598f6046ffb7a0ac014d8594eac40309f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593054"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="c9910-102">-moduleassemblyname — (opcją kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c9910-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="c9910-103">Określa, których typy bez publicznego .netmodule mogą uzyskiwać dostęp do zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9910-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9910-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9910-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="c9910-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c9910-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="c9910-106">Nazwa zestawu, którego niepublicznych typy .netmodule mogą uzyskiwać dostęp.</span><span class="sxs-lookup"><span data-stu-id="c9910-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9910-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9910-107">Remarks</span></span>  
 <span data-ttu-id="c9910-108">**-moduleassemblyname** należy używać podczas tworzenia modułu .netmodule, a w przypadku, gdy są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="c9910-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="c9910-109">.netmodule musi mieć dostęp do typów niepublicznych w istniejącego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9910-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="c9910-110">Znasz nazwę zestawu, do którego zostanie utworzona .netmodule.</span><span class="sxs-lookup"><span data-stu-id="c9910-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="c9910-111">Istniejący zestaw przyznał prawa dostępu do zestawu friend do zestawu, do którego zostanie utworzona .netmodule.</span><span class="sxs-lookup"><span data-stu-id="c9910-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="c9910-112">Aby uzyskać więcej informacji na temat budowania .netmodule zobacz [-target: module (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c9910-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="c9910-113">Aby uzyskać więcej informacji na temat przyjaznych zestawów, zobacz [przyjaznych zestawów](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="c9910-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="c9910-114">Ta opcja nie jest dostępne z poziomu środowiska programistycznego; jest on dostępny tylko wtedy, podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c9910-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="c9910-115">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="c9910-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9910-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9910-116">Example</span></span>  
 <span data-ttu-id="c9910-117">Ten przykład tworzy zestaw o prywatny typ i daje dostęp do zestawu friend do zestawu o nazwie csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="c9910-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="c9910-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9910-118">Example</span></span>  
 <span data-ttu-id="c9910-119">Ten przykład tworzy .netmodule, który uzyskuje dostęp do typu niepublicznych w moduleassemblyname_1.dll zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9910-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="c9910-120">Wiadomo, że tego modułu .netmodule zostanie skompilowany w zestawie o nazwie csman_an_assembly, można określić **- moduleassemblyname**, dzięki czemu netmodule można uzyskiwać dostęp do typów niepublicznych w zestawie, który przyznał przyjaznego zestawu dostęp do csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="c9910-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="c9910-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9910-121">Example</span></span>  
 <span data-ttu-id="c9910-122">Ten przykładowy kod tworzy csman_an_assembly zestawu, odwołania do zestawu wcześniej skompilowana i .netmodule.</span><span class="sxs-lookup"><span data-stu-id="c9910-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="c9910-123">**An_Internal_Class.test o nazwie**</span><span class="sxs-lookup"><span data-stu-id="c9910-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="c9910-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9910-124">See also</span></span>

- [<span data-ttu-id="c9910-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="c9910-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="c9910-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="c9910-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
