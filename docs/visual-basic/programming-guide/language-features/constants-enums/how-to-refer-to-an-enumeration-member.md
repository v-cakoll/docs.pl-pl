---
title: 'Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 000c7f8f87792b598f177cae123010eb8888c328
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645964"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="195d5-102">Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="195d5-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="195d5-103">Wyliczenia zapewniają wygodny sposób pracy z zestawami pokrewnych stałych i skojarzyć wartości stałych o nazwach.</span><span class="sxs-lookup"><span data-stu-id="195d5-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="195d5-104">Na przykład można zadeklarować wyliczenie zbiór stałe całkowite skojarzone z dni tygodnia, a w kodzie następnie używać nazwy dni, a nie ich wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="195d5-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="195d5-105">Możesz uniknąć używania z w pełni kwalifikowanych nazw `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="195d5-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="195d5-106">Aby uzyskać więcej informacji, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="195d5-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="195d5-107">Aby odwołać się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="195d5-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="195d5-108">Kwalifikują się nazwę składowej wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="195d5-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="195d5-109">Na przykład, poniższy przykład przypisuje `Saturday` członkiem `FirstDayOfWeek` wyliczenia do zmiennej `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="195d5-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="195d5-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="195d5-110">See also</span></span>

- [<span data-ttu-id="195d5-111">Instrukcje: Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="195d5-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="195d5-112">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="195d5-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="195d5-113">Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="195d5-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="195d5-114">Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="195d5-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="195d5-115">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="195d5-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
