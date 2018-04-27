---
title: Przeciążenie elementu członkowskiego
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 546db0540cf7852b40678476f732663369b15824
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="member-overloading"></a><span data-ttu-id="94391-102">Przeciążenie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="94391-102">Member Overloading</span></span>
<span data-ttu-id="94391-103">Przeciążenie elementu członkowskiego oznacza, że utworzenie dwóch lub więcej elementów członkowskich do tego samego typu, które różnią się jedynie liczby lub typów parametrów, ale mają taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="94391-103">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="94391-104">Na przykład w poniższych `WriteLine` metody jest przeciążona:</span><span class="sxs-lookup"><span data-stu-id="94391-104">For example, in the following, the `WriteLine` method is overloaded:</span></span>  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 <span data-ttu-id="94391-105">Ponieważ metody, konstruktorów i właściwości indeksowanych może mieć parametrów, tylko te elementy Członkowskie mogą być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="94391-105">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>  
  
 <span data-ttu-id="94391-106">Przeciążanie jest jednym z najważniejszych technik dla poprawy użyteczność, wydajności i czytelność biblioteki do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="94391-106">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="94391-107">Przeciążanie liczby parametrów umożliwia zapewnienie prostsze wersje konstruktory i metody.</span><span class="sxs-lookup"><span data-stu-id="94391-107">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="94391-108">Przeciążanie na typ parametru umożliwia Użyj takiej samej nazwie elementu członkowskiego dla operacji identyczne na wybrany zestaw różnych typów elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="94391-108">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>  
  
 <span data-ttu-id="94391-109">**CZY ✓** próby Użyj nazwy opisowej parametrów, aby wskazać, wartość domyślna używana przez krótszy przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="94391-109">**✓ DO** try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>  
  
 <span data-ttu-id="94391-110">**X należy UNIKAĆ** arbitralnie różne nazwy parametrów w przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="94391-110">**X AVOID** arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="94391-111">Jeśli parametr w przeciążeniami reprezentuje dane wejściowe tego samego jako parametru w innego przeciążenia, parametry muszą mieć taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="94391-111">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>  
  
 <span data-ttu-id="94391-112">**X należy UNIKAĆ** niespójne w kolejności parametrów w przeciążeniu elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="94391-112">**X AVOID** being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="94391-113">Parametry o takiej samej nazwie powinna pojawić się w tej samej pozycji w wszystkie przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="94391-113">Parameters with the same name should appear in the same position in all overloads.</span></span>  
  
 <span data-ttu-id="94391-114">**CZY ✓** Tworzenie wirtualnego najdłuższym przeciążenia (Jeśli wymagane jest rozszerzalności).</span><span class="sxs-lookup"><span data-stu-id="94391-114">**✓ DO** make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="94391-115">Przeciążenia krótszą po prostu powinny wywoływać za pomocą przeciążenia dłużej.</span><span class="sxs-lookup"><span data-stu-id="94391-115">Shorter overloads should simply call through to a longer overload.</span></span>  
  
 <span data-ttu-id="94391-116">**X nie** użyj `ref` lub `out` Modyfikatory do przeciążenia elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="94391-116">**X DO NOT** use `ref` or `out` modifiers to overload members.</span></span>  
  
 <span data-ttu-id="94391-117">W przypadku niektórych języków nie można rozpoznać wywołania przeciążenia następująco.</span><span class="sxs-lookup"><span data-stu-id="94391-117">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="94391-118">Ponadto takie przeciążenia zwykle ma semantykę różną całkowicie i prawdopodobnie nie powinien być przeciążenia, ale dwa oddzielne metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="94391-118">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>  
  
 <span data-ttu-id="94391-119">**X nie** mają przeciążenia z parametrami w tej samej pozycji i podobnych typów jeszcze z różnych semantyki.</span><span class="sxs-lookup"><span data-stu-id="94391-119">**X DO NOT** have overloads with parameters at the same position and similar types yet with different semantics.</span></span>  
  
 <span data-ttu-id="94391-120">**CZY ✓** Zezwalaj `null` do przekazania na argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="94391-120">**✓ DO**  allow `null` to be passed for optional arguments.</span></span>  
  
 <span data-ttu-id="94391-121">**CZY ✓** używać elementu członkowskiego przeładowanie, a nie Definiowanie elementów członkowskich z argumentami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="94391-121">**✓ DO** use member overloading rather than defining members with default arguments.</span></span>  
  
 <span data-ttu-id="94391-122">Argumenty domyślne nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="94391-122">Default arguments are not CLS compliant.</span></span>  
  
 <span data-ttu-id="94391-123">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="94391-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="94391-124">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="94391-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94391-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94391-125">See Also</span></span>  
 [<span data-ttu-id="94391-126">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="94391-126">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="94391-127">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="94391-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
