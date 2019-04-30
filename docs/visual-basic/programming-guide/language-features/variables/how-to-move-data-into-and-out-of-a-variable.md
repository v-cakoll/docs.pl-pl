---
title: 'Instrukcje: Przenoszenie danych do i z zmiennej (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 30d1c0ab91724ac556e59b272782513ee8b8067b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756601"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="7b06a-102">Instrukcje: Przenoszenie danych do i z zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b06a-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="7b06a-103">Wartość jest przechowywana w zmiennej, umieszczając nazwę zmiennej po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="7b06a-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="7b06a-104">Umieszczenie danych w zmiennej</span><span class="sxs-lookup"><span data-stu-id="7b06a-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="7b06a-105">Do przechowywania wartości w zmiennej</span><span class="sxs-lookup"><span data-stu-id="7b06a-105">To store a value in a variable</span></span>  
  
- <span data-ttu-id="7b06a-106">Użyj nazwy zmiennej po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="7b06a-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="7b06a-107">W poniższym przykładzie ustawiono wartość zmiennej `alpha`.</span><span class="sxs-lookup"><span data-stu-id="7b06a-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="7b06a-108">Wartość generowane po prawej stronie instrukcji przypisania są przechowywane w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7b06a-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="7b06a-109">Pobieranie danych ze zmiennej</span><span class="sxs-lookup"><span data-stu-id="7b06a-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="7b06a-110">Aby uzyskać wartość zmiennej, łącznie z nazwą zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="7b06a-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="7b06a-111">Aby pobrać wartość ze zmiennej</span><span class="sxs-lookup"><span data-stu-id="7b06a-111">To retrieve a value from a variable</span></span>  
  
- <span data-ttu-id="7b06a-112">Użyj nazwy zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="7b06a-112">Use the variable name in an expression.</span></span> <span data-ttu-id="7b06a-113">Można użyć zmiennej dowolnego miejsca umożliwia stałą lub literałem, z wyjątkiem w wyrażeniu, który definiuje wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="7b06a-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="7b06a-114">—lub—</span><span class="sxs-lookup"><span data-stu-id="7b06a-114">-or-</span></span>  
  
- <span data-ttu-id="7b06a-115">Użyj nazwy zmiennej po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="7b06a-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="7b06a-116">Poniższy przykład odczytuje wartość zmiennej `startValue` , a następnie używa wartości zmiennej `counter` w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="7b06a-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="7b06a-117">Wartość zmiennej uczestniczy w wyrażeniu, tak jak będzie stałą, a następnie jest on przechowywany w zmiennej lub właściwość po lewej stronie w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="7b06a-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b06a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b06a-118">See also</span></span>

- [<span data-ttu-id="7b06a-119">Zmienne</span><span class="sxs-lookup"><span data-stu-id="7b06a-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="7b06a-120">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="7b06a-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="7b06a-121">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="7b06a-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
