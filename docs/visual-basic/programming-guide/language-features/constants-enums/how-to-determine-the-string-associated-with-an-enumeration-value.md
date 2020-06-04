---
title: 'Porady: określanie ciągu skojarzonego z wartością wyliczenia'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 525da9206472afefa9f85b49ceee0775cbd168c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414469"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="7fb2e-102">Porady: określanie ciągu skojarzonego z wartością wyliczenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fb2e-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="7fb2e-103"><xref:System.Enum.GetValues%2A>Metody i <xref:System.Enum.GetNames%2A> umożliwiają określanie ciągów i wartości skojarzonych z elementami członkowskimi wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7fb2e-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="7fb2e-104">Aby określić ciąg skojarzony z wyliczeniem</span><span class="sxs-lookup"><span data-stu-id="7fb2e-104">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="7fb2e-105">Użyj <xref:System.Enum.GetNames%2A> metody, aby pobrać ciągi skojarzone z elementami członkowskimi wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7fb2e-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="7fb2e-106">Ten przykład deklaruje Wyliczenie, `flavorEnum` a następnie używa <xref:System.Enum.GetNames%2A> metody do wyświetlania ciągów skojarzonych z poszczególnymi elementami członkowskimi.</span><span class="sxs-lookup"><span data-stu-id="7fb2e-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7fb2e-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7fb2e-107">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="7fb2e-108">Instrukcje: deklarowanie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7fb2e-108">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="7fb2e-109">Porady: odwoływanie się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7fb2e-109">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="7fb2e-110">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="7fb2e-110">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="7fb2e-111">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7fb2e-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="7fb2e-112">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="7fb2e-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="7fb2e-113">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7fb2e-113">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
