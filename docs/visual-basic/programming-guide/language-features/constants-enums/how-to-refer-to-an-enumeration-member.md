---
title: 'Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: efaaecb231b340798012206a0f23fde0ad4cdbeb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602003"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="978e1-102">Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="978e1-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="978e1-103">Wyliczenia zapewniają wygodny sposób pracy z zestawami pokrewnych stałych i skojarzyć wartości stałych o nazwach.</span><span class="sxs-lookup"><span data-stu-id="978e1-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="978e1-104">Na przykład można zadeklarować wyliczenie zbiór stałe całkowite skojarzone z dni tygodnia, a w kodzie następnie używać nazwy dni, a nie ich wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="978e1-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="978e1-105">Możesz uniknąć używania z w pełni kwalifikowanych nazw `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="978e1-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="978e1-106">Aby uzyskać więcej informacji, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="978e1-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="978e1-107">Aby odwołać się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="978e1-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="978e1-108">Kwalifikują się nazwę składowej wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="978e1-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="978e1-109">Na przykład, poniższy przykład przypisuje `Saturday` członkiem `FirstDayOfWeek` wyliczenia do zmiennej `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="978e1-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="978e1-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="978e1-110">See also</span></span>
- [<span data-ttu-id="978e1-111">Instrukcje: Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="978e1-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="978e1-112">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="978e1-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="978e1-113">Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="978e1-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="978e1-114">Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="978e1-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="978e1-115">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="978e1-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
