---
title: Kopiowanie wartości parametru „ByRef” <parametername>” z powrotem do pasującego argumentu powoduje zawężenie typu „<typename1>” do typu „<typename2>”.
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: bac5f9a88df719bc64a8b0541f65e5912275866e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409754"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a><span data-ttu-id="1af08-102">Kopiowanie wartości parametru „ByRef” \<parametername>” z powrotem do pasującego argumentu powoduje zawężenie typu „\<typename1>” do typu „\<typename2>”.</span><span class="sxs-lookup"><span data-stu-id="1af08-102">Copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument narrows from type '\<typename1>' to type '\<typename2>'</span></span>
<span data-ttu-id="1af08-103">Procedura jest wywoływana z argumentem, który jest poszerzany do odpowiedniego typu parametru, a konwersja z parametru do argumentu jest zawężana.</span><span class="sxs-lookup"><span data-stu-id="1af08-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="1af08-104">Podczas definiowania klasy lub struktury można zdefiniować jeden lub więcej operatorów konwersji, aby przekonwertować tę klasę lub typ struktury na inne typy.</span><span class="sxs-lookup"><span data-stu-id="1af08-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="1af08-105">Można również zdefiniować operatory konwersji odwrotnej, aby przekonwertować te inne typy z powrotem na klasę lub typ struktury.</span><span class="sxs-lookup"><span data-stu-id="1af08-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="1af08-106">Jeśli używasz klasy lub typu struktury w wywołaniu procedury, Visual Basic może użyć tych operatorów konwersji do przekonwertowania typu argumentu na typ odpowiadającego mu parametru.</span><span class="sxs-lookup"><span data-stu-id="1af08-106">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="1af08-107">W przypadku przekazania argumentu [ByRef](../modifiers/byref.md), Visual Basic czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, zamiast przekazywać odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1af08-107">If you pass the argument [ByRef](../modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="1af08-108">W takim przypadku, gdy procedura zwraca, Visual Basic należy skopiować wartość zmiennej lokalnej z powrotem do argumentu w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="1af08-108">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="1af08-109">Jeśli `ByRef` wartość argumentu jest kopiowana do procedury, a argument i parametr są tego samego typu, konwersja nie jest konieczna.</span><span class="sxs-lookup"><span data-stu-id="1af08-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="1af08-110">Ale jeśli typy są różne, Visual Basic muszą być konwertowane w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="1af08-110">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="1af08-111">Jeśli jeden z typów jest klasą lub typem struktury, Visual Basic musi przekonwertować go zarówno do, jak i z innego typu.</span><span class="sxs-lookup"><span data-stu-id="1af08-111">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="1af08-112">Jeśli jedno z tych konwersji jest rozszerzane, konwersja odwrotna może ulec zawężaniu.</span><span class="sxs-lookup"><span data-stu-id="1af08-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="1af08-113">**Identyfikator błędu:** BC32053</span><span class="sxs-lookup"><span data-stu-id="1af08-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1af08-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1af08-114">To correct this error</span></span>  
  
- <span data-ttu-id="1af08-115">Jeśli to możliwe, użyj argumentu wywołującego tego samego typu co parametr procedury, więc Visual Basic nie musi wykonywać żadnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="1af08-115">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="1af08-116">Jeśli musisz wywołać procedurę z typem argumentu innym niż typ parametru, ale nie musisz zwracać wartości do argumentu wywołującego, zdefiniuj parametr jako [ByVal](../modifiers/byval.md) zamiast `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="1af08-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>  
  
- <span data-ttu-id="1af08-117">Jeśli musisz zwrócić wartość do argumentu wywołującego, zdefiniuj Operator konwersji odwrotnej jako [rozszerzający](../modifiers/widening.md), jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="1af08-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af08-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1af08-118">See also</span></span>

- [<span data-ttu-id="1af08-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="1af08-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="1af08-120">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="1af08-120">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1af08-121">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="1af08-121">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="1af08-122">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="1af08-122">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="1af08-123">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="1af08-123">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="1af08-124">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="1af08-124">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="1af08-125">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="1af08-125">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="1af08-126">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1af08-126">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="1af08-127">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="1af08-127">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
