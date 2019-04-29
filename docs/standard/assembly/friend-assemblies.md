---
title: Przyjazne zestawy (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627872"
---
# <a name="friend-assemblies"></a><span data-ttu-id="279b0-102">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="279b0-102">Friend assemblies</span></span>

<span data-ttu-id="279b0-103">A *przyjaznego zestawu* to zestaw, który mogą uzyskiwać dostęp do innego zestawu [wewnętrzny](../../csharp/language-reference/keywords/internal.md) (w C# lub [Friend](../../visual-basic/language-reference/modifiers/friend.md) w języku Visual Basic) typy i elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="279b0-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (in C# or [Friend](../../visual-basic/language-reference/modifiers/friend.md) in Visual Basic) types and members.</span></span> <span data-ttu-id="279b0-104">Po zidentyfikowaniu zestawu jako zestaw przyjazny, masz już Oznacz typy i elementy członkowskie jako publiczny je, aby były dostępne dla innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="279b0-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="279b0-105">Jest to szczególnie wygodne w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="279b0-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="279b0-106">Podczas testowania jednostek, gdy kod testowy jest uruchamiany osobny zestaw ale wymaga dostępu do elementów członkowskich w zestawie poddawana testom, które są oznaczone jako `internal` w C# lub `Friend` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="279b0-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="279b0-107">Podczas tworzenia biblioteki klas i ma zostać dodany do biblioteki znajdują się w osobnych zestawach, ale wymagają dostępu do elementów członkowskich w istniejących zestawów, które są oznaczone jako `internal` w C# lub `Friend` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="279b0-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="279b0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="279b0-108">Remarks</span></span>

<span data-ttu-id="279b0-109">Możesz użyć <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut do identyfikowania jeden lub więcej zestawów przyjaznego dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="279b0-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="279b0-110">W poniższym przykładzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu w zestawie A i określa zestaw `AssemblyB` jako przyjaznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="279b0-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="279b0-111">Dzięki temu zestaw `AssemblyB` dostęp do wszystkich typów i elementów członkowskich w zestawie, które są oznaczone jako `internal` w C# lub `Friend` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="279b0-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="279b0-112">Gdy kompilujesz zestaw (zestaw `AssemblyB`) będzie uzyskiwać dostęp typy wewnętrzne lub wewnętrzne członków innego zestawu (zestaw *A*), należy jawnie określić nazwę pliku wyjściowego (.exe lub .dll), używając **/out** — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="279b0-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="279b0-113">Jest to wymagane, ponieważ kompilator nie ma jeszcze wygenerować nazwę zestawu, który tworzysz w czasie, który jest wiązanie odwołań zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="279b0-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="279b0-114">Aby uzyskać więcej informacji, zobacz [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="279b0-114">For more information, see [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="279b0-115">C#</span><span class="sxs-lookup"><span data-stu-id="279b0-115">C#</span></span>](#tab/csharp)

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

# <a name="visual-basictabvb"></a>[<span data-ttu-id="279b0-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="279b0-116">Visual Basic</span></span>](#tab/vb)

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

---

<span data-ttu-id="279b0-117">Tylko zestawy, które zostaną jawnie określone, zgodnie z przyjaciółmi mogą uzyskiwać dostęp do `internal` (w C# lub `Friend` w języku Visual Basic) typy i elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="279b0-117">Only assemblies that you explicitly specify as friends can access `internal` (in C# or `Friend` in Visual Basic) types and members.</span></span> <span data-ttu-id="279b0-118">Na przykład, jeśli zestaw B jest przyjaznego zestawu A i C zestawu odwołania do zestawu B, C nie ma dostępu do `internal` (w C# lub `Friend` w języku Visual Basic) typy w A.</span><span class="sxs-lookup"><span data-stu-id="279b0-118">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` (in C# or `Friend` in Visual Basic) types in A.</span></span>

<span data-ttu-id="279b0-119">Kompilator wykonuje niektóre podstawowe sprawdzanie poprawności nazwy przyjaznego zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="279b0-119">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="279b0-120">Jeśli zestaw *A* deklaruje *B* jako zestaw przyjaznych reguły sprawdzania poprawności są następujące:</span><span class="sxs-lookup"><span data-stu-id="279b0-120">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="279b0-121">Jeśli zestaw *A* jest silną nazwę zestawu *B* również musi mieć silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="279b0-121">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="279b0-122">Nazwy przyjaznego zestawu, który jest przekazywany do atrybutu musi zawierać nazwę zestawu i klucz publiczny klucz silnej nazwy, który jest używany do podpisywania zestawu *B*.</span><span class="sxs-lookup"><span data-stu-id="279b0-122">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>

     <span data-ttu-id="279b0-123">Nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut nie może być silnej nazwy zestawu *B*: nie ma zestawu wersji, kultury, architektury lub token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="279b0-123">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="279b0-124">Jeśli zestaw *A* nie jest silną nazwę, nazwy przyjaznego zestawu powinna składać się wyłącznie nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="279b0-124">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="279b0-125">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie nieoznaczonych przyjaznych zestawów (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) lub [jak: Tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="279b0-125">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) or [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>

- <span data-ttu-id="279b0-126">Jeśli zestaw *B* jest silną nazwę, należy określić klucz silnej nazwy zestawu *B* przy użyciu wiersza polecenia i ustawienie projektu `/keyfile` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="279b0-126">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="279b0-127">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie oznaczonych przyjaznych zestawów (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) lub [jak: Tworzenie oznaczonych przyjaznych zestawów (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="279b0-127">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) or [How to: Create Signed Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>

 <span data-ttu-id="279b0-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> Klasa udostępnia także możliwość udostępniania typów, z następującymi różnicami:</span><span class="sxs-lookup"><span data-stu-id="279b0-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="279b0-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> ma zastosowanie do poszczególnych typu, gdy zestaw przyjazny, który ma zastosowanie do całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="279b0-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="279b0-130">Jeśli istnieją setki typów w zestawie *A* , którą chcesz udostępnić zestawu *B*, trzeba dodać <xref:System.Security.Permissions.StrongNameIdentityPermission> do wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="279b0-130">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="279b0-131">Jeśli używasz zestaw przyjazny, wystarczy raz deklarowania relacji friend.</span><span class="sxs-lookup"><span data-stu-id="279b0-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="279b0-132">Jeśli używasz <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, które chcesz udostępnić musi być zadeklarowana jako publiczne.</span><span class="sxs-lookup"><span data-stu-id="279b0-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="279b0-133">Jeśli używasz zestaw przyjazny, udostępnione typy są deklarowane jako `internal` (w C# lub `Friend` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="279b0-133">If you use a friend assembly, the shared types are declared as `internal` (in C# or `Friend` in Visual Basic).</span></span>

<span data-ttu-id="279b0-134">Aby uzyskać informacje dotyczące dostępu do zestawu `internal` (w C# lub `Friend` w języku Visual Basic) typy i metody z pliku modułu (plik z rozszerzeniem .netmodule), zobacz [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) lub [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="279b0-134">For information about how to access an assembly's `internal` (in C# or `Friend` in Visual Basic) types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="279b0-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="279b0-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="279b0-136">Instrukcje: Tworzenie nieoznaczonych przyjaznych zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="279b0-136">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="279b0-137">Instrukcje: Tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="279b0-137">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="279b0-138">Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="279b0-138">How to: Create Signed Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="279b0-139">Instrukcje: Tworzenie oznaczonych przyjaznych zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="279b0-139">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="279b0-140">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="279b0-140">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="279b0-141">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="279b0-141">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="279b0-142">Pojęcia związane z programowaniem</span><span class="sxs-lookup"><span data-stu-id="279b0-142">Programming Concepts</span></span>](../../visual-basic/programming-guide/concepts/index.md)
