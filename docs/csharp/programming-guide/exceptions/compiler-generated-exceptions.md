---
title: "Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d1417e42f588978d5fc1beca4ad55463502ee219
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="a1c52-102">Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a1c52-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="a1c52-103">Niektóre wyjątki zostaną zgłoszone automatycznie przez .NET Framework środowisko uruchomieniowe języka wspólnego (CLR), gdy podstawowe operacje nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="a1c52-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="a1c52-104">W poniższej tabeli wymieniono te wyjątki i ich warunki błędów.</span><span class="sxs-lookup"><span data-stu-id="a1c52-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="a1c52-105">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="a1c52-105">Exception</span></span>|<span data-ttu-id="a1c52-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a1c52-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="a1c52-107">Klasa podstawowa dla wyjątków występujących podczas operacje arytmetyczne, takie jak <xref:System.DivideByZeroException> i <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="a1c52-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="a1c52-108">Element zgłaszany, gdy tablicy nie może przechowywać danego elementu, ponieważ typ rzeczywistego elementu jest niezgodny z rzeczywisty typ tablicy.</span><span class="sxs-lookup"><span data-stu-id="a1c52-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="a1c52-109">Element zgłaszany, gdy jest podejmowana próba wartością całkowitą dzielenia przez zero.</span><span class="sxs-lookup"><span data-stu-id="a1c52-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="a1c52-110">Element zgłaszany, gdy podejmowana jest próba do indeksu tablicy, gdy indeks jest mniejszy od zera lub poza granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="a1c52-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="a1c52-111">Element zgłaszany, gdy jawna konwersja z typu podstawowego interfejsu lub typu pochodnego nie powiedzie się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a1c52-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="a1c52-112">Wyjątek podczas próby odwołuje się do obiektu, którego wartość jest [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="a1c52-112">Thrown when you attempt to reference an object whose value is [null](../../../csharp/language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="a1c52-113">Element zgłaszany, gdy próba przydzielenia pamięci przy użyciu [nowe](../../../csharp/language-reference/keywords/new-operator.md) operator nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="a1c52-113">Thrown when an attempt to allocate memory using the [new](../../../csharp/language-reference/keywords/new-operator.md) operator fails.</span></span> <span data-ttu-id="a1c52-114">To ustawienie określa wyczerpaniu pamięci dostępnej dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a1c52-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="a1c52-115">Element zgłaszany, gdy w operacji arytmetycznej `checked` przelewa kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a1c52-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="a1c52-116">Element zgłaszany, gdy stos wykonywania wyczerpaniem przez zbyt wiele wywołań metody oczekujące; zwykle wskazuje bardzo bezpośrednich lub nieskończoną rekursję.</span><span class="sxs-lookup"><span data-stu-id="a1c52-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="a1c52-117">Element zgłaszany, gdy Konstruktor statyczny zgłasza wyjątek i zgodnego `catch` istnieje klauzuli catch go.</span><span class="sxs-lookup"><span data-stu-id="a1c52-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1c52-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1c52-118">See Also</span></span>  
 [<span data-ttu-id="a1c52-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a1c52-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a1c52-120">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="a1c52-120">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="a1c52-121">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="a1c52-121">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [<span data-ttu-id="a1c52-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="a1c52-122">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="a1c52-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="a1c52-123">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="a1c52-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="a1c52-124">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
