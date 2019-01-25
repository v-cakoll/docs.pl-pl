---
title: 'Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 92d2e9918429c9cf408f288f832e4615b95ad423
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690192"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="fb111-102">Instrukcje: Określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb111-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="fb111-103"><xref:System.Enum.GetValues%2A> i <xref:System.Enum.GetNames%2A> metody umożliwiają określenie parametrów i wartości skojarzone z elementów członkowskich wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fb111-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="fb111-104">Aby określić parametry skojarzone z wyliczeniem</span><span class="sxs-lookup"><span data-stu-id="fb111-104">To determine the string associated with an enumeration</span></span>  
  
-   <span data-ttu-id="fb111-105">Użyj <xref:System.Enum.GetNames%2A> metodę, aby pobrać parametry skojarzone z elementów członkowskich wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fb111-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="fb111-106">W tym przykładzie deklaruje wyliczenie `flavorEnum`, następnie używa <xref:System.Enum.GetNames%2A> metodę w celu wyświetlenia ciągi skojarzonych z każdym elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="fb111-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fb111-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb111-107">See also</span></span>
- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="fb111-108">Instrukcje: Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="fb111-108">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="fb111-109">Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fb111-109">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="fb111-110">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="fb111-110">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="fb111-111">Instrukcje: Iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb111-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="fb111-112">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="fb111-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="fb111-113">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fb111-113">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
