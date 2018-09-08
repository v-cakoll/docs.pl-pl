---
title: Używanie standardowych typów wyjątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ea4a61be3a76c30c564cbf98ba3318fc6c3e7d4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193630"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="a7fa4-102">Używanie standardowych typów wyjątków</span><span class="sxs-lookup"><span data-stu-id="a7fa4-102">Using Standard Exception Types</span></span>
<span data-ttu-id="a7fa4-103">W tej sekcji opisano standardowych wyjątków, które są dostarczane przez platformę i szczegółowe informacje o ich użycia.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="a7fa4-104">Lista w żadnym wypadku nie jest wyczerpująca.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="a7fa4-105">Można znaleźć dokumentację referencyjną .NET Framework użycie innych typów wyjątków Framework.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="a7fa4-106">Wyjątek i SystemException</span><span class="sxs-lookup"><span data-stu-id="a7fa4-106">Exception and SystemException</span></span>  
 <span data-ttu-id="a7fa4-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> lub <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a7fa4-108">**X DO NOT** catch `System.Exception` lub `System.SystemException` w ramach kodu, chyba że planujesz do ponownego zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="a7fa4-109">**X AVOID** Przechwytywanie `System.Exception` lub `System.SystemException`, z wyjątkiem programów obsługi wyjątków najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="a7fa4-110">Applicationexception —</span><span class="sxs-lookup"><span data-stu-id="a7fa4-110">ApplicationException</span></span>  
 <span data-ttu-id="a7fa4-111">**X DO NOT** zgłosić lub pochodzić od <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="a7fa4-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="a7fa4-112">InvalidOperationException</span></span>  
 <span data-ttu-id="a7fa4-113">**✓ DO** throw <xref:System.InvalidOperationException> Jeśli obiekt jest w nieodpowiednim stanie.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="a7fa4-114">ArgumentException ArgumentNullException i Trwa wyjątku ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="a7fa4-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="a7fa4-115">**✓ DO** throw <xref:System.ArgumentException> lub jednego z jego podtypach jeśli złe argumenty są przekazywane do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="a7fa4-116">Preferuj najbardziej pochodny typ wyjątku, jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="a7fa4-117">**✓ DO** ustawić `ParamName` właściwości, gdy jeden podklasy zgłaszanie `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="a7fa4-118">Ta właściwość reprezentuje nazwę parametru, który spowodował zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="a7fa4-119">Należy pamiętać, że właściwość można ustawić przy użyciu jednego z przeciążeń konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="a7fa4-120">**✓ DO** użyj `value` dla nazwy parametru niejawne wartości metody ustawiające właściwości.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="a7fa4-121">Obiektu NullReferenceException IndexOutOfRangeException i AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="a7fa4-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="a7fa4-122">**X DO NOT** Zezwalaj publicznie można wywołać interfejsów API, aby jawnie lub niejawnie throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, lub <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="a7fa4-123">Wyjątki te są zarezerwowane i generowane przez aparat wykonywania i w większości przypadków wskazania błędu.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="a7fa4-124">Wykonaj sprawdzanie, aby uniknąć generowania wyjątków tych argumentów.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="a7fa4-125">Zgłaszanie tych wyjątków przedstawia szczegóły implementacji metody, która może spowodować zmianę wraz z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="a7fa4-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="a7fa4-126">StackOverflowException</span></span>  
 <span data-ttu-id="a7fa4-127">**X DO NOT** jawne zgłaszanie <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="a7fa4-128">Powinny być jawnie wyjątku tylko przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="a7fa4-129">**X DO NOT** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="a7fa4-130">Jest prawie niemożliwe do pisania kodu zarządzanego, które pozostają spójne obecności przepełnienia stosu dowolnego.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="a7fa4-131">Niezarządzane części środowiska CLR pozostają spójne, za pomocą sondy na potrzeby przeniesienia przepełnienie stosu do miejsc dobrze zdefiniowane, a nie przez cofanie się z przepełnienia stosu dowolnego.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="a7fa4-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="a7fa4-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="a7fa4-133">**X DO NOT** jawne zgłaszanie <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="a7fa4-134">Ten wyjątek jest zostanie wygenerowany tylko przez infrastrukturę CLR.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="a7fa4-135">ComException, sehexception — i ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="a7fa4-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="a7fa4-136">**X DO NOT** jawne zgłaszanie <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, i <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="a7fa4-137">Wyjątki te są zostanie wygenerowany tylko przez infrastrukturę CLR.</span><span class="sxs-lookup"><span data-stu-id="a7fa4-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="a7fa4-138">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="a7fa4-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a7fa4-139">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="a7fa4-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7fa4-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7fa4-140">See also</span></span>

- [<span data-ttu-id="a7fa4-141">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="a7fa4-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="a7fa4-142">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="a7fa4-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
