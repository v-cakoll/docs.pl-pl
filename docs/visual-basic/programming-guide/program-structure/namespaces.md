---
title: Przestrzenie nazw
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: 087c6f02e1fca9cf2664ca76581c08a9b1a5e447
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398360"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="06454-102">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06454-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="06454-103">Przestrzenie nazw organizują obiekty zdefiniowane w zestawie.</span><span class="sxs-lookup"><span data-stu-id="06454-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="06454-104">Zestawy mogą zawierać wiele przestrzeni nazw, które mogą z kolei zawierać inne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="06454-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="06454-105">Przestrzenie nazw uniemożliwiają niejednoznaczność i upraszczają odwołania w przypadku używania dużych grup obiektów, takich jak biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="06454-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="06454-106">Na przykład .NET Framework definiuje <xref:System.Windows.Forms.ListBox> klasę w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06454-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="06454-107">Poniższy fragment kodu przedstawia sposób deklarowania zmiennej przy użyciu w pełni kwalifikowanej nazwy dla tej klasy:</span><span class="sxs-lookup"><span data-stu-id="06454-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="06454-108">Unikanie kolizji nazw</span><span class="sxs-lookup"><span data-stu-id="06454-108">Avoiding Name Collisions</span></span>  
 <span data-ttu-id="06454-109">Przestrzenie nazw .NET Framework rozwiązaniu problemu czasami nazywanego *zanieczyszczeniem przestrzeni nazw*, w którym deweloper biblioteki klas jest niehamowany przez użycie podobnych nazw w innej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="06454-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="06454-110">Te konflikty z istniejącymi składnikami są czasami nazywane *kolizjami nazw*.</span><span class="sxs-lookup"><span data-stu-id="06454-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="06454-111">Na przykład jeśli utworzysz nową klasę o nazwie, możesz `ListBox` jej użyć w projekcie bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="06454-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="06454-112">Jeśli jednak chcesz użyć <xref:System.Windows.Forms.ListBox> klasy .NET Framework w tym samym projekcie, musisz użyć w pełni kwalifikowanego odwołania, aby odwołać odwołanie.</span><span class="sxs-lookup"><span data-stu-id="06454-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="06454-113">Jeśli odwołanie nie jest unikatowe, Visual Basic generuje błąd informujący o tym, że nazwa jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="06454-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="06454-114">Poniższy przykład kodu demonstruje, jak zadeklarować te obiekty:</span><span class="sxs-lookup"><span data-stu-id="06454-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="06454-115">Na poniższej ilustracji przedstawiono dwie hierarchie przestrzeni nazw, które zawierają obiekt o nazwie `ListBox` :</span><span class="sxs-lookup"><span data-stu-id="06454-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![Zrzut ekranu pokazujący dwie hierarchie przestrzeni nazw.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="06454-117">Domyślnie każdy plik wykonywalny tworzony za pomocą Visual Basic zawiera przestrzeń nazw o tej samej nazwie co projekt.</span><span class="sxs-lookup"><span data-stu-id="06454-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="06454-118">Na przykład, jeśli zdefiniujesz obiekt w projekcie o nazwie `ListBoxProject` , plik wykonywalny ListBoxProject. exe zawiera przestrzeń nazw o nazwie `ListBoxProject` .</span><span class="sxs-lookup"><span data-stu-id="06454-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="06454-119">Wiele zestawów może używać tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06454-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="06454-120">Visual Basic traktuje je jako pojedynczy zestaw nazw.</span><span class="sxs-lookup"><span data-stu-id="06454-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="06454-121">Na przykład można zdefiniować klasy dla przestrzeni nazw o nazwie `SomeNameSpace` w zestawie o nazwie `Assemb1` i zdefiniować dodatkowe klasy dla tej samej przestrzeni nazw z zestawu o nazwie `Assemb2` .</span><span class="sxs-lookup"><span data-stu-id="06454-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="06454-122">W pełni kwalifikowane nazwy</span><span class="sxs-lookup"><span data-stu-id="06454-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="06454-123">W pełni kwalifikowane nazwy są odwołaniami do obiektów, które są poprzedzone nazwą przestrzeni nazw, w której jest zdefiniowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="06454-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="06454-124">Możesz użyć obiektów zdefiniowanych w innych projektach, jeśli utworzysz odwołanie do klasy (wybierając **Dodaj odwołanie** z menu **projekt** ), a następnie użyj w pełni kwalifikowanej nazwy dla obiektu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="06454-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="06454-125">Poniższy fragment kodu pokazuje, jak używać w pełni kwalifikowanej nazwy dla obiektu z przestrzeni nazw innego projektu:</span><span class="sxs-lookup"><span data-stu-id="06454-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="06454-126">W pełni kwalifikowane nazwy uniemożliwiają konflikty nazw, ponieważ umożliwiają kompilatorowi określenie, który obiekt jest używany.</span><span class="sxs-lookup"><span data-stu-id="06454-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="06454-127">Nazwy same mogą jednak być długie i nieskomplikowane.</span><span class="sxs-lookup"><span data-stu-id="06454-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="06454-128">Aby to zrobić, można użyć `Imports` instrukcji w celu zdefiniowania *aliasu*— skróconej nazwy, której można użyć zamiast w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="06454-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="06454-129">Poniższy przykład kodu tworzy aliasy dla dwóch w pełni kwalifikowanych nazw i używa tych aliasów do definiowania dwóch obiektów.</span><span class="sxs-lookup"><span data-stu-id="06454-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="06454-130">Jeśli używasz `Imports` instrukcji bez aliasu, możesz użyć wszystkich nazw w tej przestrzeni nazw bez kwalifikacji, pod warunkiem, że są one unikatowe dla projektu.</span><span class="sxs-lookup"><span data-stu-id="06454-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="06454-131">Jeśli projekt zawiera `Imports` instrukcje dla przestrzeni nazw, które zawierają elementy o tej samej nazwie, należy w pełni zakwalifikować tę nazwę podczas korzystania z niej.</span><span class="sxs-lookup"><span data-stu-id="06454-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="06454-132">Załóżmy na przykład, że projekt zawiera następujące dwie `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="06454-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="06454-133">Jeśli próba użycia nie zostanie w `Class1` pełni zakwalifikowania, Visual Basic generuje błąd informujący o tym, że nazwa `Class1` jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="06454-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="06454-134">Instrukcje na poziomie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="06454-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="06454-135">W przestrzeni nazw można definiować elementy, takie jak moduły, interfejsy, klasy, Delegaty, wyliczenia, struktury i inne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="06454-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="06454-136">Nie można definiować elementów, takich jak właściwości, procedury, zmienne i zdarzenia, na poziomie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06454-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="06454-137">Te elementy muszą być zadeklarowane w kontenerach, takich jak moduły, struktury lub klasy.</span><span class="sxs-lookup"><span data-stu-id="06454-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="06454-138">Globalne słowo kluczowe w w pełni kwalifikowanych nazwach</span><span class="sxs-lookup"><span data-stu-id="06454-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="06454-139">Jeśli zdefiniowano hierarchię zagnieżdżoną przestrzeni nazw, kod wewnątrz tej hierarchii może mieć zablokowany dostęp do <xref:System?displayProperty=nameWithType> przestrzeni nazw .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06454-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="06454-140">Poniższy przykład ilustruje hierarchię, w której `SpecialSpace.System` przestrzeń nazw blokuje dostęp do <xref:System?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="06454-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="06454-141">W związku z tym kompilator Visual Basic nie może pomyślnie rozpoznać odwołania do <xref:System.Int32?displayProperty=nameWithType> , ponieważ nie `SpecialSpace.System` definiuje `Int32` .</span><span class="sxs-lookup"><span data-stu-id="06454-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="06454-142">Możesz użyć `Global` słowa kluczowego do uruchomienia łańcucha kwalifikacji na najbardziej zewnętrznym poziomie biblioteki klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06454-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="06454-143">Pozwala to określić <xref:System?displayProperty=nameWithType> przestrzeń nazw lub inną przestrzeń nazw w bibliotece klas.</span><span class="sxs-lookup"><span data-stu-id="06454-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="06454-144">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="06454-144">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="06454-145">Można użyć, `Global` Aby uzyskać dostęp do innych obszarów nazw na poziomie głównym, takich jak <xref:Microsoft.VisualBasic?displayProperty=nameWithType> i wszystkich przestrzeni nazw skojarzonych z projektem.</span><span class="sxs-lookup"><span data-stu-id="06454-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="06454-146">Globalne słowo kluczowe w instrukcjach Namespace</span><span class="sxs-lookup"><span data-stu-id="06454-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="06454-147">Możesz również użyć `Global` słowa kluczowego w [instrukcji Namespace](../../language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="06454-147">You can also use the `Global` keyword in a [Namespace Statement](../../language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="06454-148">Pozwala to definiować przestrzeń nazw poza główną przestrzenią nazw projektu.</span><span class="sxs-lookup"><span data-stu-id="06454-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="06454-149">Wszystkie przestrzenie nazw w projekcie są oparte na głównej przestrzeni nazw dla projektu.</span><span class="sxs-lookup"><span data-stu-id="06454-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="06454-150">Program Visual Studio przypisuje nazwę projektu jako domyślną główną przestrzeń nazw dla całego kodu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="06454-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="06454-151">Na przykład jeśli projekt ma nazwę `ConsoleApplication1` , jego elementy programistyczne należą do przestrzeni nazw `ConsoleApplication1` .</span><span class="sxs-lookup"><span data-stu-id="06454-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="06454-152">Jeśli zadeklarujesz `Namespace Magnetosphere` , odwołania do `Magnetosphere` w projekcie będą miały dostęp `ConsoleApplication1.Magnetosphere` .</span><span class="sxs-lookup"><span data-stu-id="06454-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="06454-153">W poniższych przykładach użyto `Global` słowa kluczowego, aby zadeklarować przestrzeń nazw poza główną przestrzeń nazw dla projektu.</span><span class="sxs-lookup"><span data-stu-id="06454-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="06454-154">W deklaracji przestrzeni nazw `Global` nie może być zagnieżdżona w innej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06454-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="06454-155">Za pomocą [strony aplikacji, projektanta projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) można wyświetlać i modyfikować **główną przestrzeń nazw** projektu.</span><span class="sxs-lookup"><span data-stu-id="06454-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="06454-156">W przypadku nowych projektów, **główna przestrzeń nazw** domyślnie jest nazwą projektu.</span><span class="sxs-lookup"><span data-stu-id="06454-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="06454-157">Aby `Global` można było uzyskać przestrzeń nazw najwyższego poziomu, można wyczyścić wpis **głównej przestrzeni nazw** , aby pole było puste.</span><span class="sxs-lookup"><span data-stu-id="06454-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="06454-158">Czyszczenie **głównej przestrzeni nazw** usuwa potrzebę `Global` słowa kluczowego w deklaracjach przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06454-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="06454-159">Jeśli `Namespace` instrukcja deklaruje nazwę, która jest również przestrzenią nazw w .NET Framework, przestrzeń nazw .NET Framework będzie niedostępna, jeśli `Global` słowo kluczowe nie zostanie użyte w w pełni kwalifikowanej nazwie.</span><span class="sxs-lookup"><span data-stu-id="06454-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="06454-160">Aby umożliwić dostęp do tego .NET Framework przestrzeni nazw bez użycia `Global` słowa kluczowego, można dołączyć `Global` słowo kluczowe do `Namespace` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="06454-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="06454-161">Poniższy przykład zawiera `Global` słowo kluczowe w `System.Text` deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06454-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="06454-162">Jeśli `Global` słowo kluczowe nie było obecne w deklaracji przestrzeni nazw, nie można <xref:System.Text.StringBuilder> uzyskać do niego dostępu bez określenia `Global.System.Text.StringBuilder` .</span><span class="sxs-lookup"><span data-stu-id="06454-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="06454-163">Dla projektu o nazwie `ConsoleApplication1` odwołuje się do `System.Text` niego, `ConsoleApplication1.System.Text` Jeśli `Global` słowo kluczowe nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="06454-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="06454-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06454-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="06454-165">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="06454-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="06454-166">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="06454-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="06454-167">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="06454-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="06454-168">Pisanie kodu dla rozwiązań pakietu Office</span><span class="sxs-lookup"><span data-stu-id="06454-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
