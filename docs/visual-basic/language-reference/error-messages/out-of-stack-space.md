---
title: Za mało miejsca na stosie
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349183"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="bdec2-102">Za mało miejsca na stosie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdec2-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="bdec2-103">Stos jest obszarem roboczym pamięci, który powiększa się i zmniejsza dynamicznie z wymaganiami wykonywanymi przez program.</span><span class="sxs-lookup"><span data-stu-id="bdec2-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="bdec2-104">Przekroczono limity.</span><span class="sxs-lookup"><span data-stu-id="bdec2-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bdec2-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="bdec2-105">To correct this error</span></span>  
  
1. <span data-ttu-id="bdec2-106">Sprawdź, czy procedury nie są zbyt głęboko zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="bdec2-106">Check that procedures are not nested too deeply.</span></span>  
  
2. <span data-ttu-id="bdec2-107">Upewnij się, że procedury cykliczne kończą się prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="bdec2-107">Make sure recursive procedures terminate properly.</span></span>  
  
3. <span data-ttu-id="bdec2-108">Jeśli zmienne lokalne wymagają więcej przestrzeni zmiennych lokalnych niż jest dostępna, spróbuj Zadeklaruj pewne zmienne na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="bdec2-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="bdec2-109">Można również zadeklarować wszystkie zmienne w procedurze statycznej, poprzedzając słowo kluczowe `Property`, `Sub`lub `Function` z `Static`.</span><span class="sxs-lookup"><span data-stu-id="bdec2-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="bdec2-110">Można też użyć instrukcji `Static`, aby zadeklarować poszczególne zmienne statyczne w ramach procedur.</span><span class="sxs-lookup"><span data-stu-id="bdec2-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4. <span data-ttu-id="bdec2-111">Przedefiniuj niektóre ciągi o stałej długości jako ciągi o zmiennej długości, ponieważ ciągi o stałej długości używają większej ilości miejsca na stosie niż ciągi o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="bdec2-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="bdec2-112">Możesz również zdefiniować ciąg na poziomie modułu, gdzie nie wymaga miejsca na stosie.</span><span class="sxs-lookup"><span data-stu-id="bdec2-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5. <span data-ttu-id="bdec2-113">Sprawdź liczbę zagnieżdżonych wywołań funkcji `DoEvents` przy użyciu okna dialogowego `Calls`, aby zobaczyć, które procedury są aktywne na stosie.</span><span class="sxs-lookup"><span data-stu-id="bdec2-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6. <span data-ttu-id="bdec2-114">Upewnij się, że "zdarzenie kaskadowe" nie zostało wywołane przez wyzwolenie zdarzenia, które wywołuje procedurę zdarzenia już na stosie.</span><span class="sxs-lookup"><span data-stu-id="bdec2-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="bdec2-115">Zdarzenie kaskadowe jest podobne do niekończącego wywołania procedury cyklicznej, ale jest mniej oczywiste, ponieważ wywołanie jest wykonywane przez Visual Basic, a nie jawne wywołanie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="bdec2-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="bdec2-116">Za pomocą okna dialogowego `Calls` można zobaczyć, które procedury są aktywne na stosie.</span><span class="sxs-lookup"><span data-stu-id="bdec2-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdec2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdec2-117">See also</span></span>

- [<span data-ttu-id="bdec2-118">Okna pamięci</span><span class="sxs-lookup"><span data-stu-id="bdec2-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
