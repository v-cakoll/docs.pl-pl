---
title: Przeciążanie elementu członkowskiego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353177"
---
# <a name="member-overloading"></a><span data-ttu-id="9102f-102">Przeciążanie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="9102f-102">Member Overloading</span></span>
<span data-ttu-id="9102f-103">Przeciążanie elementu członkowskiego oznacza, że tworzenie dwóch lub więcej elementów członkowskich do tego samego typu, które różnią się jedynie liczby lub typu parametrów, ale mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="9102f-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="9102f-104">Na przykład w następujących `WriteLine` jest przeciążona metoda:</span><span class="sxs-lookup"><span data-stu-id="9102f-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="9102f-105">Ponieważ metody, konstruktorów i właściwości indeksowanych może mieć parametrów, tylko te elementy Członkowskie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="9102f-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="9102f-106">Przeciążenie jest jednym z najważniejszych technik dla poprawy użyteczność, produktywności i czytelności biblioteki do ponownego wykorzystania.</span><span class="sxs-lookup"><span data-stu-id="9102f-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="9102f-107">Przeciążanie liczby parametrów umożliwia zapewnienie prostsze wersje konstruktorów i metod.</span><span class="sxs-lookup"><span data-stu-id="9102f-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="9102f-108">Przeciążenie dla typu parametru umożliwia do korzystania z tej samej nazwy elementu członkowskiego dla elementów członkowskich, wykonywanie operacji identyczne na wybranym zestawem różnych typów.</span><span class="sxs-lookup"><span data-stu-id="9102f-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="9102f-109">**✓ DO** próby Użyj nazwy opisowej parametrów, aby wskazać, wartość domyślna używana przez krótszy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="9102f-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="9102f-110">**X AVOID** arbitralnie różne nazwy parametrów w przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="9102f-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="9102f-111">Jeśli parametr w kilkoma przeciążeniami przedstawia to samo wejście jako parametr w innego przeciążenia metody, parametry powinny mieć taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="9102f-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="9102f-112">**X AVOID** niespójne w kolejności parametrów w przeciążeniu elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="9102f-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="9102f-113">Parametry o takiej samej nazwie powinna pojawić się w tej samej pozycji w wszystkie przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="9102f-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="9102f-114">**✓ DO** Tworzenie wirtualnego najdłuższym przeciążenia (Jeśli wymagane jest rozszerzalności).</span><span class="sxs-lookup"><span data-stu-id="9102f-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="9102f-115">Przeciążenia krótszy należy po prostu wykonywać wywołania za pośrednictwem dłużej przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="9102f-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="9102f-116">**X DO NOT** użyj `ref` lub `out` Modyfikatory do przeciążenia elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="9102f-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="9102f-117">W przypadku niektórych języków nie można rozpoznać wywołania przeciążenia następująco.</span><span class="sxs-lookup"><span data-stu-id="9102f-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="9102f-118">Ponadto takimi przeciążeniami zazwyczaj mają całkowicie różną semantykę i prawdopodobnie nie powinny być przeciążenia, ale dwie odrębne metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="9102f-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="9102f-119">**X DO NOT** mają przeciążenia z parametrami w tej samej pozycji i podobnych typów jeszcze z różnych semantyki.</span><span class="sxs-lookup"><span data-stu-id="9102f-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="9102f-120">**✓ DO** Zezwalaj `null` do przekazania na argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="9102f-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="9102f-121">**✓ DO** używać elementu członkowskiego przeładowanie, a nie Definiowanie elementów członkowskich z argumentami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="9102f-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="9102f-122">Argumenty domyślne nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="9102f-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="9102f-123">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="9102f-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9102f-124">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="9102f-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9102f-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9102f-125">See also</span></span>

- [<span data-ttu-id="9102f-126">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="9102f-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="9102f-127">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="9102f-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
