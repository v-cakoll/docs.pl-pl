---
title: Przyjazne zestawy (C#)
ms.date: 07/20/2015
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: e8c295fe23685e39e20a14ff23139339f24564c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510088"
---
# <a name="friend-assemblies-c"></a><span data-ttu-id="5afa1-102">Przyjazne zestawy (C#)</span><span class="sxs-lookup"><span data-stu-id="5afa1-102">Friend Assemblies (C#)</span></span>
<span data-ttu-id="5afa1-103">A *przyjaznego zestawu* to zestaw, który mogą uzyskiwać dostęp do innego zestawu [wewnętrzny](../../../../csharp/language-reference/keywords/internal.md) typów i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5afa1-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../../../csharp/language-reference/keywords/internal.md) types and members.</span></span> <span data-ttu-id="5afa1-104">Po zidentyfikowaniu zestawu jako zestaw przyjazny, masz już Oznacz typy i elementy członkowskie jako publiczny je, aby były dostępne dla innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="5afa1-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="5afa1-105">Jest to szczególnie wygodne w następujących scenariuszach:</span><span class="sxs-lookup"><span data-stu-id="5afa1-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="5afa1-106">Podczas testowania jednostek, gdy kod testowy jest uruchamiany osobny zestaw ale wymaga dostępu do składowych w zestawie poddawana testom, które są oznaczone jako `internal` .</span><span class="sxs-lookup"><span data-stu-id="5afa1-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` .</span></span>  
  
-   <span data-ttu-id="5afa1-107">Podczas tworzenia biblioteki klas i ma zostać dodany do biblioteki znajdują się w osobnych zestawach, ale wymagają dostępu do elementów członkowskich w istniejących zestawów, które są oznaczone jako `internal` .</span><span class="sxs-lookup"><span data-stu-id="5afa1-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` .</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5afa1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5afa1-108">Remarks</span></span>  
 <span data-ttu-id="5afa1-109">Możesz użyć <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut do identyfikowania jeden lub więcej zestawów przyjaznego dla danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5afa1-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="5afa1-110">W poniższym przykładzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu w zestawie A i określa zestaw `AssemblyB` jako przyjaznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5afa1-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="5afa1-111">Dzięki temu zestaw `AssemblyB` dostęp do wszystkich typów i elementów członkowskich w zestawie, które są oznaczone jako `internal`.</span><span class="sxs-lookup"><span data-stu-id="5afa1-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5afa1-112">Gdy kompilujesz zestaw (zestaw `AssemblyB`) będzie uzyskiwać dostęp typy wewnętrzne lub wewnętrzne członków innego zestawu (zestaw *A*), należy jawnie określić nazwę pliku wyjściowego (.exe lub .dll), używając **/out** — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5afa1-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="5afa1-113">Jest to wymagane, ponieważ kompilator nie ma jeszcze wygenerować nazwę zestawu, który tworzysz w czasie, który jest wiązanie odwołań zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="5afa1-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="5afa1-114">Aby uzyskać więcej informacji, zobacz [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="5afa1-114">For more information, see [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .</span></span>  
  
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
  
 <span data-ttu-id="5afa1-115">Tylko zestawy, które zostaną jawnie określone, zgodnie z przyjaciółmi mogą uzyskiwać dostęp do `internal` typów i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5afa1-115">Only assemblies that you explicitly specify as friends can access `internal` types and members.</span></span> <span data-ttu-id="5afa1-116">Na przykład, jeśli zestaw B jest przyjaznego zestawu A i C zestawu odwołania do zestawu B, C nie ma dostępu do `internal` typów w A.</span><span class="sxs-lookup"><span data-stu-id="5afa1-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` types in A.</span></span>  
  
 <span data-ttu-id="5afa1-117">Kompilator wykonuje niektóre podstawowe sprawdzanie poprawności nazwy przyjaznego zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5afa1-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="5afa1-118">Jeśli zestaw *A* deklaruje *B* jako zestaw przyjaznych reguły sprawdzania poprawności są następujące:</span><span class="sxs-lookup"><span data-stu-id="5afa1-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="5afa1-119">Jeśli zestaw *A* jest silną nazwę zestawu *B* również musi mieć silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5afa1-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="5afa1-120">Nazwy przyjaznego zestawu, który jest przekazywany do atrybutu musi zawierać nazwę zestawu i klucz publiczny klucz silnej nazwy, który jest używany do podpisywania zestawu *B*.</span><span class="sxs-lookup"><span data-stu-id="5afa1-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="5afa1-121">Nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut nie może być silnej nazwy zestawu *B*: nie ma zestawu wersji, kultury, architektury lub token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="5afa1-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="5afa1-122">Jeśli zestaw *A* nie jest silną nazwę, nazwy przyjaznego zestawu powinna składać się wyłącznie nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="5afa1-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="5afa1-123">Aby uzyskać więcej informacji, zobacz [porady: tworzenie niepodpisane przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5afa1-123">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="5afa1-124">Jeśli zestaw *B* jest silną nazwę, należy określić klucz silnej nazwy zestawu *B* przy użyciu wiersza polecenia i ustawienie projektu `/keyfile` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5afa1-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="5afa1-125">Aby uzyskać więcej informacji, zobacz [porady: tworzenie podpisany przyjaznych zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5afa1-125">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="5afa1-126"><xref:System.Security.Permissions.StrongNameIdentityPermission> Klasa udostępnia także możliwość udostępniania typów, z następującymi różnicami:</span><span class="sxs-lookup"><span data-stu-id="5afa1-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="5afa1-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> ma zastosowanie do poszczególnych typu, gdy zestaw przyjazny, który ma zastosowanie do całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5afa1-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="5afa1-128">Jeśli istnieją setki typów w zestawie *A* , którą chcesz udostępnić zestawu *B*, trzeba dodać <xref:System.Security.Permissions.StrongNameIdentityPermission> do wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="5afa1-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="5afa1-129">Jeśli używasz zestaw przyjazny, wystarczy raz deklarowania relacji friend.</span><span class="sxs-lookup"><span data-stu-id="5afa1-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="5afa1-130">Jeśli używasz <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, które chcesz udostępnić musi być zadeklarowana jako publiczne.</span><span class="sxs-lookup"><span data-stu-id="5afa1-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="5afa1-131">Jeśli używasz zestaw przyjazny, udostępnione typy są deklarowane jako `internal`.</span><span class="sxs-lookup"><span data-stu-id="5afa1-131">If you use a friend assembly, the shared types are declared as `internal`.</span></span>  
  
 <span data-ttu-id="5afa1-132">Aby uzyskać informacje dotyczące dostępu do zestawu `internal` typów i metod z pliku modułu (plik z rozszerzeniem .netmodule), zobacz [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5afa1-132">For information about how to access an assembly's `internal` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5afa1-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5afa1-133">See Also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
- <xref:System.Security.Permissions.StrongNameIdentityPermission>  
- [<span data-ttu-id="5afa1-134">Porady: tworzenie nieoznaczonych przyjaznych zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="5afa1-134">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
- [<span data-ttu-id="5afa1-135">Porady: tworzenie oznaczonych przyjaznych zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="5afa1-135">How to: Create Signed Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
- [<span data-ttu-id="5afa1-136">Zestawy i Globalna pamięć podręczna zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="5afa1-136">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="5afa1-137">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5afa1-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
