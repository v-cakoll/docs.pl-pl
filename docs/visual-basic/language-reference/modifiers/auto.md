---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 414998b4bef526060e7ba4f584fa071fbd0acaa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="auto-visual-basic"></a><span data-ttu-id="b7960-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7960-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="b7960-103">Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework oparte na zewnętrzną nazwę procedury zewnętrznej został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="b7960-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="b7960-104">Po wywołaniu procedury zdefiniowany poza projektem, kompilator Visual Basic nie ma dostępu do informacji musi mieć do wywołania tej procedury poprawnie.</span><span class="sxs-lookup"><span data-stu-id="b7960-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="b7960-105">Informacje te obejmują lokalizacji procedurą, jak określono, jego sekwencja wywoływania oraz zwracany typ i ciąg znaków ustaw go używa.</span><span class="sxs-lookup"><span data-stu-id="b7960-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="b7960-106">[Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.</span><span class="sxs-lookup"><span data-stu-id="b7960-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="b7960-107">`charsetmodifier` Części w `Declare` instrukcji dostarcza informacji zestaw znaków dla organizowanie ciągów podczas wywoływania procedury zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="b7960-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="b7960-108">Wpływa to również na jak Visual Basic wyszukuje plik zewnętrznych dla nazwę procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="b7960-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="b7960-109">`Auto` Modyfikator Określa, że Visual Basic powinien kierować ciągi zgodnie z regułami programu .NET Framework i powinien ustalić podstawowy zestaw czasu wykonywania platformy i prawdopodobnie znaków zmodyfikować nazwę procedury zewnętrznej, jeśli początkowe wyszukiwanie kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b7960-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="b7960-110">Aby uzyskać więcej informacji, zobacz "Zestawów znaków" w [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b7960-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="b7960-111">Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="b7960-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7960-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7960-112">Remarks</span></span>  
 <span data-ttu-id="b7960-113">`Auto` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="b7960-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b7960-114">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b7960-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="b7960-115">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="b7960-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="b7960-116">To słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b7960-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7960-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7960-117">See Also</span></span>  
 [<span data-ttu-id="b7960-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="b7960-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="b7960-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="b7960-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="b7960-120">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b7960-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
