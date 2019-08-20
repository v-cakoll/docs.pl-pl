---
title: Wyjątki generowane przez kompilator — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: d0e0a304c8f7d77e7ba5c89b643fc5658c458558
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590369"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="61329-102">Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="61329-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="61329-103">Niektóre wyjątki są generowane automatycznie przez środowisko uruchomieniowe języka wspólnego (CLR) .NET Framework, gdy podstawowe operacje kończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="61329-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="61329-104">Te wyjątki i ich warunki błędu są wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="61329-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="61329-105">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="61329-105">Exception</span></span>|<span data-ttu-id="61329-106">Opis</span><span class="sxs-lookup"><span data-stu-id="61329-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="61329-107">Klasa bazowa dla wyjątków, które występują podczas operacji arytmetycznych, takich <xref:System.DivideByZeroException> jak <xref:System.OverflowException>i.</span><span class="sxs-lookup"><span data-stu-id="61329-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="61329-108">Zgłaszany, gdy tablica nie może przechowywać danego elementu, ponieważ rzeczywisty typ elementu jest niezgodny z rzeczywistym typem tablicy.</span><span class="sxs-lookup"><span data-stu-id="61329-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="61329-109">Zgłaszany, gdy podejmowana jest próba dzielenia wartości całkowitej przez zero.</span><span class="sxs-lookup"><span data-stu-id="61329-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="61329-110">Zgłaszany, gdy podejmowana jest próba indeksowania tablicy, gdy indeks jest mniejszy od zera lub poza granicami tablicy.</span><span class="sxs-lookup"><span data-stu-id="61329-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="61329-111">Zgłaszany, gdy jawna konwersja z typu podstawowego do interfejsu lub typu pochodnego kończy się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="61329-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="61329-112">Zgłaszany podczas próby odwołania się do obiektu, którego wartość jest [równa null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="61329-112">Thrown when you attempt to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="61329-113">Zgłaszany, gdy próba przydzielenia pamięci przy użyciu operatora [New](../../language-reference/operators/new-operator.md) zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="61329-113">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="61329-114">Oznacza to wyczerpanie pamięci dostępnej dla środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="61329-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="61329-115">Zgłaszane w przypadku przepełnienia operacji `checked` arytmetycznej w kontekście.</span><span class="sxs-lookup"><span data-stu-id="61329-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="61329-116">Zgłaszany, gdy stos wykonywania został wyczerpany przez zbyt wiele oczekujących wywołań metod; zwykle wskazuje bardzo głęboką lub nieskończoną rekursję.</span><span class="sxs-lookup"><span data-stu-id="61329-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="61329-117">Zgłaszany, gdy Konstruktor statyczny zgłasza wyjątek i nie `catch` istnieje zgodna klauzula, aby ją przechwycić.</span><span class="sxs-lookup"><span data-stu-id="61329-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61329-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61329-118">See also</span></span>

- [<span data-ttu-id="61329-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="61329-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="61329-120">Wyjątki i obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="61329-120">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="61329-121">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="61329-121">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="61329-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="61329-122">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="61329-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="61329-123">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="61329-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="61329-124">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
