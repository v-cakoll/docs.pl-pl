---
title: Przyjazne zestawy
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348176"
---
# <a name="friend-assemblies"></a><span data-ttu-id="03b62-102">Przyjazne zestawy</span><span class="sxs-lookup"><span data-stu-id="03b62-102">Friend assemblies</span></span>

<span data-ttu-id="03b62-103">*Zestaw znajomego* jest zestaw, który może uzyskać dostęp do [wewnętrznego](../../csharp/language-reference/keywords/internal.md) innego zestawu (C#) lub [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) typów i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="03b62-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="03b62-104">Jeśli zidentyfikujesz zestaw jako zestaw znajomego, nie trzeba już oznaczać typy i elementy członkowskie jako publiczne, aby były dostępne dla nich przez inne zestawy.</span><span class="sxs-lookup"><span data-stu-id="03b62-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="03b62-105">Jest to szczególnie wygodne w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="03b62-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="03b62-106">Podczas testowania jednostkowego, gdy kod testu jest uruchamiany w oddzielnym zestawie, `internal` ale wymaga `Friend` dostępu do elementów członkowskich w testowanym zestawie, które są oznaczone jako c# lub w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03b62-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="03b62-107">Podczas opracowywania biblioteki klas i dodatki do biblioteki są zawarte w oddzielnych zestawów, ale wymagają `internal` dostępu do `Friend` elementów członkowskich w istniejących zestawów, które są oznaczone jako w języku C# lub w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03b62-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="03b62-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03b62-108">Remarks</span></span>

<span data-ttu-id="03b62-109">Atrybut użyje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> do zidentyfikowania jednego lub więcej zestawów znajomych dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="03b62-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="03b62-110">W poniższym <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> przykładzie użyto atrybutu w *zestawie A* i określa zestaw *AssemblyB* jako zestaw znajomego.</span><span class="sxs-lookup"><span data-stu-id="03b62-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="03b62-111">Daje to *assemblyAssemblyB* dostęp do wszystkich typów i `internal` elementów członkowskich `Friend` w *zestawie A,* które są oznaczone jako c# lub w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03b62-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="03b62-112">Podczas kompilowania zestawu, takiego jak *AssemblyB,* który będzie uzyskiwał dostęp do wewnętrznych typów lub wewnętrznych elementów członkowskich innego zestawu, takiego jak *zestaw A,* należy jawnie określić nazwę pliku wyjściowego *(exe* lub *dll)* za pomocą opcji **kompilatora -out.**</span><span class="sxs-lookup"><span data-stu-id="03b62-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="03b62-113">Jest to wymagane, ponieważ kompilator nie wygenerował jeszcze nazwę zestawu, który tworzy w czasie jest powiązany z odwołaniami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="03b62-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="03b62-114">Aby uzyskać więcej informacji, zobacz [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="03b62-114">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

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

<span data-ttu-id="03b62-115">Tylko zestawy, które jawnie określić `internal` jako znajomi `Friend` mogą uzyskać dostęp (C#) lub (Visual Basic) typy i elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="03b62-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="03b62-116">Na przykład jeśli *AssemblyB* jest przyjacielem *zestawu A* i *zestawu C* odwołuje się do *AssemblyB,* *zestaw C* nie ma dostępu `internal` do (C#) lub `Friend` (Visual Basic) typów w zestawie *A*.</span><span class="sxs-lookup"><span data-stu-id="03b62-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="03b62-117">Kompilator wykonuje podstawowe sprawdzanie poprawności nazwy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zestawu znajomego przekazany do atrybutu.</span><span class="sxs-lookup"><span data-stu-id="03b62-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="03b62-118">Jeśli *zestaw A* deklaruje *AssemblyB* jako zestaw przyjaciela, reguły sprawdzania poprawności są następujące:</span><span class="sxs-lookup"><span data-stu-id="03b62-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="03b62-119">Jeśli *zestaw A* jest silny *nazwie, AssemblyB* musi być również silne ja.</span><span class="sxs-lookup"><span data-stu-id="03b62-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="03b62-120">Nazwa zestawu znajomego, która jest przekazywana do atrybutu musi składać się z nazwy zestawu i klucza publicznego klucza silnej nazwy, który jest używany do podpisania *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="03b62-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="03b62-121">Nazwa zestawu znajomego, która <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> jest przekazywana do atrybutu, nie może być silną nazwą *AssemblyB*.</span><span class="sxs-lookup"><span data-stu-id="03b62-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="03b62-122">Nie należy dołączać wersji zestawu, kultury, architektury ani tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="03b62-122">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="03b62-123">Jeśli *zestaw A* nie jest silny nazwie, nazwa zestawu znajomego powinna składać się tylko z nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="03b62-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="03b62-124">Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie niepodpisanych zestawów znajomych](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="03b62-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="03b62-125">Jeśli *AssemblyB* jest silny o nazwie, należy określić klucz silnej nazwy *dla AssemblyB* przy użyciu ustawienia projektu lub opcji kompilatora wiersza `/keyfile` polecenia.</span><span class="sxs-lookup"><span data-stu-id="03b62-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="03b62-126">Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie podpisanych zestawów znajomych](create-signed-friend.md).</span><span class="sxs-lookup"><span data-stu-id="03b62-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="03b62-127">Klasa <xref:System.Security.Permissions.StrongNameIdentityPermission> zapewnia również możliwość udostępniania typów, z następującymi różnicami:</span><span class="sxs-lookup"><span data-stu-id="03b62-127">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="03b62-128"><xref:System.Security.Permissions.StrongNameIdentityPermission>dotyczy pojedynczego typu, podczas gdy zespół znajomego ma zastosowanie do całego złożenia.</span><span class="sxs-lookup"><span data-stu-id="03b62-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="03b62-129">Jeśli w *zestawie A* istnieją setki typów, które chcesz udostępnić <xref:System.Security.Permissions.StrongNameIdentityPermission> *zestawowi B,* należy dodać je wszystkie.</span><span class="sxs-lookup"><span data-stu-id="03b62-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="03b62-130">Jeśli używasz zestawu znajomych, wystarczy zadeklarować relację przyjaciela tylko raz.</span><span class="sxs-lookup"><span data-stu-id="03b62-130">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="03b62-131">Jeśli używasz, <xref:System.Security.Permissions.StrongNameIdentityPermission>typy, które chcesz udostępnić muszą być zadeklarowane jako publiczne.</span><span class="sxs-lookup"><span data-stu-id="03b62-131">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="03b62-132">Jeśli używasz zestawu znajomego, typy udostępnione `internal` są deklarowane `Friend` jako (C#) lub (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="03b62-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="03b62-133">Aby uzyskać informacje dotyczące uzyskiwania `internal` dostępu do `Friend` typów i metod zestawu (C#) lub (Visual Basic) z pliku modułu (pliku z rozszerzeniem *.netmodule),* zobacz [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) lub [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="03b62-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03b62-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03b62-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="03b62-135">Jak: Tworzenie niepodpisanych zestawów znajomych</span><span class="sxs-lookup"><span data-stu-id="03b62-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="03b62-136">Jak: Tworzenie podpisanych zestawów znajomych</span><span class="sxs-lookup"><span data-stu-id="03b62-136">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="03b62-137">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="03b62-137">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="03b62-138">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="03b62-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="03b62-139">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03b62-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
