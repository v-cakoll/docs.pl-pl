---
title: Modyfikator „Custom” jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: c1b57ccdaa9e04c837ecf7572bc164683a934b2d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273520"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="3d8b9-102">Modyfikator „Custom” jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych</span><span class="sxs-lookup"><span data-stu-id="3d8b9-102">'Custom' modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="3d8b9-103">W przeciwieństwie do zdarzenia niestandardowe nie `Custom Event` deklaracja wymaga `As` klauzuli po nazwie zdarzeń, który jawnie określa typ delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3d8b9-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="3d8b9-104">Zdarzenia niestandardowe nie mogą być zdefiniowane przy użyciu `As` klauzuli jawny typ delegata, a z parametrem listy natychmiast po nazwie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3d8b9-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="3d8b9-105">**Identyfikator błędu:** BC31122</span><span class="sxs-lookup"><span data-stu-id="3d8b9-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3d8b9-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="3d8b9-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="3d8b9-107">Zdefiniowanie pełnomocnika z tej samej listy parametrów jako zdarzenie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="3d8b9-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="3d8b9-108">Na przykład jeśli `Custom Event` został zdefiniowany przez `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, a następnie odpowiedniego delegata będą naliczane w następujący.</span><span class="sxs-lookup"><span data-stu-id="3d8b9-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="3d8b9-109">Zastąp zdarzenie niestandardowe z listy parametrów `As` klauzuli określający typ delegata.</span><span class="sxs-lookup"><span data-stu-id="3d8b9-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="3d8b9-110">Kontynuując w przykładzie `Custom Event` deklaracja może zostać przepisane, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3d8b9-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="3d8b9-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d8b9-111">Example</span></span>  
 <span data-ttu-id="3d8b9-112">W tym przykładzie deklaruje `Custom Event` i określa wymagane `As` klauzuli z typem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="3d8b9-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3d8b9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d8b9-113">See also</span></span>
- [<span data-ttu-id="3d8b9-114">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3d8b9-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="3d8b9-115">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3d8b9-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="3d8b9-116">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3d8b9-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
