---
title: Wyliczenie i kwantyfikacja nazwy
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
ms.openlocfilehash: 4b09284b8282c481e406050d37cbdb2f3c8686bc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414508"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="9830d-102">Wyliczenie i kwantyfikacja nazwy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9830d-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="9830d-103">Zwykle w przypadku odwoływania się do elementu członkowskiego wyliczenia należy zakwalifikować nazwę elementu członkowskiego o nazwie wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9830d-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="9830d-104">Na przykład, aby odwołać się do `Sunday` elementu członkowskiego `Days` wyliczenia, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="9830d-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="9830d-105">Korzystanie z instrukcji Imports</span><span class="sxs-lookup"><span data-stu-id="9830d-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="9830d-106">Można uniknąć używania w pełni kwalifikowanych nazw, dodając `Imports` instrukcję do sekcji deklaracji przestrzeni nazw kodu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9830d-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="9830d-107">`Imports`Instrukcja importuje nazwy przestrzeni nazw z przywoływanych projektów i zestawów oraz z tego samego projektu, co moduł, w którym znajduje się instrukcja.</span><span class="sxs-lookup"><span data-stu-id="9830d-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="9830d-108">Po dodaniu tej instrukcji można odwołać się do członków wyliczenia bez kwalifikacji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9830d-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="9830d-109">Organizując zestawy powiązanych stałych w wyliczeniach, można użyć tych samych stałych nazw w różnych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="9830d-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="9830d-110">Na przykład można użyć tych samych nazw dla stałych dni tygodnia w `Days` `WorkDays` wyliczeniach i.</span><span class="sxs-lookup"><span data-stu-id="9830d-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="9830d-111">Jeśli używasz `Imports` instrukcji z wyliczeniami, należy zachować ostrożność, aby uniknąć niejednoznacznych odwołań.</span><span class="sxs-lookup"><span data-stu-id="9830d-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="9830d-112">Rozpatrzmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="9830d-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="9830d-113">Przy założeniu `Monday` , że jest składową zarówno `Days` wyliczenia, jak i `Workdays` wyliczenia, ten kod generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9830d-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="9830d-114">Aby uniknąć niejednoznacznych odwołań podczas odwoływania się do pojedynczej stałej, należy zakwalifikować stałą nazwę z wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="9830d-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="9830d-115">Poniższy kod odwołuje się do `Saturday` stałych w `Days` `WorkDays` wyliczeniach i.</span><span class="sxs-lookup"><span data-stu-id="9830d-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="9830d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9830d-116">See also</span></span>

- [<span data-ttu-id="9830d-117">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9830d-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="9830d-118">Instrukcje: deklarowanie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9830d-118">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="9830d-119">Porady: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9830d-119">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="9830d-120">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9830d-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="9830d-121">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9830d-121">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="9830d-122">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="9830d-122">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="9830d-123">Stała i typy literałów</span><span class="sxs-lookup"><span data-stu-id="9830d-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="9830d-124">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9830d-124">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="9830d-125">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="9830d-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="9830d-126">Typy danych</span><span class="sxs-lookup"><span data-stu-id="9830d-126">Data Types</span></span>](../../../language-reference/data-types/index.md)
