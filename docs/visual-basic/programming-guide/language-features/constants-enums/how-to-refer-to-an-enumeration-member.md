---
title: 'Porady: odwoływanie się do elementu członkowskiego wyliczenia'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 01db5b84783eda45cd7867dc8fea8a69fc18b98a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353996"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="52280-102">Porady: odwoływanie się do elementu członkowskiego wyliczenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52280-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="52280-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span><span class="sxs-lookup"><span data-stu-id="52280-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="52280-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span><span class="sxs-lookup"><span data-stu-id="52280-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="52280-105">You can avoid using fully qualified names with the `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="52280-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="52280-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="52280-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="52280-107">To refer to an enumeration member</span><span class="sxs-lookup"><span data-stu-id="52280-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="52280-108">Qualify the member name with the enumeration.</span><span class="sxs-lookup"><span data-stu-id="52280-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="52280-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="52280-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="52280-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52280-110">See also</span></span>

- [<span data-ttu-id="52280-111">How to: Declare an Enumeration</span><span class="sxs-lookup"><span data-stu-id="52280-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="52280-112">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="52280-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="52280-113">How to: Iterate Through An Enumeration in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52280-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="52280-114">Instrukcje: określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="52280-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="52280-115">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="52280-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
