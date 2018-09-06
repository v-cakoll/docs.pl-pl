---
title: Wyliczenie i kwantyfikacja nazwy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: cd07c883c576e917cf1aa5072505854bc906eb3f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857592"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="a613b-102">Wyliczenie i kwantyfikacja nazwy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a613b-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="a613b-103">Zwykle przy odwoływaniu się do elementu członkowskiego wyliczenia, masz prawo nazwę elementu członkowskiego o nazwie wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a613b-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="a613b-104">Na przykład, aby odwołać się do `Sunday` członek Twojego `Days` wyliczenia, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="a613b-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="a613b-105">Za pomocą Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a613b-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="a613b-106">Możesz uniknąć używania w pełni kwalifikowanych nazw, dodając `Imports` instrukcję do sekcji deklaracji przestrzeni nazw w kodzie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a613b-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 <span data-ttu-id="a613b-107">`Imports` Instrukcja importuje nazwy przestrzeni nazw z przywoływane projekty i zespoły i w tym samym projekcie jako moduł, w której występuje instrukcja.</span><span class="sxs-lookup"><span data-stu-id="a613b-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="a613b-108">Po dodaniu tej instrukcji, możesz zapoznać się z elementów członkowskich wyliczenia bez kwalifikacji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a613b-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 <span data-ttu-id="a613b-109">Organizując zestawów powiązanych stałe wyliczeń, można użyć takich samych nazwach stałej w różnych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="a613b-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="a613b-110">Na przykład, można użyć tej samej nazwy dla stałych dzień tygodnia, w `Days` i `WorkDays` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a613b-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="a613b-111">Jeśli używasz `Imports` instrukcji związanych z wyliczeniami usługi, należy uważać, aby uniknąć niejednoznacznego odwołania.</span><span class="sxs-lookup"><span data-stu-id="a613b-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="a613b-112">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="a613b-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 <span data-ttu-id="a613b-113">Przy założeniu, że `Monday` jest elementem członkowskim `Days` wyliczenie i `Workdays` wyliczenia, ten kod generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a613b-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="a613b-114">Aby uniknąć niejednoznacznych odwołań przy odwoływaniu się do poszczególnych stałą, kwalifikują się stałe nazwą jego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a613b-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="a613b-115">Poniższy kod, który odwołuje się do `Saturday` stałe w `Days` i `WorkDays` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a613b-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a613b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a613b-116">See Also</span></span>  
 [<span data-ttu-id="a613b-117">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a613b-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="a613b-118">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="a613b-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="a613b-119">Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a613b-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="a613b-120">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a613b-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="a613b-121">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a613b-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="a613b-122">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="a613b-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="a613b-123">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="a613b-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="a613b-124">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a613b-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="a613b-125">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="a613b-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="a613b-126">Typy danych</span><span class="sxs-lookup"><span data-stu-id="a613b-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
