---
title: -moduleassemblyname — (C# opcja kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: d57279128c0909ba3e62d55d596705cfde6be75c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606666"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="3d986-102">-moduleassemblyname — (C# opcja kompilatora)</span><span class="sxs-lookup"><span data-stu-id="3d986-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="3d986-103">Określa zestaw, którego typy niepubliczne a. module mogą uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="3d986-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d986-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d986-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d986-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3d986-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="3d986-106">Nazwa zestawu, którego typy niepubliczne mogą uzyskać dostęp do modułu.</span><span class="sxs-lookup"><span data-stu-id="3d986-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d986-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d986-107">Remarks</span></span>  
 <span data-ttu-id="3d986-108">**-moduleassemblyname —** należy używać podczas kompilowania modułu. sieci i, gdy są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="3d986-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="3d986-109">Moduł. Webmusi mieć dostęp do niepublicznych typów w istniejącym zestawie.</span><span class="sxs-lookup"><span data-stu-id="3d986-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="3d986-110">Znasz nazwę zestawu, do którego zostanie skompilowany moduł.</span><span class="sxs-lookup"><span data-stu-id="3d986-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="3d986-111">Istniejący zestaw przydzieli znajomemu dostęp do zestawu, do którego zostanie skompilowany moduł.</span><span class="sxs-lookup"><span data-stu-id="3d986-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="3d986-112">Aby uzyskać więcej informacji na temat tworzenia modułu., zobacz [-target: module (C# opcje kompilatora)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3d986-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="3d986-113">Aby uzyskać więcej informacji o znajomych zestawach, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="3d986-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="3d986-114">Ta opcja jest niedostępna w środowisku programistycznym; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3d986-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="3d986-115">Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.</span><span class="sxs-lookup"><span data-stu-id="3d986-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d986-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d986-116">Example</span></span>  
 <span data-ttu-id="3d986-117">Ten przykład kompiluje zestaw z typem prywatnym i zapewnia znajomemu dostęp do zestawu o nazwie csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="3d986-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3d986-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d986-118">Example</span></span>  
 <span data-ttu-id="3d986-119">Ten przykład tworzy moduł. Service, który uzyskuje dostęp do niepublicznego typu w zestawie moduleassemblyname_1. dll.</span><span class="sxs-lookup"><span data-stu-id="3d986-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="3d986-120">Wiedząc, że ten moduł. module zostanie skompilowany w zestawie o nazwie csman_an_assembly, możemy określić wartość **-moduleassemblyname —** , umożliwiając modułowi. servicedostęp do niepublicznych typów w zestawie, który udzielił znajomemu dostęp do zestawu csman_an_ hamulc.</span><span class="sxs-lookup"><span data-stu-id="3d986-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3d986-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d986-121">Example</span></span>  
 <span data-ttu-id="3d986-122">Ten przykładowy kod kompiluje csman_an_assembly zestawu, który odwołuje się do wcześniej skompilowanego zestawu i modułu.</span><span class="sxs-lookup"><span data-stu-id="3d986-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
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
  
<span data-ttu-id="3d986-123">**An_Internal_Class. test wywołany**</span><span class="sxs-lookup"><span data-stu-id="3d986-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="3d986-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d986-124">See also</span></span>

- [<span data-ttu-id="3d986-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="3d986-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3d986-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="3d986-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
