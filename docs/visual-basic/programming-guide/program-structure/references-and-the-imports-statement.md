---
title: Referencje i importy — Instrukcja (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 89d360e5caa3cdb0dd1ecb985ea7ba727e5a6d9d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991067"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="a43fe-102">Referencje i importy — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a43fe-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="a43fe-103">Można udostępnić zewnętrznych obiektów do projektu, wybierając **Dodaj odwołanie** polecenie **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="a43fe-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="a43fe-104">Zestawy, które są podobne biblioteki typów, ale zawierają więcej informacji może wskazywać odwołania w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a43fe-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="a43fe-105">Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a43fe-105">The Imports Statement</span></span>  
 <span data-ttu-id="a43fe-106">Zestawy zawierają jeden lub kilka przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a43fe-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="a43fe-107">Po dodaniu odwołania do zestawu, można również dodać `Imports` instrukcję, aby moduł, który kontroluje widoczność tego zestawu przestrzeni nazw, w module.</span><span class="sxs-lookup"><span data-stu-id="a43fe-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="a43fe-108">`Imports` Instrukcja oferuje zakresu kontekstu, która umożliwia używanie tylko część obszaru nazw, trzeba podać unikatowy odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a43fe-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="a43fe-109">`Imports` Instrukcji ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="a43fe-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="a43fe-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="a43fe-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="a43fe-111">`Aliasname` odnosi się do krótką nazwę, których można użyć w kodzie, do odwoływania się do importowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a43fe-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="a43fe-112">`Namespace` jest dostępna za pośrednictwem jednej przestrzeni nazw odwołanie projektu za pomocą definicji w projekcie lub poprzedniej `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a43fe-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="a43fe-113">Moduł może zawierać dowolną liczbę `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a43fe-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="a43fe-114">Muszą występować po każdym `Option` instrukcji, jeśli jest obecny, ale przed innymi kodami.</span><span class="sxs-lookup"><span data-stu-id="a43fe-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a43fe-115">Nie należy mylić odwołania do projektu przy użyciu `Imports` instrukcji lub `Declare` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a43fe-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="a43fe-116">Odwołania do projektu udostępnić zewnętrzne obiekty, takie jak obiekty w zestawach, do projektów Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a43fe-116">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="a43fe-117">`Imports` Instrukcja jest używana, aby uprościć dostęp do odwołania do projektu, ale nie zapewnia dostępu do tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="a43fe-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="a43fe-118">`Declare` Instrukcja jest używana do zadeklarowania odwołania do zewnętrznej procedury biblioteki dołączanej (dynamicznie DLL).</span><span class="sxs-lookup"><span data-stu-id="a43fe-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="a43fe-119">Aliasy użycia za pomocą Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a43fe-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="a43fe-120">`Imports` Instrukcji ułatwia dostęp do metod klas, eliminując konieczność jawnie wpisz w pełni kwalifikowane nazwy odwołań.</span><span class="sxs-lookup"><span data-stu-id="a43fe-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="a43fe-121">Aliasy umożliwiają przypisywanie bardziej przyjaznej nazwy do tylko jednej części przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a43fe-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="a43fe-122">Na przykład sekwencji, który powoduje, że pojedynczy tekst do wyświetlenia w wielu wierszach CR/LF jest częścią <xref:Microsoft.VisualBasic.ControlChars> modułu w <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a43fe-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="a43fe-123">Aby użyć tej stałej w programie bez aliasu, należy wpisać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="a43fe-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="a43fe-124">`Imports` instrukcje musi być zawsze pierwszych wierszy, natychmiast po dowolnej `Option` instrukcji w module.</span><span class="sxs-lookup"><span data-stu-id="a43fe-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="a43fe-125">Poniższy fragment kodu przedstawia sposób importowania i przypisać aliasu do <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modułu:</span><span class="sxs-lookup"><span data-stu-id="a43fe-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="a43fe-126">Odwołania do tej przestrzeni nazw może być znacznie krótszy:</span><span class="sxs-lookup"><span data-stu-id="a43fe-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="a43fe-127">Jeśli `Imports` instrukcji nie ma nazwę aliasu, elementy zdefiniowane w importowanych przestrzeni nazw mogą być używane w module bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="a43fe-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="a43fe-128">Jeśli określono nazwę aliasu, musi używać jako kwalifikator nazw zawartych w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a43fe-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a43fe-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a43fe-129">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="a43fe-130">Przestrzenie nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a43fe-130">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
- [<span data-ttu-id="a43fe-131">Zestawy i globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="a43fe-131">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="a43fe-132">Instrukcje: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a43fe-132">How to: Create and Use Assemblies Using the Command Line</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)  
- [<span data-ttu-id="a43fe-133">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="a43fe-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
