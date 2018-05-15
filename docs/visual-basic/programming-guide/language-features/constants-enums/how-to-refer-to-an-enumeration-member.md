---
title: 'Porady: odwoływanie się do elementu członkowskiego wyliczenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: f995a0ef69c503360a5d709551a7f0ccfd67ce40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="2ef85-102">Porady: odwoływanie się do elementu członkowskiego wyliczenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ef85-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="2ef85-103">Wyliczenia zapewnić wygodny sposób pracy z zestawów powiązanych stałych i do skojarzenia z nazwami wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="2ef85-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="2ef85-104">Na przykład można zadeklarować wyliczenia dla zestawu stałe całkowite skojarzone z dni tygodnia, a następnie użyć nazwy dni, a nie ich wartości całkowite w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2ef85-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="2ef85-105">Możesz uniknąć używania w pełni kwalifikowane nazwy z `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2ef85-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="2ef85-106">Aby uzyskać więcej informacji, zobacz [wyliczenie i kwantyfikacja nazwy](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="2ef85-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="2ef85-107">Aby odwołać się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2ef85-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="2ef85-108">Nazwy elementu członkowskiego z wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2ef85-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="2ef85-109">Na przykład w poniższym przykładzie przypisano `Saturday` członkiem `FirstDayOfWeek` wyliczenie do zmiennej `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="2ef85-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2ef85-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ef85-110">See Also</span></span>  
 [<span data-ttu-id="2ef85-111">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="2ef85-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="2ef85-112">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="2ef85-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="2ef85-113">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2ef85-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="2ef85-114">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2ef85-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="2ef85-115">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="2ef85-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
