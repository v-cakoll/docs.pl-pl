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
ms.openlocfilehash: c50a25dc0802f275e5cd4e0068e1a68bf559abc1
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066041"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="f867a-102">Referencje i importy — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f867a-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="f867a-103">Można udostępnić zewnętrznych obiektów do projektu, wybierając **Dodaj odwołanie** polecenie **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="f867a-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="f867a-104">Zestawy, które są podobne biblioteki typów, ale zawierają więcej informacji może wskazywać odwołania w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f867a-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="f867a-105">Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f867a-105">The Imports Statement</span></span>  
 <span data-ttu-id="f867a-106">Zestawy zawierają jeden lub kilka przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f867a-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="f867a-107">Po dodaniu odwołania do zestawu, można również dodać `Imports` instrukcję, aby moduł, który kontroluje widoczność tego zestawu przestrzeni nazw, w module.</span><span class="sxs-lookup"><span data-stu-id="f867a-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="f867a-108">`Imports` Instrukcja oferuje zakresu kontekstu, która umożliwia używanie tylko część obszaru nazw, trzeba podać unikatowy odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f867a-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="f867a-109">`Imports` Instrukcji ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="f867a-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="f867a-110">`Aliasname` odnosi się do krótką nazwę, których można użyć w kodzie, do odwoływania się do importowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f867a-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="f867a-111">`Namespace` jest dostępna za pośrednictwem jednej przestrzeni nazw odwołanie projektu za pomocą definicji w projekcie lub poprzedniej `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f867a-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="f867a-112">Moduł może zawierać dowolną liczbę `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f867a-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="f867a-113">Muszą występować po każdym `Option` instrukcji, jeśli jest obecny, ale przed innymi kodami.</span><span class="sxs-lookup"><span data-stu-id="f867a-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f867a-114">Nie należy mylić odwołania do projektu przy użyciu `Imports` instrukcji lub `Declare` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f867a-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="f867a-115">Odwołania do projektu udostępnić zewnętrzne obiekty, takie jak obiekty w zestawach, do projektów Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f867a-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="f867a-116">`Imports` Instrukcja jest używana, aby uprościć dostęp do odwołania do projektu, ale nie zapewnia dostępu do tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="f867a-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="f867a-117">`Declare` Instrukcja jest używana do zadeklarowania odwołania do zewnętrznej procedury biblioteki dołączanej (dynamicznie DLL).</span><span class="sxs-lookup"><span data-stu-id="f867a-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="f867a-118">Aliasy użycia za pomocą Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f867a-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="f867a-119">`Imports` Instrukcji ułatwia dostęp do metod klas, eliminując konieczność jawnie wpisz w pełni kwalifikowane nazwy odwołań.</span><span class="sxs-lookup"><span data-stu-id="f867a-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="f867a-120">Aliasy umożliwiają przypisywanie bardziej przyjaznej nazwy do tylko jednej części przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f867a-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="f867a-121">Na przykład sekwencji, który powoduje, że pojedynczy tekst do wyświetlenia w wielu wierszach CR/LF jest częścią <xref:Microsoft.VisualBasic.ControlChars> modułu w <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f867a-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f867a-122">Aby użyć tej stałej w programie bez aliasu, należy wpisać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f867a-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="f867a-123">`Imports` instrukcje musi być zawsze pierwszych wierszy, natychmiast po dowolnej `Option` instrukcji w module.</span><span class="sxs-lookup"><span data-stu-id="f867a-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="f867a-124">Poniższy fragment kodu przedstawia sposób importowania i przypisać aliasu do <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modułu:</span><span class="sxs-lookup"><span data-stu-id="f867a-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="f867a-125">Odwołania do tej przestrzeni nazw może być znacznie krótszy:</span><span class="sxs-lookup"><span data-stu-id="f867a-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="f867a-126">Jeśli `Imports` instrukcji nie ma nazwę aliasu, elementy zdefiniowane w importowanych przestrzeni nazw mogą być używane w module bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="f867a-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="f867a-127">Jeśli określono nazwę aliasu, musi używać jako kwalifikator nazw zawartych w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f867a-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f867a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f867a-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="f867a-129">Przestrzenie nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f867a-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="f867a-130">Zestawy i globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="f867a-130">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [<span data-ttu-id="f867a-131">Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f867a-131">How to: Create and Use Assemblies Using the Command Line</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
- [<span data-ttu-id="f867a-132">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="f867a-132">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
