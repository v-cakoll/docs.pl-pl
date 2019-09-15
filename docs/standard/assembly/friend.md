---
title: Przyjazne zestawy
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 6387e93bcd4efeec57ada9228dcaf015d053dbf7
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973237"
---
# <a name="friend-assemblies"></a><span data-ttu-id="c1b9d-102">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="c1b9d-102">Friend assemblies</span></span>

<span data-ttu-id="c1b9d-103">*Zestaw zaprzyjaźniony* jest zestawem, który może uzyskiwać dostęp do typów iC#elementów [wewnętrznych](../../csharp/language-reference/keywords/internal.md) () lub [zaprzyjaźnionych](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="c1b9d-104">Jeśli zestaw jest identyfikowany jako zestaw zaprzyjaźniony, nie trzeba już oznaczać typów i składowych jako publicznych, aby były dostępne dla innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="c1b9d-105">Jest to szczególnie wygodne w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="c1b9d-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="c1b9d-106">Podczas testowania jednostkowego, gdy kod testowy jest uruchamiany w osobnym zestawie, ale wymaga dostępu do elementów członkowskich w testowanym zestawie, które `internal` są C# oznaczone `Friend` jako w lub w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="c1b9d-107">Podczas tworzenia biblioteki klas, a dodatki do biblioteki są zawarte w oddzielnych zestawach, ale wymagają dostępu do elementów członkowskich w istniejących zestawach, które są `internal` oznaczone C# jako `Friend` w lub w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1b9d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1b9d-108">Remarks</span></span>

<span data-ttu-id="c1b9d-109">Możesz użyć atrybutu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> aby zidentyfikować jeden lub więcej zaprzyjaźnionych zestawów dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="c1b9d-110">W poniższym przykładzie zastosowano <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut w *zestawie* a i określa Assembly *AssemblyB* jako zestaw zaprzyjaźniony.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="c1b9d-111">Daje to zestawowi *AssemblyB* dostęp do wszystkich typów i członków w *zestawie a* , które są `internal` oznaczone C# jako `Friend` w lub w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="c1b9d-112">Podczas kompilowania zestawu, takiego jak *AssemblyB* , który będzie uzyskiwać dostęp do typów wewnętrznych lub wewnętrznych elementów członkowskich innego zestawu, takiego jak *zestaw A*, należy jawnie określić nazwę pliku wyjściowego (*exe* lub *dll*) przy użyciu polecenia **/out** opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **/out** compiler option.</span></span> <span data-ttu-id="c1b9d-113">Jest to wymagane, ponieważ kompilator nie wygenerował jeszcze nazwy dla zestawu, który jest tworzony w momencie powiązania z odwołaniami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="c1b9d-114">Aby uzyskać więcej informacji, zobacz [/outC#()](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="c1b9d-114">For more information, see [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

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
Imports System
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

<span data-ttu-id="c1b9d-115">Tylko zestawy, które można jawnie określić jako znajomi mogą `internal` uzyskaćC#dostęp ( `Friend` ) lub (Visual Basic) typów i członków.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="c1b9d-116">Na przykład, jeśli *AssemblyB* jest znajomością *zestawu* a i *zestawu c* References *AssemblyB*, *zestaw c* nie ma dostępu `internal` do (C#) lub `Friend` (Visual Basic) typów w *zestawie a* .</span><span class="sxs-lookup"><span data-stu-id="c1b9d-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="c1b9d-117">Kompilator wykonuje pewne podstawowe walidacje nazwy zestawu zaprzyjaźnionego przekazaną do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="c1b9d-118">Jeśli *zestaw A* deklaruje *AssemblyB* jako zestaw zaprzyjaźniony, reguły walidacji są następujące:</span><span class="sxs-lookup"><span data-stu-id="c1b9d-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="c1b9d-119">Jeśli *zestaw A* ma silną nazwę, *AssemblyB* musi być również silną nazwą.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="c1b9d-120">Nazwa zestawu zaprzyjaźnionego, który jest przesyłany do atrybutu, musi zawierać nazwę zestawu i klucz publiczny klucza o silnej nazwie, który jest używany do podpisywania *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="c1b9d-121">Nazwa zestawu zaprzyjaźnionego, która jest przenoszona <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> do atrybutu, nie może być silną nazwą *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="c1b9d-122">Nie dołączaj wersji zestawu, kultury, architektury lub tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-122">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="c1b9d-123">Jeśli *zestaw A* nie ma silnej nazwy, nazwa zestawu zaprzyjaźnionego powinna zawierać tylko nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="c1b9d-124">Aby uzyskać więcej informacji, zobacz [jak: Utwórz niepodpisane zaprzyjaźnione zestawy](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="c1b9d-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="c1b9d-125">Jeśli *AssemblyB* ma silną nazwę, należy określić klucz silnej nazwy dla *AssemblyB* przy użyciu ustawienia projektu lub opcji kompilatora wiersza `/keyfile` polecenia.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="c1b9d-126">Aby uzyskać więcej informacji, zobacz [jak: Utwórz podpisane zaprzyjaźnione](create-signed-friend.md)zestawy.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="c1b9d-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> Klasa oferuje również możliwość udostępniania typów z następującymi różnicami:</span><span class="sxs-lookup"><span data-stu-id="c1b9d-127">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="c1b9d-128"><xref:System.Security.Permissions.StrongNameIdentityPermission>dotyczy pojedynczego typu, podczas gdy zestaw zaprzyjaźniony ma zastosowanie do całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="c1b9d-129">Jeśli istnieją setki typów w *zestawie A* , które chcesz udostępnić w *AssemblyB*, musisz dodać <xref:System.Security.Permissions.StrongNameIdentityPermission> je do wszystkich.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="c1b9d-130">Jeśli używasz zestawu zaprzyjaźnionego, musisz tylko raz zadeklarować relację zaprzyjaźnioną.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-130">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="c1b9d-131">Jeśli używasz <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, które chcesz udostępnić, muszą być zadeklarowane jako publiczne.</span><span class="sxs-lookup"><span data-stu-id="c1b9d-131">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="c1b9d-132">Jeśli używasz zestawu zaprzyjaźnionego, typy udostępnione są zadeklarowane jako `internal` (C#) lub `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c1b9d-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="c1b9d-133">Aby uzyskać informacje o sposobach uzyskiwania dostępu do `internal` typówC#i metod `Friend` zestawu () lub (Visual Basic) z pliku modułu (pliku z rozszerzeniem *. webmodule* ), zobacz [/moduleassemblynameC#()](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) lub [/ moduleassemblyname — (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="c1b9d-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c1b9d-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1b9d-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="c1b9d-135">Instrukcje: Utwórz niepodpisane zestawy zaprzyjaźnione</span><span class="sxs-lookup"><span data-stu-id="c1b9d-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="c1b9d-136">Instrukcje: Utwórz podpisane zaprzyjaźnione zestawy</span><span class="sxs-lookup"><span data-stu-id="c1b9d-136">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="c1b9d-137">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="c1b9d-137">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="c1b9d-138">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="c1b9d-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c1b9d-139">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1b9d-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
