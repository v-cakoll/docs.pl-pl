---
title: 'Porady: przenoszenie danych do zmiennej i z niej'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bc5a7377a5e2e4c7ebe7291fd5f0093c4d6e996d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346902"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="e6a94-102">Porady: przenoszenie danych do zmiennej i z niej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6a94-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>

<span data-ttu-id="e6a94-103">Wartość jest przechowywana w zmiennej przez umieszczenie nazwy zmiennej po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="e6a94-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>

## <a name="putting-data-in-a-variable"></a><span data-ttu-id="e6a94-104">Umieszczanie danych w zmiennej</span><span class="sxs-lookup"><span data-stu-id="e6a94-104">Putting Data in a Variable</span></span>

#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="e6a94-105">Aby zapisać wartość w zmiennej</span><span class="sxs-lookup"><span data-stu-id="e6a94-105">To store a value in a variable</span></span>

- <span data-ttu-id="e6a94-106">Użyj nazwy zmiennej po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="e6a94-106">Use the variable name on the left side of an assignment statement.</span></span>

    <span data-ttu-id="e6a94-107">Poniższy przykład ustawia wartość zmiennej `alpha`.</span><span class="sxs-lookup"><span data-stu-id="e6a94-107">The following example sets the value of the variable `alpha`.</span></span>

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    <span data-ttu-id="e6a94-108">Wartość wygenerowana po prawej stronie instrukcji przypisania jest przechowywana w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e6a94-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>

## <a name="getting-data-from-a-variable"></a><span data-ttu-id="e6a94-109">Pobieranie danych ze zmiennej</span><span class="sxs-lookup"><span data-stu-id="e6a94-109">Getting Data from a Variable</span></span>

<span data-ttu-id="e6a94-110">Wartość zmiennej jest pobierana przez dołączenie nazwy zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="e6a94-110">You retrieve a variable's value by including the variable name in an expression.</span></span>

#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="e6a94-111">Aby pobrać wartość ze zmiennej</span><span class="sxs-lookup"><span data-stu-id="e6a94-111">To retrieve a value from a variable</span></span>

- <span data-ttu-id="e6a94-112">Użyj nazwy zmiennej w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="e6a94-112">Use the variable name in an expression.</span></span> <span data-ttu-id="e6a94-113">Możesz użyć zmiennej wszędzie tam, gdzie można użyć stałej lub literału, z wyjątkiem wyrażenia, które definiuje wartość stałej.</span><span class="sxs-lookup"><span data-stu-id="e6a94-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>

  <span data-ttu-id="e6a94-114">\-lub-</span><span class="sxs-lookup"><span data-stu-id="e6a94-114">\-or-</span></span>

- <span data-ttu-id="e6a94-115">Użyj nazwy zmiennej po znaku równości (`=`) w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="e6a94-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>

  <span data-ttu-id="e6a94-116">Poniższy przykład odczytuje wartość zmiennej `startValue` a następnie używa wartości zmiennej `counter` w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="e6a94-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  <span data-ttu-id="e6a94-117">Wartość zmiennej uczestniczy w wyrażeniu tak samo jak stała, a następnie jest przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="e6a94-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6a94-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6a94-118">See also</span></span>

- [<span data-ttu-id="e6a94-119">Zmienne</span><span class="sxs-lookup"><span data-stu-id="e6a94-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="e6a94-120">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="e6a94-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="e6a94-121">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="e6a94-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
