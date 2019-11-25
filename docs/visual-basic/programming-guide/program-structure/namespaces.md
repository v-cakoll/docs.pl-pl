---
title: Namespaces
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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347332"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="1f9e2-102">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1f9e2-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="1f9e2-103">Namespaces organize the objects defined in an assembly.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="1f9e2-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="1f9e2-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="1f9e2-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1f9e2-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span><span class="sxs-lookup"><span data-stu-id="1f9e2-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="1f9e2-108">Avoiding Name Collisions</span><span class="sxs-lookup"><span data-stu-id="1f9e2-108">Avoiding Name Collisions</span></span>  
 <span data-ttu-id="1f9e2-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="1f9e2-110">These conflicts with existing components are sometimes called *name collisions*.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="1f9e2-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="1f9e2-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="1f9e2-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="1f9e2-114">The following code example demonstrates how to declare these objects:</span><span class="sxs-lookup"><span data-stu-id="1f9e2-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="1f9e2-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span><span class="sxs-lookup"><span data-stu-id="1f9e2-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![Screenshot that shows two namespace hierarchies.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="1f9e2-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="1f9e2-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="1f9e2-119">Multiple assemblies can use the same namespace.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="1f9e2-120">Visual Basic treats them as a single set of names.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="1f9e2-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="1f9e2-122">Fully Qualified Names</span><span class="sxs-lookup"><span data-stu-id="1f9e2-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="1f9e2-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="1f9e2-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="1f9e2-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span><span class="sxs-lookup"><span data-stu-id="1f9e2-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="1f9e2-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="1f9e2-127">However, the names themselves can get long and cumbersome.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="1f9e2-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="1f9e2-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="1f9e2-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="1f9e2-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="1f9e2-132">Suppose, for example, your project contained the following two `Imports` statements:</span><span class="sxs-lookup"><span data-stu-id="1f9e2-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="1f9e2-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="1f9e2-134">Namespace Level Statements</span><span class="sxs-lookup"><span data-stu-id="1f9e2-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="1f9e2-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="1f9e2-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="1f9e2-137">These items must be declared within containers such as modules, structures, or classes.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="1f9e2-138">Global Keyword in Fully Qualified Names</span><span class="sxs-lookup"><span data-stu-id="1f9e2-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="1f9e2-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="1f9e2-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="1f9e2-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="1f9e2-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="1f9e2-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="1f9e2-144">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="1f9e2-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="1f9e2-146">Global Keyword in Namespace Statements</span><span class="sxs-lookup"><span data-stu-id="1f9e2-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="1f9e2-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1f9e2-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="1f9e2-148">This lets you define a namespace out of the root namespace of your project.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="1f9e2-149">All namespaces in your project are based on the root namespace for the project.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="1f9e2-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="1f9e2-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="1f9e2-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="1f9e2-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="1f9e2-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="1f9e2-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="1f9e2-156">For new projects, the **Root Namespace** defaults to the project name.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="1f9e2-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="1f9e2-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="1f9e2-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="1f9e2-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="1f9e2-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="1f9e2-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="1f9e2-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span><span class="sxs-lookup"><span data-stu-id="1f9e2-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="1f9e2-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f9e2-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="1f9e2-165">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="1f9e2-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="1f9e2-166">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="1f9e2-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="1f9e2-167">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="1f9e2-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="1f9e2-168">Pisanie kodu dla rozwiązań pakietu Office</span><span class="sxs-lookup"><span data-stu-id="1f9e2-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
