---
title: -moduleassemblyname (Opcja kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 1477eeb0f2e16e18cb86009739bc8e7d9dee2ac0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173721"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="4645c-102">-moduleassemblyname (Opcja kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="4645c-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="4645c-103">Określa zestaw, do którego niepubliczne typy .netmodule mogą uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="4645c-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4645c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4645c-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="4645c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4645c-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="4645c-106">Nazwa zestawu, którego niepubliczne typy .netmodule można uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="4645c-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4645c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4645c-107">Remarks</span></span>  
 <span data-ttu-id="4645c-108">**-moduleassemblyname** należy używać podczas tworzenia .netmodule i tam, gdzie spełnione są następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="4645c-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="4645c-109">Moduł .netmodule wymaga dostępu do typów niepublicznych w istniejącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="4645c-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="4645c-110">Znasz nazwę zestawu, w którym zostanie utworzony moduł .netmodule.</span><span class="sxs-lookup"><span data-stu-id="4645c-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="4645c-111">Istniejący zestaw przyznał zestawowi znajomych dostęp do zestawu, w którym zostanie utworzony moduł .netmodule.</span><span class="sxs-lookup"><span data-stu-id="4645c-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="4645c-112">Aby uzyskać więcej informacji na temat tworzenia .netmodule, zobacz [-target:module (Opcje kompilatora C#)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4645c-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="4645c-113">Aby uzyskać więcej informacji na temat zgromadzeń znajomych, zobacz [Zestawy znajomych](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="4645c-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="4645c-114">Ta opcja nie jest dostępna w środowisku programistycznym; jest dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4645c-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="4645c-115">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="4645c-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4645c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="4645c-116">Example</span></span>  
 <span data-ttu-id="4645c-117">Ten przykład tworzy zestaw z typem prywatnym i który daje dostęp do zestawu znajomego do zestawu o nazwie csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="4645c-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4645c-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="4645c-118">Example</span></span>  
 <span data-ttu-id="4645c-119">Ten przykład tworzy .netmodule, który uzyskuje dostęp do typu niepublicznego w zestawie moduleassemblyname_1.dll.</span><span class="sxs-lookup"><span data-stu-id="4645c-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="4645c-120">Wiedząc, że ten .netmodule zostanie wbudowany w zestaw o nazwie csman_an_assembly, możemy określić **-moduleassemblyname,** umożliwiając modułowi .netmoduł dostęp do typów niepublicznych w zestawie, który przyznał dostęp do zestawu znajomych do csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="4645c-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4645c-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="4645c-121">Example</span></span>  
 <span data-ttu-id="4645c-122">Ten przykładowy kod tworzy csman_an_assembly zestawu, odwołując się do wcześniej utworzonego zestawu i .netmodule.</span><span class="sxs-lookup"><span data-stu-id="4645c-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
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
  
<span data-ttu-id="4645c-123">**An_Internal_Class.Test o nazwie**</span><span class="sxs-lookup"><span data-stu-id="4645c-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="4645c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4645c-124">See also</span></span>

- [<span data-ttu-id="4645c-125">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="4645c-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4645c-126">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="4645c-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
