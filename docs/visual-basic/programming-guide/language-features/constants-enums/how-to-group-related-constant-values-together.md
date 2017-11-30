---
title: "Porady: grupowanie związanych wartości stałych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="4f99b-102">Porady: grupowanie związanych wartości stałych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f99b-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="4f99b-103">Wyliczenie to najlepszy sposób, aby grupować powiązane stałe.</span><span class="sxs-lookup"><span data-stu-id="4f99b-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="4f99b-104">Utwórz wyliczenie z `Enum` instrukcji w sekcji deklaracji klasy lub module.</span><span class="sxs-lookup"><span data-stu-id="4f99b-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="4f99b-105">Aby uzyskać więcej informacji, zobacz [porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="4f99b-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="4f99b-106">Do grupy związanych wartości stałych</span><span class="sxs-lookup"><span data-stu-id="4f99b-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="4f99b-107">Zapis deklaracji, która zawiera poziom dostępu kodu, `Enum` — słowo kluczowe i prawidłową nazwę.</span><span class="sxs-lookup"><span data-stu-id="4f99b-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="4f99b-108">Ten przykład tworzy `Private` wyliczenia, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="4f99b-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="4f99b-109">Definiowanie stałych w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="4f99b-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="4f99b-110">Ten przykład tworzy `Public` wyliczenie `temperatureValues` i przypisuje jej wartości.</span><span class="sxs-lookup"><span data-stu-id="4f99b-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4f99b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f99b-111">See Also</span></span>  
 [<span data-ttu-id="4f99b-112">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="4f99b-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="4f99b-113">Porady: odwołuje się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4f99b-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="4f99b-114">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="4f99b-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="4f99b-115">Stałe — Przegląd</span><span class="sxs-lookup"><span data-stu-id="4f99b-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="4f99b-116">Stała i typy literałów</span><span class="sxs-lookup"><span data-stu-id="4f99b-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="4f99b-117">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4f99b-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
