---
title: Wyjątki generowane przez kompilator — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 1d2d561df3e496893657b050fa93b44c56542d97
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240736"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="d17b6-102">Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d17b6-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>

<span data-ttu-id="d17b6-103">Niektóre wyjątki są generowane automatycznie przez środowisko uruchomieniowe .NET, gdy podstawowe operacje zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d17b6-103">Some exceptions are thrown automatically by the .NET runtime when basic operations fail.</span></span> <span data-ttu-id="d17b6-104">Te wyjątki i ich warunki błędu są wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d17b6-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="d17b6-105">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="d17b6-105">Exception</span></span>|<span data-ttu-id="d17b6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d17b6-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="d17b6-107">Klasa bazowa dla wyjątków, które występują podczas operacji arytmetycznych, takich jak <xref:System.DivideByZeroException> i <xref:System.OverflowException> .</span><span class="sxs-lookup"><span data-stu-id="d17b6-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="d17b6-108">Zgłaszany, gdy tablica nie może przechowywać danego elementu, ponieważ rzeczywisty typ elementu jest niezgodny z rzeczywistym typem tablicy.</span><span class="sxs-lookup"><span data-stu-id="d17b6-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="d17b6-109">Zgłaszany, gdy podejmowana jest próba dzielenia wartości całkowitej przez zero.</span><span class="sxs-lookup"><span data-stu-id="d17b6-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="d17b6-110">Zgłaszany, gdy podejmowana jest próba indeksowania tablicy, gdy indeks jest mniejszy od zera lub poza granicami tablicy.</span><span class="sxs-lookup"><span data-stu-id="d17b6-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="d17b6-111">Zgłaszany, gdy jawna konwersja z typu podstawowego do interfejsu lub typu pochodnego kończy się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d17b6-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="d17b6-112">Zgłaszany, gdy podejmowana jest próba odwołująca się do obiektu, którego wartość jest [równa null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="d17b6-112">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="d17b6-113">Zgłaszany, gdy próba przydzielenia pamięci przy użyciu operatora [New](../../language-reference/operators/new-operator.md) zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d17b6-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="d17b6-114">Oznacza to wyczerpanie pamięci dostępnej dla środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="d17b6-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="d17b6-115">Zgłaszane w przypadku przepełnienia operacji arytmetycznej w `checked` kontekście.</span><span class="sxs-lookup"><span data-stu-id="d17b6-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="d17b6-116">Zgłaszany, gdy stos wykonywania został wyczerpany przez zbyt wiele oczekujących wywołań metod; zwykle wskazuje bardzo głęboką lub nieskończoną rekursję.</span><span class="sxs-lookup"><span data-stu-id="d17b6-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="d17b6-117">Zgłaszany, gdy Konstruktor statyczny zgłasza wyjątek i nie `catch` istnieje zgodna klauzula, aby ją przechwycić.</span><span class="sxs-lookup"><span data-stu-id="d17b6-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d17b6-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d17b6-118">See also</span></span>

- [<span data-ttu-id="d17b6-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d17b6-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d17b6-120">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="d17b6-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="d17b6-121">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="d17b6-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="d17b6-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="d17b6-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="d17b6-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="d17b6-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="d17b6-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="d17b6-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
