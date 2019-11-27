---
title: Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: fd2ef1c25233cc1eaad6bcde68923688393b471d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345106"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="8a391-102">Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8a391-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="8a391-103">W tym temacie wymieniono typowe problemy związane z obsługą zdarzeń w składnikach dziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="8a391-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8a391-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="8a391-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="8a391-105">Kod w obsłudze zdarzeń jest wykonywany dwukrotnie dla każdego wywołania</span><span class="sxs-lookup"><span data-stu-id="8a391-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="8a391-106">Dziedziczona procedura obsługi zdarzeń nie może zawierać klauzuli [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="8a391-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="8a391-107">Metoda w klasie bazowej jest już skojarzona ze zdarzeniem i zostanie odpowiednio wyzwolona.</span><span class="sxs-lookup"><span data-stu-id="8a391-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="8a391-108">Usuń klauzulę `Handles` z dziedziczonej metody.</span><span class="sxs-lookup"><span data-stu-id="8a391-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="8a391-109">Jeśli dziedziczona Metoda nie ma słowa kluczowego `Handles`, należy sprawdzić, czy kod nie zawiera dodatkowej [instrukcji AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ani żadnych dodatkowych metod, które obsługują to samo zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="8a391-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a391-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a391-110">See also</span></span>

- [<span data-ttu-id="8a391-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8a391-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
