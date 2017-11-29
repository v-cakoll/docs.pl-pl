---
title: '&#39; &lt;typename&gt;&#39; jest to typ delegowany'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords: BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="a87f3-102">&#39; &lt;typename&gt;&#39; jest to typ delegowany</span><span class="sxs-lookup"><span data-stu-id="a87f3-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="a87f3-103">"\<typename >" jest typem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="a87f3-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="a87f3-104">Delegat konstrukcji zezwala na tylko jedno wyrażenie AddressOf jako listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="a87f3-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="a87f3-105">Wyrażenia AddressOf można często zamiast konstrukcji obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="a87f3-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="a87f3-106">A `New` klauzuli tworzenia wystąpienia klasy delegata dostarcza listy nieprawidłowy argument do konstruktora delegata.</span><span class="sxs-lookup"><span data-stu-id="a87f3-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="a87f3-107">Można podać tylko jeden `AddressOf` wyrażenie podczas tworzenia nowego wystąpienia obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="a87f3-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="a87f3-108">Ten błąd może spowodować żadnych argumentów nie jest przekazywany do konstruktora delegata, jeśli przekazać więcej niż jeden argument lub w przypadku przekazania pojedynczy argument który nie jest prawidłową `AddressOf` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a87f3-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="a87f3-109">**Identyfikator błędu:** BC32008</span><span class="sxs-lookup"><span data-stu-id="a87f3-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a87f3-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a87f3-110">To correct this error</span></span>  
  
-   <span data-ttu-id="a87f3-111">Użyj pojedynczego `AddressOf` wyrażenia argumentu na liście w klasie obiektów delegowanych `New` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a87f3-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87f3-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a87f3-112">See Also</span></span>  
 [<span data-ttu-id="a87f3-113">New — Operator</span><span class="sxs-lookup"><span data-stu-id="a87f3-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="a87f3-114">AddressOf — Operator</span><span class="sxs-lookup"><span data-stu-id="a87f3-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="a87f3-115">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="a87f3-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="a87f3-116">Porady: wywoływanie metody delegata</span><span class="sxs-lookup"><span data-stu-id="a87f3-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
