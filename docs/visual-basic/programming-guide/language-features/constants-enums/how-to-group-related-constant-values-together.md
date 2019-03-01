---
title: 'Instrukcje: Grupowanie związanych wartości stałych razem (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 63475487c8a35f5b306b28d4e7097324bef00d85
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977828"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="a6acf-102">Instrukcje: Grupowanie związanych wartości stałych razem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6acf-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="a6acf-103">Wyliczenie to najlepszy sposób, aby zgrupować pokrewnych stałych.</span><span class="sxs-lookup"><span data-stu-id="a6acf-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="a6acf-104">Utwórz wyliczenie z `Enum` instrukcji w sekcji deklaracji klasy lub modułu.</span><span class="sxs-lookup"><span data-stu-id="a6acf-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="a6acf-105">Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="a6acf-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="a6acf-106">Do grupy powiązanych wartości stałych</span><span class="sxs-lookup"><span data-stu-id="a6acf-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="a6acf-107">Zapis deklarację, że obejmuje poziom dostępu do kodu, `Enum` — słowo kluczowe i prawidłową nazwę.</span><span class="sxs-lookup"><span data-stu-id="a6acf-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="a6acf-108">Ten przykład tworzy `Private` wyliczenia, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="a6acf-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  <span data-ttu-id="a6acf-109">Definiowanie stałych w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="a6acf-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="a6acf-110">Ten przykład tworzy `Public` wyliczenie `temperatureValues` i przypisuje jej wartości.</span><span class="sxs-lookup"><span data-stu-id="a6acf-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a6acf-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6acf-111">See also</span></span>
- [<span data-ttu-id="a6acf-112">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="a6acf-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="a6acf-113">Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a6acf-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="a6acf-114">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="a6acf-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="a6acf-115">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="a6acf-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="a6acf-116">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="a6acf-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="a6acf-117">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a6acf-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
