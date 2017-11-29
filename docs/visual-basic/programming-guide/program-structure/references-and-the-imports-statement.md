---
title: "Referencje i importy — Instrukcja (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 739934b65241a7846b5323d5e75446832d83e5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="ae8b9-102">Referencje i importy — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8b9-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="ae8b9-103">Można udostępnić obiektów zewnętrznych do projektu, wybierając **Dodaj odwołanie** na **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="ae8b9-104">Odwołania w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] może wskazywać na zestawy, które są takie jak biblioteki typów, ale zawierają więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-104">References in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="ae8b9-105">Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ae8b9-105">The Imports Statement</span></span>  
 <span data-ttu-id="ae8b9-106">Zestawy zawiera jeden lub kilka przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="ae8b9-107">Podczas dodawania odwołania do zestawu, możesz także dodać `Imports` instrukcji, aby moduł, który określa widoczność nazw tego zestawu w module.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="ae8b9-108">`Imports` Instrukcji zapewnia zakresu kontekstu, która umożliwia używanie tylko części obszaru nazw, które są niezbędne do dostarczania unikatowe odwołanie.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="ae8b9-109">`Imports` Instrukcji ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="ae8b9-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="ae8b9-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="ae8b9-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="ae8b9-111">`Aliasname`odnosi się do krótkiej nazwy, używanych w ramach kodu do odwoływania się do importowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="ae8b9-112">`Namespace`jest dostępna za pośrednictwem jednej przestrzeni nazw odwołanie do projektu, za pośrednictwem definicji w projekcie, lub poprzedniej `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="ae8b9-113">Moduł może zawierać dowolną liczbę `Imports` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="ae8b9-114">Muszą występować po jednej `Option` instrukcje, jeśli nie istnieje, ale przed innymi kodu.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae8b9-115">Nie należy mylić odwołania do projektu z `Imports` instrukcji lub `Declare` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="ae8b9-116">Odwołania do projektu udostępnić zewnętrznych obiektów, takich jak obiekty w zestawach, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projektów.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-116">Project references make external objects, such as objects in assemblies, available to [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projects.</span></span> <span data-ttu-id="ae8b9-117">`Imports` Instrukcja jest używane w celu uproszczenia dostępu do odwołania do projektu, ale nie zapewnia dostępu do tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="ae8b9-118">`Declare` Instrukcji służy do deklarowania odwołanie do zewnętrznej procedury biblioteki dołączanej (dynamicznie DLL).</span><span class="sxs-lookup"><span data-stu-id="ae8b9-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="ae8b9-119">Aliasy użycia z Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ae8b9-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="ae8b9-120">`Imports` Instrukcji ułatwia metody dostępu do klasy, eliminując konieczność jawnie wpisz w pełni kwalifikowane nazwy odwołań.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="ae8b9-121">Aliasy umożliwiają przypisać nazwę służący do tylko jednej części obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="ae8b9-122">Na przykład sekwencji, który powoduje, że jeden fragment tekstu do wyświetlenia w wielu wierszach CR/LF jest częścią <xref:Microsoft.VisualBasic.ControlChars> modułu w <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ae8b9-123">Aby użyć tego stała w programie bez aliasu, konieczne będzie wpisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="ae8b9-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="ae8b9-124">`Imports`instrukcje musi być zawsze pierwszych wierszy bezpośrednio po żadnego `Option` instrukcji w module.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="ae8b9-125">Poniższy fragment kodu przedstawia sposób importowania i przypisać aliasu <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modułu:</span><span class="sxs-lookup"><span data-stu-id="ae8b9-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="ae8b9-126">Odwołania do tej przestrzeni nazw może być znacznie krótszy:</span><span class="sxs-lookup"><span data-stu-id="ae8b9-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="ae8b9-127">Jeśli `Imports` instrukcji nie zawiera nazwę aliasu, elementy zdefiniowane w importowanych przestrzeni nazw może być używany w module bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="ae8b9-128">Jeśli zostanie określona nazwa aliasu, należy użyć jako kwalifikator dla nazw zawartych w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ae8b9-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae8b9-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae8b9-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
 [<span data-ttu-id="ae8b9-130">NIB porady: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="ae8b9-130">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="ae8b9-131">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae8b9-131">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="ae8b9-132">Zestawy i Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="ae8b9-132">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="ae8b9-133">Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ae8b9-133">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="ae8b9-134">Imports — instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="ae8b9-134">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
