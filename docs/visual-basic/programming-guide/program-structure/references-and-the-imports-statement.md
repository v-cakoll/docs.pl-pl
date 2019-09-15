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
ms.openlocfilehash: 5b810af86f8659ffbe27d23d36aece408516a9bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972057"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="f1f5b-102">Referencje i importy — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1f5b-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="f1f5b-103">Obiekty zewnętrzne można udostępnić projekt, wybierając polecenie **Dodaj odwołanie** w menu **projekt** .</span><span class="sxs-lookup"><span data-stu-id="f1f5b-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="f1f5b-104">Odwołania w Visual Basic mogą wskazywać zestawy, które są takie jak biblioteki typów, ale zawierają więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="f1f5b-105">Instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="f1f5b-105">The Imports Statement</span></span>  
 <span data-ttu-id="f1f5b-106">Zestawy obejmują co najmniej jedną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="f1f5b-107">Po dodaniu odwołania do zestawu, można również dodać `Imports` instrukcję do modułu, który kontroluje widoczność przestrzeni nazw tego zestawu w module.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="f1f5b-108">`Imports` Instrukcja zawiera kontekst zakresu, który umożliwia użycie tylko części przestrzeni nazw niezbędnej do dostarczenia unikatowego odwołania.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="f1f5b-109">`Imports` Instrukcja ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="f1f5b-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="f1f5b-110">`Aliasname`odwołuje się do krótkiej nazwy, której można użyć w kodzie, aby odwołać się do zaimportowanej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="f1f5b-111">`Namespace`jest przestrzenią nazw dostępną za pomocą odwołania do projektu, za pomocą definicji w ramach projektu lub poprzedniej `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="f1f5b-112">Moduł może zawierać dowolną liczbę `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="f1f5b-113">Muszą one znajdować się `Option` po każdej instrukcji, jeśli jest obecny, ale przed jakimkolwiek innym kodem.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1f5b-114">Nie należy mylić odwołań projektu z `Imports` instrukcją `Declare` lub instrukcją.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="f1f5b-115">Odwołania projektu tworzą obiekty zewnętrzne, takie jak obiekty w zestawach, dostępne do Visual Basic projektów.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="f1f5b-116">`Imports` Instrukcja służy do uproszczenia dostępu do odwołań do projektu, ale nie zapewnia dostępu do tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="f1f5b-117">`Declare` Instrukcja jest używana do deklarowania odwołania do procedury zewnętrznej w bibliotece dołączanej dynamicznie (dll).</span><span class="sxs-lookup"><span data-stu-id="f1f5b-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="f1f5b-118">Używanie aliasów z instrukcją Imports</span><span class="sxs-lookup"><span data-stu-id="f1f5b-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="f1f5b-119">`Imports` Instrukcja ułatwia dostęp do metod klas przez wyeliminowanie konieczności jawnego wpisywania w pełni kwalifikowanych nazw odwołań.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="f1f5b-120">Aliasy umożliwiają przypisanie nazwy bardziej przyjaznej tylko do jednej części przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="f1f5b-121">Na przykład sekwencja powrotu karetki i wysuwu wiersza, która powoduje, że pojedynczy fragment tekstu, który ma być wyświetlany w wielu wierszach, <xref:Microsoft.VisualBasic.ControlChars> jest częścią <xref:Microsoft.VisualBasic?displayProperty=nameWithType> modułu w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f1f5b-122">Aby użyć tej stałej w programie bez aliasu, należy wpisać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f1f5b-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="f1f5b-123">`Imports`instrukcje muszą zawsze być pierwszym wierszem bezpośrednio po `Option` instrukcjach w module.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="f1f5b-124">Poniższy fragment kodu przedstawia sposób importowania i przypisywania aliasu do <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modułu:</span><span class="sxs-lookup"><span data-stu-id="f1f5b-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="f1f5b-125">Przyszłe odwołania do tej przestrzeni nazw mogą być znacznie krótsze:</span><span class="sxs-lookup"><span data-stu-id="f1f5b-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="f1f5b-126">`Imports` Jeśli instrukcja nie zawiera nazwy aliasu, elementy zdefiniowane w zaimportowanej przestrzeni nazw mogą być używane w module bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="f1f5b-127">Jeśli Nazwa aliasu jest określona, musi być używana jako kwalifikator dla nazw zawartych w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1f5b-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f5b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1f5b-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="f1f5b-129">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1f5b-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="f1f5b-130">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="f1f5b-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="f1f5b-131">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="f1f5b-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
