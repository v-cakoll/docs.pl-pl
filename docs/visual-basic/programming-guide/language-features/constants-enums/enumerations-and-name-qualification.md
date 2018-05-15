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
ms.openlocfilehash: eb1f5653d968e81168833cd57813219e8f049b70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="e75af-102">Wyliczenie i kwantyfikacja nazwy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e75af-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="e75af-103">Zwykle podczas odwoływania się do elementu członkowskiego wyliczenia, muszą kwalifikować się nazwę elementu członkowskiego o nazwie wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e75af-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="e75af-104">Na przykład, aby odwołać się do `Sunday` członka Twojej `Days` wyliczenia, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="e75af-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="e75af-105">Przy użyciu Importy — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e75af-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="e75af-106">Możesz uniknąć używania w pełni kwalifikowane nazwy przez dodanie `Imports` instrukcji w sekcji deklaracji przestrzeni nazw kodu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e75af-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 <span data-ttu-id="e75af-107">`Imports` Instrukcji imports nazwy przestrzeni nazw z przywoływane projekty i zestawy, a za pomocą tego samego projektu jako moduł, w której występuje instrukcja.</span><span class="sxs-lookup"><span data-stu-id="e75af-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="e75af-108">Po dodaniu tej instrukcji można odwołać się do członków wyliczenia bez kwalifikacji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e75af-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 <span data-ttu-id="e75af-109">Poprzez organizowanie zestawów powiązanych stałe w wyliczenia, można użyć tych samych nazw stałej w różnych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="e75af-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="e75af-110">Na przykład można użyć tych samych nazw stałe dzień tygodnia w `Days` i `WorkDays` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e75af-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="e75af-111">Jeśli używasz `Imports` instrukcji z Twojej wyliczenia, należy zachować ostrożność uniknąć niejednoznacznych odwołań.</span><span class="sxs-lookup"><span data-stu-id="e75af-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="e75af-112">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="e75af-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 <span data-ttu-id="e75af-113">Przy założeniu, że `Monday` jest elementem członkowskim `Days` wyliczenie i `Workdays` wyliczenia, ten kod generowany jest błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e75af-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="e75af-114">Aby uniknąć niejednoznacznych odwołań podczas odwoływania się do poszczególnych stała, Zakwalifikuj nazwę przez stałej z jego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e75af-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="e75af-115">Poniższy kod odwołuje się do `Saturday` stałe w `Days` i `WorkDays` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e75af-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e75af-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e75af-116">See Also</span></span>  
 [<span data-ttu-id="e75af-117">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e75af-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="e75af-118">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="e75af-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="e75af-119">Instrukcje: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e75af-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="e75af-120">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e75af-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="e75af-121">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e75af-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="e75af-122">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="e75af-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="e75af-123">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="e75af-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="e75af-124">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e75af-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="e75af-125">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="e75af-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="e75af-126">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e75af-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
