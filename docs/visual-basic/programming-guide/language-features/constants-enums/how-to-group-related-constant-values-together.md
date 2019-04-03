---
title: 'Instrukcje: Grupowanie związanych wartości stałych razem (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 9174bcd2385103cf7fa1daf3133e388f9b4998a4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843765"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="2838d-102">Instrukcje: Grupowanie związanych wartości stałych razem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2838d-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="2838d-103">Wyliczenie to najlepszy sposób, aby zgrupować pokrewnych stałych.</span><span class="sxs-lookup"><span data-stu-id="2838d-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="2838d-104">Utwórz wyliczenie z `Enum` instrukcji w sekcji deklaracji klasy lub modułu.</span><span class="sxs-lookup"><span data-stu-id="2838d-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="2838d-105">Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="2838d-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="2838d-106">Do grupy powiązanych wartości stałych</span><span class="sxs-lookup"><span data-stu-id="2838d-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="2838d-107">Zapis deklarację, że obejmuje poziom dostępu do kodu, `Enum` — słowo kluczowe i prawidłową nazwę.</span><span class="sxs-lookup"><span data-stu-id="2838d-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="2838d-108">Ten przykład tworzy `Private` wyliczenia, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="2838d-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  <span data-ttu-id="2838d-109">Definiowanie stałych w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="2838d-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="2838d-110">Ten przykład tworzy `Public` wyliczenie `temperatureValues` i przypisuje jej wartości.</span><span class="sxs-lookup"><span data-stu-id="2838d-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2838d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2838d-111">See also</span></span>

- [<span data-ttu-id="2838d-112">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="2838d-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="2838d-113">Instrukcje: Odnoszą się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2838d-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="2838d-114">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="2838d-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="2838d-115">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="2838d-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="2838d-116">Typy danych Stała i Literał</span><span class="sxs-lookup"><span data-stu-id="2838d-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="2838d-117">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2838d-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
