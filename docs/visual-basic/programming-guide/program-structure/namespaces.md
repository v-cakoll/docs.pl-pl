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
ms.openlocfilehash: ec892167f30a7ded739dc188ab4096cb3a5d154c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400674"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="46a01-102">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46a01-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="46a01-103">Przestrzenie nazw organizują obiekty zdefiniowane w złożeniu.</span><span class="sxs-lookup"><span data-stu-id="46a01-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="46a01-104">Zestawy mogą zawierać wiele obszarów nazw, które z kolei mogą zawierać inne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="46a01-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="46a01-105">Przestrzenie nazw zapobiegają niejednoznaczności i upraszczają odwołania podczas korzystania z dużych grup obiektów, takich jak biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="46a01-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="46a01-106">Na przykład .NET Framework definiuje <xref:System.Windows.Forms.ListBox> klasę <xref:System.Windows.Forms?displayProperty=nameWithType> w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="46a01-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="46a01-107">Poniższy fragment kodu pokazuje, jak zadeklarować zmienną przy użyciu w pełni kwalifikowanej nazwy dla tej klasy:</span><span class="sxs-lookup"><span data-stu-id="46a01-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="46a01-108">Unikanie kolizji nazw</span><span class="sxs-lookup"><span data-stu-id="46a01-108">Avoiding Name Collisions</span></span>  
 <span data-ttu-id="46a01-109">.NET Framework przestrzenie nazw rozwiązać problem czasami nazywany *zanieczyszczenia obszaru nazw,* w którym deweloper biblioteki klas jest utrudniony przez użycie podobnych nazw w innej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="46a01-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="46a01-110">Te konflikty z istniejącymi komponentami są czasami nazywane *kolizjami nazw*.</span><span class="sxs-lookup"><span data-stu-id="46a01-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="46a01-111">Na przykład jeśli utworzysz `ListBox`nową klasę o nazwie , można jej używać wewnątrz projektu bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="46a01-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="46a01-112">Jednak jeśli chcesz użyć klasy .NET Framework <xref:System.Windows.Forms.ListBox> w tym samym projekcie, należy użyć w pełni kwalifikowanego odwołania, aby odwołanie było unikatowe.</span><span class="sxs-lookup"><span data-stu-id="46a01-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="46a01-113">Jeśli odwołanie nie jest unikatowe, visual basic generuje błąd stwierdzający, że nazwa jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="46a01-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="46a01-114">Poniższy przykład kodu pokazuje, jak zadeklarować te obiekty:</span><span class="sxs-lookup"><span data-stu-id="46a01-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="46a01-115">Na poniższej ilustracji przedstawiono dwie hierarchie `ListBox`obszarów nazw, oba zawierające obiekt o nazwie:</span><span class="sxs-lookup"><span data-stu-id="46a01-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![Zrzut ekranu przedstawiający dwie hierarchie obszaru nazw.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="46a01-117">Domyślnie każdy plik wykonywalny utworzony za pomocą języka Visual Basic zawiera obszar nazw o takiej samej nazwie jak projekt.</span><span class="sxs-lookup"><span data-stu-id="46a01-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="46a01-118">Na przykład, jeśli zdefiniujesz `ListBoxProject`obiekt w projekcie o nazwie , plik wykonywalny ListBoxProject.exe zawiera obszar nazw o nazwie `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="46a01-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="46a01-119">Wiele zestawów można użyć tego samego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="46a01-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="46a01-120">Visual Basic traktuje je jako pojedynczy zestaw nazw.</span><span class="sxs-lookup"><span data-stu-id="46a01-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="46a01-121">Na przykład można zdefiniować klasy dla `SomeNameSpace` obszaru nazw `Assemb1`wywoływanego w zestawie o nazwie i `Assemb2`zdefiniować dodatkowe klasy dla tego samego obszaru nazw z zestawu o nazwie .</span><span class="sxs-lookup"><span data-stu-id="46a01-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="46a01-122">W pełni kwalifikowane nazwy</span><span class="sxs-lookup"><span data-stu-id="46a01-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="46a01-123">W pełni kwalifikowane nazwy to odwołania do obiektów, które są poprzedzone nazwą obszaru nazw, w którym obiekt jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="46a01-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="46a01-124">Można użyć obiektów zdefiniowanych w innych projektach, jeśli utworzysz odwołanie do klasy (wybierając **dodaj odwołanie** z menu **Projekt),** a następnie użyj w pełni kwalifikowanej nazwy obiektu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="46a01-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="46a01-125">Poniższy fragment kodu pokazuje, jak używać w pełni kwalifikowanej nazwy obiektu z obszaru nazw innego projektu:</span><span class="sxs-lookup"><span data-stu-id="46a01-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="46a01-126">W pełni kwalifikowane nazwy zapobiegają konfliktom nazewnictwa, ponieważ umożliwiają kompilatorowi określenie, który obiekt jest używany.</span><span class="sxs-lookup"><span data-stu-id="46a01-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="46a01-127">Jednak same nazwy mogą stać się długie i uciążliwe.</span><span class="sxs-lookup"><span data-stu-id="46a01-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="46a01-128">Aby obejść ten problem, `Imports` można użyć instrukcji do zdefiniowania *aliasu*— skróconej nazwy, której można użyć zamiast w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="46a01-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="46a01-129">Na przykład poniższy przykład kodu tworzy aliasy dla dwóch w pełni kwalifikowanych nazw i używa tych aliasów do definiowania dwóch obiektów.</span><span class="sxs-lookup"><span data-stu-id="46a01-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="46a01-130">Jeśli używasz `Imports` instrukcji bez aliasu, można użyć wszystkich nazw w tym obszarze nazw bez kwalifikacji, pod warunkiem, że są unikatowe dla projektu.</span><span class="sxs-lookup"><span data-stu-id="46a01-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="46a01-131">Jeśli projekt `Imports` zawiera instrukcje dla obszarów nazw, które zawierają elementy o tej samej nazwie, należy w pełni zakwalifikować tę nazwę podczas korzystania z niej.</span><span class="sxs-lookup"><span data-stu-id="46a01-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="46a01-132">Załóżmy, że na przykład projekt `Imports` zawierał następujące dwie instrukcje:</span><span class="sxs-lookup"><span data-stu-id="46a01-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="46a01-133">Jeśli spróbujesz `Class1` użyć bez pełnego zakwalifikowania go, Visual Basic `Class1` generuje błąd stwierdzający, że nazwa jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="46a01-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="46a01-134">Instrukcje poziomu obszaru nazw</span><span class="sxs-lookup"><span data-stu-id="46a01-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="46a01-135">W obszarze nazw można definiować elementy, takie jak moduły, interfejsy, klasy, delegatów, wyliczenia, struktury i inne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="46a01-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="46a01-136">Nie można definiować elementów, takich jak właściwości, procedury, zmienne i zdarzenia na poziomie obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="46a01-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="46a01-137">Te elementy muszą być zadeklarowane w kontenerach, takich jak moduły, struktury lub klasy.</span><span class="sxs-lookup"><span data-stu-id="46a01-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="46a01-138">Globalne słowo kluczowe w pełni kwalifikowanych nazwach</span><span class="sxs-lookup"><span data-stu-id="46a01-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="46a01-139">Jeśli zdefiniowano zagnieżdżoną hierarchię obszarów nazw, kod wewnątrz tej <xref:System?displayProperty=nameWithType> hierarchii może być zablokowany w dostępie do obszaru nazw programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46a01-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="46a01-140">Poniższy przykład ilustruje hierarchię, `SpecialSpace.System` w której <xref:System?displayProperty=nameWithType>obszar nazw blokuje dostęp do .</span><span class="sxs-lookup"><span data-stu-id="46a01-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="46a01-141">W rezultacie kompilator języka Visual Basic nie <xref:System.Int32?displayProperty=nameWithType>może `SpecialSpace.System` pomyślnie `Int32`rozpoznać odwołania do programu , ponieważ nie definiuje .</span><span class="sxs-lookup"><span data-stu-id="46a01-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="46a01-142">Za pomocą `Global` słowa kluczowego można uruchomić łańcuch kwalifikacji na najbardziej wysuniętym na zewnątrz poziomie biblioteki klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46a01-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="46a01-143">Dzięki temu można <xref:System?displayProperty=nameWithType> określić obszar nazw lub inny obszar nazw w bibliotece klas.</span><span class="sxs-lookup"><span data-stu-id="46a01-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="46a01-144">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="46a01-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="46a01-145">Można użyć `Global` dostępu do innych głównych obszarów <xref:Microsoft.VisualBasic?displayProperty=nameWithType>nazw na poziomie, takich jak , i dowolnej przestrzeni nazw skojarzonej z projektem.</span><span class="sxs-lookup"><span data-stu-id="46a01-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="46a01-146">Globalne słowo kluczowe w instrukcjach obszaru nazw</span><span class="sxs-lookup"><span data-stu-id="46a01-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="46a01-147">Słowa kluczowego `Global` można również użyć w [instrukcji Obszar nazw](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="46a01-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="46a01-148">Dzięki temu można zdefiniować obszar nazw z głównej przestrzeni nazw projektu.</span><span class="sxs-lookup"><span data-stu-id="46a01-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="46a01-149">Wszystkie przestrzenie nazw w projekcie są oparte na głównej przestrzeni nazw projektu.</span><span class="sxs-lookup"><span data-stu-id="46a01-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="46a01-150">Visual Studio przypisuje nazwę projektu jako domyślną główną przestrzeń nazw dla całego kodu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="46a01-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="46a01-151">Na przykład, jeśli projekt `ConsoleApplication1`ma nazwę , jego `ConsoleApplication1`elementy programowania należą do obszaru nazw .</span><span class="sxs-lookup"><span data-stu-id="46a01-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="46a01-152">Jeśli `Namespace Magnetosphere`zadeklarujesz, `Magnetosphere` odwołania do `ConsoleApplication1.Magnetosphere`projektu będą uzyskiwać dostęp .</span><span class="sxs-lookup"><span data-stu-id="46a01-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="46a01-153">Poniższe przykłady `Global` używają słowa kluczowego do deklarowania obszaru nazw poza głównym obszarem nazw dla projektu.</span><span class="sxs-lookup"><span data-stu-id="46a01-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="46a01-154">W deklaracji obszaru `Global` nazw nie można zagnieżdżać w innej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46a01-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="46a01-155">Za pomocą [strony aplikacji, projektanta projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) można wyświetlić i zmodyfikować **główny obszar nazw** projektu.</span><span class="sxs-lookup"><span data-stu-id="46a01-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="46a01-156">W przypadku nowych projektów **główny obszar nazw** domyślnie nazywa się nazwą projektu.</span><span class="sxs-lookup"><span data-stu-id="46a01-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="46a01-157">Aby `Global` spowodować, że obszar nazw najwyższego poziomu, można wyczyścić wpis **głównego obszaru nazw,** tak aby pole było puste.</span><span class="sxs-lookup"><span data-stu-id="46a01-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="46a01-158">Wyczyszczenie **głównego obszaru** nazw `Global` eliminuje potrzebę słowa kluczowego w deklaracjach obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="46a01-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="46a01-159">Jeśli `Namespace` instrukcja deklaruje nazwę, która jest również obszar nazw w .NET Framework, .NET Framework obszar nazw staje się niedostępny, jeśli `Global` słowo kluczowe nie jest używany w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="46a01-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="46a01-160">Aby włączyć dostęp do tego obszaru nazw `Global` programu .NET `Global` Framework bez `Namespace` użycia słowa kluczowego, można dołączyć słowo kluczowe w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="46a01-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="46a01-161">Poniższy przykład `Global` ma słowo `System.Text` kluczowe w deklaracji obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="46a01-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="46a01-162">Jeśli `Global` słowo kluczowe nie było obecne <xref:System.Text.StringBuilder> w deklaracji obszaru nazw, `Global.System.Text.StringBuilder`nie można uzyskać dostępu bez określenia .</span><span class="sxs-lookup"><span data-stu-id="46a01-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="46a01-163">W przypadku `ConsoleApplication1`projektu o `System.Text` nazwie `ConsoleApplication1.System.Text` odwołania `Global` będą miały dostęp, jeśli słowo kluczowe nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="46a01-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="46a01-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46a01-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="46a01-165">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="46a01-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="46a01-166">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="46a01-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="46a01-167">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="46a01-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="46a01-168">Pisanie kodu dla rozwiązań pakietu Office</span><span class="sxs-lookup"><span data-stu-id="46a01-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
