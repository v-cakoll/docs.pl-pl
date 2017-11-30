---
title: "Używanie typów wyjątków standardowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 91cd9a03ad1acf61681ecfad0edb061802c4362c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="add1c-102">Używanie typów wyjątków standardowe</span><span class="sxs-lookup"><span data-stu-id="add1c-102">Using Standard Exception Types</span></span>
<span data-ttu-id="add1c-103">W tej sekcji opisano wyjątki standardowe dostarczane przez platformę i szczegóły ich użycia.</span><span class="sxs-lookup"><span data-stu-id="add1c-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="add1c-104">Lista w żadnym wypadku nie jest kompletną.</span><span class="sxs-lookup"><span data-stu-id="add1c-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="add1c-105">Skontaktuj się z dokumentacją odwołanie .NET Framework użycia innych typów wyjątków Framework.</span><span class="sxs-lookup"><span data-stu-id="add1c-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="add1c-106">Wyjątek i SystemException</span><span class="sxs-lookup"><span data-stu-id="add1c-106">Exception and SystemException</span></span>  
 <span data-ttu-id="add1c-107">**X nie** throw <xref:System.Exception?displayProperty=nameWithType> lub <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="add1c-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="add1c-108">**X nie** catch `System.Exception` lub `System.SystemException` w ramach kodu, chyba że planujesz do ponownego zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="add1c-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="add1c-109">**X należy UNIKAĆ** Przechwytywanie `System.Exception` lub `System.SystemException`, z wyjątkiem programów obsługi wyjątków najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="add1c-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="add1c-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="add1c-110">ApplicationException</span></span>  
 <span data-ttu-id="add1c-111">**X nie** zgłosić lub pochodzić od <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="add1c-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="add1c-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="add1c-112">InvalidOperationException</span></span>  
 <span data-ttu-id="add1c-113">**CZY ✓** throw <xref:System.InvalidOperationException> Jeśli obiekt jest w nieodpowiednim stanie.</span><span class="sxs-lookup"><span data-stu-id="add1c-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="add1c-114">ArgumentException argumentnullexception — i ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="add1c-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="add1c-115">**CZY ✓** throw <xref:System.ArgumentException> lub jednego z jego podtypach jeśli złe argumenty są przekazywane do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="add1c-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="add1c-116">Preferowane najdalszych pochodnych typ wyjątku, jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="add1c-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="add1c-117">**CZY ✓** ustawić `ParamName` właściwości, gdy jeden podklasy zgłaszanie `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="add1c-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="add1c-118">Ta właściwość reprezentuje nazwę parametru, który spowodował wyjątek zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="add1c-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="add1c-119">Należy pamiętać, że właściwość można ustawić przy użyciu jednego z przeciążeń konstruktora.</span><span class="sxs-lookup"><span data-stu-id="add1c-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="add1c-120">**CZY ✓** użyj `value` dla nazwy parametru niejawne wartości metody ustawiające właściwości.</span><span class="sxs-lookup"><span data-stu-id="add1c-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="add1c-121">NullReferenceException, IndexOutOfRangeException i accessviolationexception —</span><span class="sxs-lookup"><span data-stu-id="add1c-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="add1c-122">**X nie** Zezwalaj publicznie można wywołać interfejsów API, aby jawnie lub niejawnie throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, lub <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="add1c-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="add1c-123">Wyjątki te są zarezerwowane i zgłaszanych przez aparat wykonywania i w większości przypadków wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="add1c-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="add1c-124">Wykonaj sprawdzanie, aby uniknąć generowania wyjątków tych argumentów.</span><span class="sxs-lookup"><span data-stu-id="add1c-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="add1c-125">Wyrzucanie wyjątków te przedstawia szczegóły implementacji metody, która może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="add1c-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="add1c-126">Stackoverflowexception —</span><span class="sxs-lookup"><span data-stu-id="add1c-126">StackOverflowException</span></span>  
 <span data-ttu-id="add1c-127">**X nie** jawne zgłaszanie <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="add1c-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="add1c-128">Wyjątek powinien jawnie zgłoszony tylko przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="add1c-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="add1c-129">**X nie** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="add1c-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="add1c-130">Jest praktycznie niemożliwe napisać kod zarządzany, które pozostają spójne obecności przepełnienia stosu dowolnego.</span><span class="sxs-lookup"><span data-stu-id="add1c-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="add1c-131">Niezarządzane części środowiska CLR zachować spójność za pomocą sond przenoszenia przepełnienie stosu dobrze zdefiniowany miejsca, a nie przez wycofaniu z przepełnienia stosu dowolnego.</span><span class="sxs-lookup"><span data-stu-id="add1c-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="add1c-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="add1c-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="add1c-133">**X nie** jawne zgłaszanie <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="add1c-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="add1c-134">Ten wyjątek ma być zgłoszony tylko przez infrastrukturę CLR.</span><span class="sxs-lookup"><span data-stu-id="add1c-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="add1c-135">ComException, sehexception — i ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="add1c-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="add1c-136">**X nie** jawne zgłaszanie <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, i <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="add1c-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="add1c-137">Te wyjątki powinny być zgłoszony tylko przez infrastrukturę CLR.</span><span class="sxs-lookup"><span data-stu-id="add1c-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="add1c-138">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="add1c-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="add1c-139">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="add1c-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add1c-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="add1c-140">See Also</span></span>  
 [<span data-ttu-id="add1c-141">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="add1c-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="add1c-142">Wskazówek dotyczących wyjątków</span><span class="sxs-lookup"><span data-stu-id="add1c-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
