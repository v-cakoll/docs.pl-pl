---
title: 'Porady: przenoszenie danych do zmiennej i z niej (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fefb1979e35cd7b5fa1917f8f1a57af575e51234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="700d4-102">Porady: przenoszenie danych do zmiennej i z niej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="700d4-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="700d4-103">Wartości są przechowywane w zmiennej ustawiając nazwę zmiennej po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="700d4-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="700d4-104">Wprowadzanie danych w zmiennej</span><span class="sxs-lookup"><span data-stu-id="700d4-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="700d4-105">Do przechowywania wartości w zmiennej</span><span class="sxs-lookup"><span data-stu-id="700d4-105">To store a value in a variable</span></span>  
  
-   <span data-ttu-id="700d4-106">Po lewej stronie instrukcji przypisania, użyj nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="700d4-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="700d4-107">W poniższym przykładzie ustawiono wartość zmiennej `alpha`.</span><span class="sxs-lookup"><span data-stu-id="700d4-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="700d4-108">Wartość generowane po prawej stronie instrukcji przypisania jest przechowywana w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="700d4-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="700d4-109">Pobieranie danych ze zmienną</span><span class="sxs-lookup"><span data-stu-id="700d4-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="700d4-110">Możesz pobrać wartość zmiennej, łącznie z nazwą zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="700d4-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="700d4-111">Aby pobrać wartość zmiennej</span><span class="sxs-lookup"><span data-stu-id="700d4-111">To retrieve a value from a variable</span></span>  
  
-   <span data-ttu-id="700d4-112">Użyj nazwy zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="700d4-112">Use the variable name in an expression.</span></span> <span data-ttu-id="700d4-113">Można użyć zmiennej dowolnym służy stałą lub literałem, z wyjątkiem w wyrażeniu, który definiuje wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="700d4-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="700d4-114">—lub—</span><span class="sxs-lookup"><span data-stu-id="700d4-114">-or-</span></span>  
  
-   <span data-ttu-id="700d4-115">Użyj nazwy zmiennej po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="700d4-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="700d4-116">Poniższy przykład odczytuje wartość zmiennej `startValue` , a następnie używa wartości zmiennej `counter` w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="700d4-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="700d4-117">Wartość zmiennej uczestniczy w wyrażeniu, tak jak będzie stałą, a następnie jest ona przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="700d4-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700d4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="700d4-118">See Also</span></span>  
 [<span data-ttu-id="700d4-119">Zmienne</span><span class="sxs-lookup"><span data-stu-id="700d4-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="700d4-120">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="700d4-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="700d4-121">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="700d4-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
