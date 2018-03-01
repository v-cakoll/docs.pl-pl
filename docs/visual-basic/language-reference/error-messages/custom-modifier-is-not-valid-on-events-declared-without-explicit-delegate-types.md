---
title: "&#39; Niestandardowe &#39; Modyfikator jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 844bd033ea05e373b04a04f80777af77179c1263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="7f5e0-102">&#39; Niestandardowe &#39; Modyfikator jest nieprawidłowy w zdarzeniach deklarowanych bez jawnych typów delegowanych</span><span class="sxs-lookup"><span data-stu-id="7f5e0-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="7f5e0-103">W przeciwieństwie do zdarzeń niestandardowych z systemem innym niż `Custom Event` deklaracja wymaga `As` klauzuli po nazwie zdarzenia, która jawnie określa typ delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7f5e0-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="7f5e0-104">Zdarzenia niestandardowe nie może być zdefiniowany za pomocą `As` klauzuli i jawnych typ delegata lub z parametrem listy natychmiast po nazwie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7f5e0-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="7f5e0-105">**Identyfikator błędu:** BC31122</span><span class="sxs-lookup"><span data-stu-id="7f5e0-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7f5e0-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="7f5e0-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7f5e0-107">Zdefiniuj delegata o tej samej listy parametrów jako zdarzenie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="7f5e0-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="7f5e0-108">Na przykład jeśli `Custom Event` został zdefiniowany przez `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, a następnie odpowiedniego delegata będą następujące.</span><span class="sxs-lookup"><span data-stu-id="7f5e0-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="7f5e0-109">Zastąp parametr listę niestandardowych zdarzeń z `As` klauzuli Określanie typu obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="7f5e0-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="7f5e0-110">Przykładzie, `Custom Event` deklaracji będzie ponownie zapisać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="7f5e0-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="7f5e0-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f5e0-111">Example</span></span>  
 <span data-ttu-id="7f5e0-112">W tym przykładzie deklaruje `Custom Event` i określa wymaganych `As` klauzuli z typem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="7f5e0-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7f5e0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f5e0-113">See Also</span></span>  
 [<span data-ttu-id="7f5e0-114">Event — instrukcja</span><span class="sxs-lookup"><span data-stu-id="7f5e0-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="7f5e0-115">Delegate — instrukcja</span><span class="sxs-lookup"><span data-stu-id="7f5e0-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="7f5e0-116">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7f5e0-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
