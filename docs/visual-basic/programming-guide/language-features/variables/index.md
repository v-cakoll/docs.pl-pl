---
title: Zmienne w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7a47ad7e4ade9f15159c27ac672aeb937a05493
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="0910c-102">Zmienne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0910c-102">Variables in Visual Basic</span></span>
<span data-ttu-id="0910c-103">Często mają do przechowywania wartości podczas wykonywania obliczeń na [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0910c-103">You often have to store values when you perform calculations with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="0910c-104">Na przykład można obliczyć wartości kilku, porównaj je i wykonywać różne operacje, w zależności od wyniku porównania.</span><span class="sxs-lookup"><span data-stu-id="0910c-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="0910c-105">Należy zachować wartości, jeśli chcesz porównać je.</span><span class="sxs-lookup"><span data-stu-id="0910c-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="0910c-106">Użycie</span><span class="sxs-lookup"><span data-stu-id="0910c-106">Usage</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="0910c-107">, podobnie jak większość języków programowania, używane zmienne do przechowywania wartości.</span><span class="sxs-lookup"><span data-stu-id="0910c-107">, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="0910c-108">A *zmiennej* ma nazwę (word, którego używasz do odwoływania się do wartości, która zawiera zmienną).</span><span class="sxs-lookup"><span data-stu-id="0910c-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="0910c-109">Zmienna również ma typ danych (który określa rodzaj danych, które mogą być przechowywane w zmiennej).</span><span class="sxs-lookup"><span data-stu-id="0910c-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="0910c-110">Zmienna może reprezentować tablicy, jeśli ma ona do przechowywania indeksowanego zbiór elementów danych jest blisko związane.</span><span class="sxs-lookup"><span data-stu-id="0910c-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="0910c-111">Wnioskowanie o typie lokalnym umożliwia Zadeklaruj zmienne bez jawne określenie typu danych.</span><span class="sxs-lookup"><span data-stu-id="0910c-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="0910c-112">Zamiast tego kompilator wnioskuje typ zmiennej typu wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="0910c-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="0910c-113">Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) i [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0910c-113">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="0910c-114">Przypisywanie wartości</span><span class="sxs-lookup"><span data-stu-id="0910c-114">Assigning Values</span></span>  
 <span data-ttu-id="0910c-115">Instrukcje przypisania służy do wykonywania obliczeń i przypisz wynik do zmiennej, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0910c-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="0910c-116">Znak równości (`=`) w tym przykładzie jest operatora przypisania nie był operator równości.</span><span class="sxs-lookup"><span data-stu-id="0910c-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="0910c-117">Wartość jest przypisany do zmiennej `applesSold`.</span><span class="sxs-lookup"><span data-stu-id="0910c-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="0910c-118">Aby uzyskać więcej informacji, zobacz [porady: przenoszenie danych do i z zmiennej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="0910c-118">For more information, see [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="0910c-119">Właściwości i zmienne</span><span class="sxs-lookup"><span data-stu-id="0910c-119">Variables and Properties</span></span>  
 <span data-ttu-id="0910c-120">Zmienna, takich jak *właściwość* reprezentuje wartość, której będziesz mieć dostęp.</span><span class="sxs-lookup"><span data-stu-id="0910c-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="0910c-121">Jest jednak bardziej skomplikowane niż zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0910c-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="0910c-122">Właściwość używa bloki kodu, które kontrolują sposób ustawiania i pobierania jej wartość.</span><span class="sxs-lookup"><span data-stu-id="0910c-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="0910c-123">Aby uzyskać więcej informacji, zobacz [różnice pomiędzy właściwościami i zmiennymi w Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="0910c-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0910c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0910c-124">See Also</span></span>  
 [<span data-ttu-id="0910c-125">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="0910c-125">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="0910c-126">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="0910c-126">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="0910c-127">Rozwiązywanie problemów z zmiennych</span><span class="sxs-lookup"><span data-stu-id="0910c-127">Troubleshooting Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)  
 [<span data-ttu-id="0910c-128">Porady: przenoszenie danych do i z zmiennej</span><span class="sxs-lookup"><span data-stu-id="0910c-128">How to: Move Data Into and Out of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [<span data-ttu-id="0910c-129">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0910c-129">Differences Between Properties and Variables in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)  
 [<span data-ttu-id="0910c-130">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="0910c-130">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
