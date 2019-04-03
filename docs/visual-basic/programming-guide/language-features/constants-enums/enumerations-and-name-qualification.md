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
ms.openlocfilehash: f0a806b040720cf6682f8a72025a0590dd4d91f7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818439"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="123f9-102">Wyliczenie i kwantyfikacja nazwy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="123f9-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="123f9-103">Zwykle przy odwoływaniu się do elementu członkowskiego wyliczenia, masz prawo nazwę elementu członkowskiego o nazwie wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="123f9-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="123f9-104">Na przykład, aby odwołać się do `Sunday` członek Twojego `Days` wyliczenia, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="123f9-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="123f9-105">Za pomocą Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="123f9-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="123f9-106">Możesz uniknąć używania w pełni kwalifikowanych nazw, dodając `Imports` instrukcję do sekcji deklaracji przestrzeni nazw w kodzie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="123f9-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="123f9-107">`Imports` Instrukcja importuje nazwy przestrzeni nazw z przywoływane projekty i zespoły i w tym samym projekcie jako moduł, w której występuje instrukcja.</span><span class="sxs-lookup"><span data-stu-id="123f9-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="123f9-108">Po dodaniu tej instrukcji, możesz zapoznać się z elementów członkowskich wyliczenia bez kwalifikacji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="123f9-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="123f9-109">Organizując zestawów powiązanych stałe wyliczeń, można użyć takich samych nazwach stałej w różnych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="123f9-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="123f9-110">Na przykład, można użyć tej samej nazwy dla stałych dzień tygodnia, w `Days` i `WorkDays` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="123f9-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="123f9-111">Jeśli używasz `Imports` instrukcji związanych z wyliczeniami usługi, należy uważać, aby uniknąć niejednoznacznego odwołania.</span><span class="sxs-lookup"><span data-stu-id="123f9-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="123f9-112">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="123f9-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="123f9-113">Przy założeniu, że `Monday` jest elementem członkowskim `Days` wyliczenie i `Workdays` wyliczenia, ten kod generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="123f9-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="123f9-114">Aby uniknąć niejednoznacznych odwołań przy odwoływaniu się do poszczególnych stałą, kwalifikują się stałe nazwą jego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="123f9-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="123f9-115">Poniższy kod, który odwołuje się do `Saturday` stałe w `Days` i `WorkDays` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="123f9-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="123f9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="123f9-116">See also</span></span>

- [<span data-ttu-id="123f9-117">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="123f9-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="123f9-118">Instrukcje: Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="123f9-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="123f9-119">Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="123f9-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="123f9-120">Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="123f9-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="123f9-121">Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="123f9-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="123f9-122">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="123f9-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="123f9-123">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="123f9-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="123f9-124">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="123f9-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="123f9-125">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="123f9-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="123f9-126">Typy danych</span><span class="sxs-lookup"><span data-stu-id="123f9-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
