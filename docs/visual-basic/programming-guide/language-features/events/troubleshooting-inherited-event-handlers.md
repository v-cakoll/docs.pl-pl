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
ms.openlocfilehash: 4e7bedd1de5197fcf8b69091f4cc878f41b01cd5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405109"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="d3c47-102">Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3c47-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="d3c47-103">W tym temacie wymieniono typowe problemy związane z obsługą zdarzeń w składnikach dziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="d3c47-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="d3c47-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="d3c47-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="d3c47-105">Kod w obsłudze zdarzeń jest wykonywany dwukrotnie dla każdego wywołania</span><span class="sxs-lookup"><span data-stu-id="d3c47-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="d3c47-106">Dziedziczona procedura obsługi zdarzeń nie może zawierać klauzuli [Handles](../../../language-reference/statements/handles-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="d3c47-106">An inherited event handler must not include a [Handles](../../../language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="d3c47-107">Metoda w klasie bazowej jest już skojarzona ze zdarzeniem i zostanie odpowiednio wyzwolona.</span><span class="sxs-lookup"><span data-stu-id="d3c47-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="d3c47-108">Usuń `Handles` klauzulę z dziedziczonej metody.</span><span class="sxs-lookup"><span data-stu-id="d3c47-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="d3c47-109">Jeśli dziedziczona Metoda nie ma `Handles` słowa kluczowego, sprawdź, czy Twój kod nie zawiera dodatkowej [instrukcji AddHandler](../../../language-reference/statements/addhandler-statement.md) ani żadnych dodatkowych metod, które obsługują to samo zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d3c47-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c47-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3c47-110">See also</span></span>

- [<span data-ttu-id="d3c47-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d3c47-111">Events</span></span>](index.md)
