---
title: Przyjazne zestawy
description: Zestaw zaprzyjaźniony jest zestawem .NET, który ma dostęp do wewnętrznych typów i elementów członkowskich innego zestawu (C#) lub zaprzyjaźnionych (Visual Basic).
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 105621da2bd418c6294fa2bbec474809599cb6a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378936"
---
# <a name="friend-assemblies"></a><span data-ttu-id="c3760-103">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="c3760-103">Friend assemblies</span></span>

<span data-ttu-id="c3760-104">*Zestaw zaprzyjaźniony* jest zestawem, który ma dostęp do [wewnętrznych](../../csharp/language-reference/keywords/internal.md) typów i elementów członkowskich innego zestawu (C#) lub [zaprzyjaźnionych](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c3760-104">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="c3760-105">Jeśli zestaw jest identyfikowany jako zestaw zaprzyjaźniony, nie trzeba już oznaczać typów i składowych jako publicznych, aby były dostępne dla innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="c3760-105">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="c3760-106">Jest to szczególnie wygodne w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="c3760-106">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="c3760-107">Podczas testowania jednostkowego, gdy kod testowy jest uruchamiany w osobnym zestawie, ale wymaga dostępu do elementów członkowskich w testowanym zestawie, które są oznaczone jako `internal` w języku C# lub `Friend` w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3760-107">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="c3760-108">Podczas tworzenia biblioteki klas i dodania do biblioteki są zawarte w oddzielnych zestawach, ale wymagają dostępu do elementów członkowskich w istniejących zestawach, które są oznaczone jako `internal` w języku C# lub `Friend` w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3760-108">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3760-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3760-109">Remarks</span></span>

<span data-ttu-id="c3760-110">Możesz użyć atrybutu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Aby zidentyfikować jeden lub więcej zaprzyjaźnionych zestawów dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c3760-110">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="c3760-111">W poniższym przykładzie zastosowano <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut w *zestawie* a i określa Assembly *AssemblyB* jako zestaw zaprzyjaźniony.</span><span class="sxs-lookup"><span data-stu-id="c3760-111">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="c3760-112">Daje to zestawowi *AssemblyB* dostęp do wszystkich typów i członków w *zestawie a* , które są oznaczone jako `internal` w języku C# lub `Friend` w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3760-112">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="c3760-113">Podczas kompilowania zestawu, takiego jak *AssemblyB* , który będzie uzyskiwać dostęp do typów wewnętrznych lub wewnętrznych elementów członkowskich innego zestawu, takiego jak *zestaw A*, należy jawnie określić nazwę pliku wyjściowego (*exe* lub *. dll*) przy użyciu opcji kompilatora **-out** .</span><span class="sxs-lookup"><span data-stu-id="c3760-113">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="c3760-114">Jest to wymagane, ponieważ kompilator nie wygenerował jeszcze nazwy dla zestawu, który jest tworzony w momencie powiązania z odwołaniami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="c3760-114">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="c3760-115">Aby uzyskać więcej informacji, zobacz sekcję [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="c3760-115">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

```vb
Imports System.Runtime.CompilerServices
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

<span data-ttu-id="c3760-116">Tylko zestawy, które można jawnie określić jako znajomi mogą uzyskać dostęp do `internal` `Friend` typów i składowych (C#) lub (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c3760-116">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="c3760-117">Na przykład, jeśli *AssemblyB* jest znajomością *zestawu* a i *zestawu c* References *AssemblyB*, *zestaw c* nie ma dostępu do `internal` typów (C#) lub `Friend` (Visual Basic) w *zestawie a*.</span><span class="sxs-lookup"><span data-stu-id="c3760-117">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="c3760-118">Kompilator wykonuje pewne podstawowe walidacje nazwy zestawu zaprzyjaźnionego przekazaną do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c3760-118">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="c3760-119">Jeśli *zestaw A* deklaruje *AssemblyB* jako zestaw zaprzyjaźniony, reguły walidacji są następujące:</span><span class="sxs-lookup"><span data-stu-id="c3760-119">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="c3760-120">Jeśli *zestaw A* ma silną nazwę, *AssemblyB* musi być również silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="c3760-120">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="c3760-121">Nazwa zestawu zaprzyjaźnionego, który jest przesyłany do atrybutu, musi zawierać nazwę zestawu i klucz publiczny klucza o silnej nazwie, który jest używany do podpisywania *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="c3760-121">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="c3760-122">Nazwa zestawu zaprzyjaźnionego, która jest przenoszona do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, nie może być silną nazwą *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="c3760-122">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="c3760-123">Nie dołączaj wersji zestawu, kultury, architektury lub tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="c3760-123">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="c3760-124">Jeśli *zestaw A* nie ma silnej nazwy, nazwa zestawu zaprzyjaźnionego powinna zawierać tylko nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="c3760-124">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="c3760-125">Aby uzyskać więcej informacji, zobacz [How to: Create unsigned zaprzyjaźnione zestawy](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="c3760-125">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="c3760-126">Jeśli *AssemblyB* ma silną nazwę, należy określić klucz silnej nazwy dla *AssemblyB* przy użyciu ustawienia projektu lub `/keyfile` opcji kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c3760-126">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="c3760-127">Aby uzyskać więcej informacji, zobacz [How to: Create podpisane zaprzyjaźnione zestawy](create-signed-friend.md).</span><span class="sxs-lookup"><span data-stu-id="c3760-127">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="c3760-128"><xref:System.Security.Permissions.StrongNameIdentityPermission>Klasa oferuje również możliwość udostępniania typów z następującymi różnicami:</span><span class="sxs-lookup"><span data-stu-id="c3760-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="c3760-129"><xref:System.Security.Permissions.StrongNameIdentityPermission>dotyczy pojedynczego typu, podczas gdy zestaw zaprzyjaźniony ma zastosowanie do całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c3760-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="c3760-130">Jeśli istnieją setki typów w *zestawie A* , które chcesz udostępnić w *AssemblyB*, musisz dodać <xref:System.Security.Permissions.StrongNameIdentityPermission> je do wszystkich.</span><span class="sxs-lookup"><span data-stu-id="c3760-130">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="c3760-131">Jeśli używasz zestawu zaprzyjaźnionego, musisz tylko raz zadeklarować relację zaprzyjaźnioną.</span><span class="sxs-lookup"><span data-stu-id="c3760-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="c3760-132">Jeśli używasz <xref:System.Security.Permissions.StrongNameIdentityPermission> , typy, które chcesz udostępnić, muszą być zadeklarowane jako publiczne.</span><span class="sxs-lookup"><span data-stu-id="c3760-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="c3760-133">Jeśli używasz zestawu zaprzyjaźnionego, typy udostępnione są zadeklarowane jako `internal` (C#) lub `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c3760-133">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="c3760-134">Aby uzyskać informacje na temat sposobu uzyskiwania dostępu do `internal` typów i metod zestawu (C#) lub `Friend` (Visual Basic) z pliku modułu (pliku z rozszerzeniem *. webmodule* ), zobacz [-moduleassemblyname — (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) lub [-moduleassemblyname — (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="c3760-134">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3760-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3760-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="c3760-136">Instrukcje: Tworzenie nieoznaczonych zaprzyjaźnionych zestawów</span><span class="sxs-lookup"><span data-stu-id="c3760-136">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="c3760-137">Instrukcje: Tworzenie podpisanych zestawów zaprzyjaźnionych</span><span class="sxs-lookup"><span data-stu-id="c3760-137">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="c3760-138">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="c3760-138">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="c3760-139">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c3760-139">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c3760-140">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3760-140">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
