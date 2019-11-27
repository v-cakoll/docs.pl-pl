---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 0c38c2b81af7b4cb8fd1723853a09c5413f805af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344740"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="90dd7-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90dd7-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="90dd7-103">Określa, że Visual Basic powinny kierować wszystkie ciągi do wartości American National Standards Institute (ANSI), niezależnie od nazwy zadeklarowanej procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="90dd7-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="90dd7-104">Po wywołaniu procedury zdefiniowanej poza projektem kompilator Visual Basic nie ma dostępu do informacji potrzebnych do poprawnego wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="90dd7-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="90dd7-105">Informacje te obejmują miejsce, w którym znajduje się procedura, sposób jego identyfikacji, jego sekwencję wywoływania i zwracany typ oraz zestaw znaków użytych w ciągu.</span><span class="sxs-lookup"><span data-stu-id="90dd7-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="90dd7-106">[Instrukcja DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.</span><span class="sxs-lookup"><span data-stu-id="90dd7-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="90dd7-107">Część `charsetmodifier` w instrukcji `Declare` dostarcza informacje o zestawie znaków do organizowania ciągów podczas wywołania procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="90dd7-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="90dd7-108">Ma także wpływ na to, w jaki sposób Visual Basic przeszukuje zewnętrzny plik dla nazwy procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="90dd7-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="90dd7-109">Modyfikator `Ansi` określa, że Visual Basic powinien kierować wszystkie ciągi do wartości ANSI i należy odszukać procedurę bez modyfikowania jej nazwy podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="90dd7-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="90dd7-110">Jeśli nie określono modyfikatora zestawu znaków, `Ansi` jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="90dd7-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90dd7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90dd7-111">Remarks</span></span>  
 <span data-ttu-id="90dd7-112">Modyfikator `Ansi` może być używany w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="90dd7-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="90dd7-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="90dd7-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="90dd7-114">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="90dd7-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="90dd7-115">To słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="90dd7-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90dd7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90dd7-116">See also</span></span>

- [<span data-ttu-id="90dd7-117">Auto</span><span class="sxs-lookup"><span data-stu-id="90dd7-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="90dd7-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="90dd7-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="90dd7-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="90dd7-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
