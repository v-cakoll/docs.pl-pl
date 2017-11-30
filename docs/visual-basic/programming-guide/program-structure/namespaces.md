---
title: Przestrzenie nazw w Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.global
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
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c18d0a9abb1d8b9e3e22f3b81bf605fb8ed75cfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="4f8bb-102">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f8bb-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="4f8bb-103">Przestrzenie nazw organizowanie obiektów zdefiniowanych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="4f8bb-104">Zestawy może zawierać wiele obszarów nazw, który z kolei może zawierać innych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="4f8bb-105">Przestrzenie nazw uniknąć niejednoznaczności i uprościć odwołań w przypadku przy użyciu dużych grup obiektów, takich jak biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="4f8bb-106">Na przykład [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definiuje <xref:System.Windows.Forms.ListBox> klasy w <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-106">For example, the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4f8bb-107">Poniższy fragment kodu przedstawia sposób zadeklarować zmiennej przy użyciu w pełni kwalifikowana nazwa dla tej klasy:</span><span class="sxs-lookup"><span data-stu-id="4f8bb-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="4f8bb-108">Unikanie konfliktów nazw</span><span class="sxs-lookup"><span data-stu-id="4f8bb-108">Avoiding Name Collisions</span></span>  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]<span data-ttu-id="4f8bb-109">przestrzenie nazw rozwiązać problem czasami nazywane *zanieczyszczenie przestrzeni nazw*, w którym dewelopera biblioteki klas jest utrudniona przez stosowanie podobnych nazw w innej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-109"> namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="4f8bb-110">Te konflikty z istniejącymi elementami są nazywane *kolizji nazw*.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="4f8bb-111">Na przykład, jeśli tworzysz nową klasę o nazwie `ListBox`, może być używany w projekcie bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="4f8bb-112">Jednak jeśli chcesz użyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> klasy w tym samym projekcie, aby odnieść unikatowy należy użyć pełni kwalifikowane odwołanie.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-112">However, if you want to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="4f8bb-113">Jeśli odwołanie nie jest unikatowa, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tworzy komunikat o błędzie informujący, że nazwa jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-113">If the reference is not unique, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="4f8bb-114">Poniższy przykładowy kod przedstawia sposób zadeklarować tych obiektów:</span><span class="sxs-lookup"><span data-stu-id="4f8bb-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 <span data-ttu-id="4f8bb-115">Na poniższej ilustracji przedstawiono dwie hierarchie przestrzeni nazw, w obu zawierający obiekt o nazwie `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`.</span></span>  
  
 <span data-ttu-id="4f8bb-116">![Hierarchia Namespace](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span><span class="sxs-lookup"><span data-stu-id="4f8bb-116">![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span></span>  
  
 <span data-ttu-id="4f8bb-117">Domyślnie każdy plik wykonywalny utworzyć z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zawiera obszarze nazw o nazwie identycznej z nazwą projektu.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-117">By default, every executable file you create with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] contains a namespace with the same name as your project.</span></span> <span data-ttu-id="4f8bb-118">Na przykład, jeśli zdefiniowania obiektu, w ramach projektu o nazwie `ListBoxProject`, plik wykonywalny ListBoxProject.exe zawiera obszar nazw o nazwie `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="4f8bb-119">Wiele zestawów można użyć tego samego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-119">Multiple assemblies can use the same namespace.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="4f8bb-120">traktuje je jako pojedynczy zestaw nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-120"> treats them as a single set of names.</span></span> <span data-ttu-id="4f8bb-121">Na przykład można zdefiniować klasy dla przestrzeni nazw o nazwie `SomeNameSpace` w zestawie o nazwie `Assemb1`i zdefiniować dodatkowe klasy dla tego samego obszaru nazw z zestawu o nazwie `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="4f8bb-122">W pełni kwalifikowane nazwy</span><span class="sxs-lookup"><span data-stu-id="4f8bb-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="4f8bb-123">W pełni kwalifikowane nazwy są odwołania do obiektów, które są poprzedzane prefiksem nazwy przestrzeni nazw, w którym zdefiniowana jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="4f8bb-124">Można użyć obiektów zdefiniowanych w innych projektach, jeśli utworzono odwołanie do klasy (przez wybranie **Dodaj odwołanie** z **projektu** menu), a następnie użyj w pełni kwalifikowana nazwa obiektu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="4f8bb-125">Poniższy fragment kodu przedstawia sposób użycia w pełni kwalifikowana nazwa obiektu z innego projektu przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="4f8bb-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 <span data-ttu-id="4f8bb-126">W pełni kwalifikowane nazwy zapobiec nazw powoduje konflikt, ponieważ są one umożliwiać kompilator, aby określić obiektu, który jest w użyciu.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="4f8bb-127">Jednak nazwy można uzyskać długich i skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="4f8bb-128">Aby uzyskać obejścia tego problemu, można użyć `Imports` instrukcji, aby zdefiniować *alias*— skróconą nazwę można użyć zamiast w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="4f8bb-129">Na przykład poniższy przykład kodu tworzy aliasów dla dwóch w pełni kwalifikowane nazwy i używa tych aliasy, aby zdefiniować dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 <span data-ttu-id="4f8bb-130">Jeśli używasz `Imports` instrukcji bez aliasu, można używać wszystkich nazw w tej przestrzeni nazw bez kwalifikacji, podane, są one unikatowe do projektu.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="4f8bb-131">Jeśli projekt zawiera `Imports` instrukcje dla przestrzeni nazw, która zawiera elementy o takiej samej nazwie, użytkownik musi pełnej nazwy tego przypadku użycia jej.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="4f8bb-132">Załóżmy na przykład projekt zawiera dwa `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="4f8bb-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 <span data-ttu-id="4f8bb-133">Jeśli próba użycia `Class1` bez pełni kwalifikujące, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tworzy komunikat o błędzie informujący, że nazwa `Class1` jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-133">If you attempt to use `Class1` without fully qualifying it, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="4f8bb-134">Poziom Namespace — instrukcje</span><span class="sxs-lookup"><span data-stu-id="4f8bb-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="4f8bb-135">W obszarze nazw należy zdefiniować elementy, takie jak moduły, interfejsów, klas, obiektów delegowanych, wyliczeń, struktur i innych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="4f8bb-136">Nie można zdefiniować elementy, takie jak właściwości, procedur, zmiennych i zdarzenia na poziomie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="4f8bb-137">Te elementy muszą być zadeklarowane w kontenerach, takich jak moduły, struktury lub klasy.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="4f8bb-138">Global — słowo kluczowe w pełni kwalifikowane nazwy</span><span class="sxs-lookup"><span data-stu-id="4f8bb-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="4f8bb-139">Jeśli zdefiniowano hierarchii zagnieżdżonych obszarów nazw kodu wewnątrz tej hierarchii może zostać zablokowany dostęp do <xref:System?displayProperty=nameWithType> przestrzeni nazw programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="4f8bb-140">Poniższy przykład przedstawia hierarchię, w którym `SpecialSpace.System` przestrzeni nazw zablokuje dostęp do <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="4f8bb-141">W związku z tym kompilator Visual Basic nie można rozpoznać odwołania do <xref:System.Int32?displayProperty=nameWithType>, ponieważ `SpecialSpace.System` nie definiuje `Int32`.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="4f8bb-142">Można użyć `Global` — słowo kluczowe, aby uruchomić łańcucha kwalifikacji na poziomie najbardziej zewnętrznego w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="4f8bb-143">Dzięki temu można określić <xref:System?displayProperty=nameWithType> przestrzeni nazw lub innych przestrzeni nazw w bibliotece klas.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="4f8bb-144">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="4f8bb-145">Można użyć `Global` można uzyskać dostępu do innych przestrzeniach nazw poziomu głównego, takich jak <xref:Microsoft.VisualBasic?displayProperty=nameWithType>i skojarzone z projektu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="4f8bb-146">Global — słowo kluczowe w instrukcjach "Namespace"</span><span class="sxs-lookup"><span data-stu-id="4f8bb-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="4f8bb-147">Można również użyć `Global` — słowo kluczowe w [instrukcji Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4f8bb-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="4f8bb-148">Dzięki temu można zdefiniować przestrzeni nazw poza głównej przestrzeni nazw projektu.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="4f8bb-149">Wszystkie przestrzenie nazw w projekcie są oparte na przestrzeń nazw korzenia dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="4f8bb-150">Visual Studio przypisuje nazwę projektu jako domyślną przestrzeń nazw głównego dla całego kodu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="4f8bb-151">Na przykład, jeśli nosi nazwę projektu `ConsoleApplication1`, jego element programistyczny należy do przestrzeni nazw `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="4f8bb-152">W przypadku `Namespace Magnetosphere`, odwołuje się do `Magnetosphere` w projekcie będą uzyskiwać dostęp do `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="4f8bb-153">W poniższych przykładach użyto `Global` — słowo kluczowe, aby zadeklarować przestrzeni nazw poza głównej przestrzeni nazw dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 <span data-ttu-id="4f8bb-154">W deklaracji przestrzeni nazw `Global` nie mogą być zagnieżdżone w innej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="4f8bb-155">Można użyć [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) do wyświetlania i modyfikowania **Namespace głównego** projektu.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="4f8bb-156">Dla nowych projektów **Namespace głównego** domyślnie nazwa projektu.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="4f8bb-157">Powoduje `Global` się przestrzeni nazw najwyższego poziomu, można wyczyścić **Namespace głównego** wpis tak, że pole jest puste.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="4f8bb-158">Wyczyszczenie **Namespace głównego** eliminuje to potrzebę `Global` — słowo kluczowe w deklaracjach przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="4f8bb-159">Jeśli `Namespace` instrukcji deklaruje nazwę, która jest również przestrzeni nazw w programie .NET Framework, obszaru nazw .NET Framework jest niedostępny Jeśli `Global` — słowo kluczowe nie jest używany w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="4f8bb-160">Aby umożliwić dostęp do tego obszaru nazw .NET Framework bez użycia `Global` — słowo kluczowe, mogą obejmować `Global` — słowo kluczowe w `Namespace` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="4f8bb-161">W poniższym przykładzie przedstawiono `Global` — słowo kluczowe w `System.Text` deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="4f8bb-162">Jeśli `Global` — słowo kluczowe nie była obecna w deklaracji przestrzeni nazw <xref:System.Text.StringBuilder> nie było możliwe bez określania `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="4f8bb-163">Dla projektu o nazwie `ConsoleApplication1`, odwołuje się do `System.Text` może uzyskać dostępu do `ConsoleApplication1.System.Text` Jeśli `Global` nie użyto słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="4f8bb-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4f8bb-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f8bb-164">See Also</span></span>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
 [<span data-ttu-id="4f8bb-165">Zestawy i Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="4f8bb-165">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="4f8bb-166">Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="4f8bb-166">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="4f8bb-167">Referencje i Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="4f8bb-167">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="4f8bb-168">Imports — instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="4f8bb-168">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="4f8bb-169">Pisanie kodu dla rozwiązań pakietu Office</span><span class="sxs-lookup"><span data-stu-id="4f8bb-169">Writing Code in Office Solutions</span></span>](https://msdn.microsoft.com/library/bb608596)
