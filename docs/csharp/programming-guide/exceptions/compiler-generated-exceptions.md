---
title: Wyjątki wygenerowane przez kompilator — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705317"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="ce088-102">Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ce088-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="ce088-103">Niektóre wyjątki są generowane automatycznie przez program runtime wspólnego języka .NET Framework (CLR), gdy podstawowe operacje nie powiodą się.</span><span class="sxs-lookup"><span data-stu-id="ce088-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="ce088-104">Te wyjątki i ich warunki błędu są wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="ce088-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="ce088-105">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="ce088-105">Exception</span></span>|<span data-ttu-id="ce088-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ce088-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="ce088-107">Klasa podstawowa dla wyjątków występujących podczas operacji <xref:System.DivideByZeroException> arytmetycznych, takich jak i <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="ce088-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="ce088-108">Generowane, gdy tablica nie może przechowywać danego elementu, ponieważ rzeczywisty typ elementu jest niezgodny z rzeczywistym typem tablicy.</span><span class="sxs-lookup"><span data-stu-id="ce088-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="ce088-109">Thrown, gdy podejmowano próbę podzielenia wartości integralnej przez zero.</span><span class="sxs-lookup"><span data-stu-id="ce088-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="ce088-110">Generowane podczas próby indeksowania tablicy, gdy indeks jest mniejszy niż zero lub poza granicami tablicy.</span><span class="sxs-lookup"><span data-stu-id="ce088-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="ce088-111">Generowane, gdy jawna konwersja z typu podstawowego do interfejsu lub typu pochodnego kończy się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ce088-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="ce088-112">Generowane, gdy podejmowano próbę odwołania się do obiektu, którego wartość jest [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="ce088-112">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="ce088-113">Generowane, gdy próba przydzielenia pamięci przy użyciu [nowego](../../language-reference/operators/new-operator.md) operatora nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="ce088-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="ce088-114">Oznacza to, że pamięć dostępna dla wspólnego języka w czasie wykonywania została wyczerpana.</span><span class="sxs-lookup"><span data-stu-id="ce088-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="ce088-115">Generowane, gdy operacja arytmetyczna w `checked` kontekście przepełnia.</span><span class="sxs-lookup"><span data-stu-id="ce088-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="ce088-116">Generowane, gdy stos wykonania jest wyczerpany przez zbyt wiele wywołań metody oczekujące; zazwyczaj wskazuje na bardzo głęboką lub nieskończoną rekursję.</span><span class="sxs-lookup"><span data-stu-id="ce088-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="ce088-117">Generowane, gdy konstruktor statyczny `catch` zgłasza wyjątek i nie istnieje zgodna klauzula, aby go przechwycić.</span><span class="sxs-lookup"><span data-stu-id="ce088-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce088-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce088-118">See also</span></span>

- [<span data-ttu-id="ce088-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ce088-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ce088-120">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="ce088-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="ce088-121">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="ce088-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="ce088-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="ce088-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="ce088-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="ce088-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="ce088-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="ce088-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
