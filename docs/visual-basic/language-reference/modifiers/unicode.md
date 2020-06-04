---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: 9b1bc40bb52244deefc0486d3a40c4b961ad1ee5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402684"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="1300a-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1300a-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="1300a-103">Określa, że Visual Basic powinny kierować wszystkie ciągi do wartości Unicode, niezależnie od nazwy zadeklarowanej procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="1300a-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="1300a-104">Po wywołaniu procedury zdefiniowanej poza projektem, kompilator Visual Basic nie ma dostępu do informacji, które muszą mieć w celu poprawnego wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="1300a-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="1300a-105">Informacje te obejmują miejsce, w którym znajduje się procedura, sposób jego identyfikacji, jego sekwencję wywoływania i zwracany typ oraz zestaw znaków użytych w ciągu.</span><span class="sxs-lookup"><span data-stu-id="1300a-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="1300a-106">[Instrukcja DECLARE](../statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza te niezbędne informacje.</span><span class="sxs-lookup"><span data-stu-id="1300a-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="1300a-107">`charsetmodifier`Część w `Declare` instrukcji dostarcza informacje zestawu znaków do organizowania ciągów podczas wywołania procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="1300a-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="1300a-108">Ma także wpływ na to, w jaki sposób Visual Basic przeszukuje zewnętrzny plik dla nazwy procedury zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="1300a-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="1300a-109">`Unicode`Modyfikator określa, że Visual Basic powinien kierować wszystkie ciągi do wartości Unicode i należy odszukać procedurę bez modyfikowania jej nazwy podczas wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="1300a-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="1300a-110">Jeśli nie określono modyfikatora zestawu znaków, `Ansi` jest to ustawienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="1300a-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1300a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1300a-111">Remarks</span></span>  
 <span data-ttu-id="1300a-112">`Unicode`Modyfikator może być używany w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="1300a-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="1300a-113">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="1300a-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="1300a-114">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="1300a-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="1300a-115">To słowo kluczowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1300a-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1300a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1300a-116">See also</span></span>

- [<span data-ttu-id="1300a-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="1300a-117">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="1300a-118">Automatycznie</span><span class="sxs-lookup"><span data-stu-id="1300a-118">Auto</span></span>](auto.md)
- [<span data-ttu-id="1300a-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1300a-119">Keywords</span></span>](../keywords/index.md)
