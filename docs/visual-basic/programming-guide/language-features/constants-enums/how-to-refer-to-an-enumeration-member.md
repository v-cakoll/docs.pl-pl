---
title: 'Porady: odwoływanie się do elementu członkowskiego wyliczenia'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 66c527bd4ba4721065de8fca8534fe652d0139be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414417"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="0bff7-102">Porady: odwoływanie się do elementu członkowskiego wyliczenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bff7-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="0bff7-103">Wyliczenia zapewniają wygodny sposób pracy z zestawami powiązanych stałych i kojarzenia wartości stałych z nazwami.</span><span class="sxs-lookup"><span data-stu-id="0bff7-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="0bff7-104">Na przykład można zadeklarować Wyliczenie dla zestawu stałych całkowitych skojarzonych z dniami tygodnia, a następnie użyć nazw dni, a nie ich wartości całkowitych w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0bff7-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="0bff7-105">Można uniknąć używania w pełni kwalifikowanych nazw przy użyciu `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0bff7-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="0bff7-106">Aby uzyskać więcej informacji, zobacz [wyliczenia i kwalifikowanie nazw](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="0bff7-106">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="0bff7-107">Aby odwołać się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0bff7-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="0bff7-108">Zakwalifikuj nazwę elementu członkowskiego z wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="0bff7-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="0bff7-109">Na przykład poniższy przykład przypisuje `Saturday` element członkowski `FirstDayOfWeek` wyliczenia do zmiennej `DayValue` .</span><span class="sxs-lookup"><span data-stu-id="0bff7-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="0bff7-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bff7-110">See also</span></span>

- [<span data-ttu-id="0bff7-111">Instrukcje: deklarowanie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0bff7-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="0bff7-112">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="0bff7-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="0bff7-113">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bff7-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="0bff7-114">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0bff7-114">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="0bff7-115">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="0bff7-115">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
