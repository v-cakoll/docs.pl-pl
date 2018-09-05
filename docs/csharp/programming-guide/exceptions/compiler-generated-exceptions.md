---
title: Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 476f5940b0b93d0c28bcd2bc9ca73147bc7bf3eb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558931"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="f34fd-102">Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f34fd-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="f34fd-103">Niektóre wyjątki są zgłaszane w automatycznie przez .NET Framework środowisko uruchomieniowe języka wspólnego (CLR), gdy podstawowe operacje kończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f34fd-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="f34fd-104">W poniższej tabeli wymieniono te wyjątki i ich warunków błędów.</span><span class="sxs-lookup"><span data-stu-id="f34fd-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="f34fd-105">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="f34fd-105">Exception</span></span>|<span data-ttu-id="f34fd-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f34fd-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="f34fd-107">Klasa bazowa dla wyjątków, które występują podczas operacje arytmetyczne, takie jak <xref:System.DivideByZeroException> i <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="f34fd-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="f34fd-108">Element zgłaszany, gdy tablica nie można zapisać danego elementu, ponieważ rzeczywisty typ elementu jest niezgodny z rzeczywisty typ tablicy.</span><span class="sxs-lookup"><span data-stu-id="f34fd-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="f34fd-109">Element zgłaszany, gdy podejmowana jest próba dzielenia wartości całkowitej przez zero.</span><span class="sxs-lookup"><span data-stu-id="f34fd-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="f34fd-110">Element zgłaszany, gdy podejmowana jest próba indeksu tablicy, gdy indeks jest mniejsza od zera lub poza granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="f34fd-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="f34fd-111">Element zgłaszany, gdy konwersja jawna z typu podstawowego interfejsu lub typu pochodnego nie powiedzie się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f34fd-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="f34fd-112">Zgłaszany, gdy użytkownik podejmie próbę odwołują się do obiektu, którego wartością jest [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="f34fd-112">Thrown when you attempt to reference an object whose value is [null](../../../csharp/language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="f34fd-113">Zgłaszany, gdy próba przydzielenia pamięci za pomocą [nowe](../../../csharp/language-reference/keywords/new-operator.md) operator nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="f34fd-113">Thrown when an attempt to allocate memory using the [new](../../../csharp/language-reference/keywords/new-operator.md) operator fails.</span></span> <span data-ttu-id="f34fd-114">Oznacza to, dostępna dla środowiska uruchomieniowego języka wspólnego pamięci została wyczerpana.</span><span class="sxs-lookup"><span data-stu-id="f34fd-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="f34fd-115">Zgłaszany, gdy operacja arytmetyczna w `checked` przepełnienia kontekstu.</span><span class="sxs-lookup"><span data-stu-id="f34fd-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="f34fd-116">Zgłaszany, gdy stos wykonywania wyczerpaniu przez zbyt wiele wywołań metod oczekujące; Wskazuje zazwyczaj bardzo szczegółowe lub nieskończoną rekursję.</span><span class="sxs-lookup"><span data-stu-id="f34fd-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="f34fd-117">Zgłaszany, gdy statyczny Konstruktor zgłasza wyjątek i zgodnego `catch` istnieje klauzuli catch go.</span><span class="sxs-lookup"><span data-stu-id="f34fd-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f34fd-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f34fd-118">See Also</span></span>

- [<span data-ttu-id="f34fd-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f34fd-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f34fd-120">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="f34fd-120">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
- [<span data-ttu-id="f34fd-121">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="f34fd-121">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
- [<span data-ttu-id="f34fd-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="f34fd-122">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
- [<span data-ttu-id="f34fd-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="f34fd-123">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
- [<span data-ttu-id="f34fd-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="f34fd-124">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
