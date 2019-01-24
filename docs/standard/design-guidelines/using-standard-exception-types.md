---
title: Używanie standardowych typów wyjątków
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: KrzysztofCwalina
ms.openlocfilehash: b947c7cce057c060b1ab5054d1227f5703ccbf89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543909"
---
# <a name="using-standard-exception-types"></a>Używanie standardowych typów wyjątków
W tej sekcji opisano standardowych wyjątków, które są dostarczane przez platformę i szczegółowe informacje o ich użycia. Lista w żadnym wypadku nie jest wyczerpująca. Można znaleźć dokumentację referencyjną .NET Framework użycie innych typów wyjątków Framework.  
  
## <a name="exception-and-systemexception"></a>Wyjątek i SystemException  
 **X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> lub <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` lub `System.SystemException` w ramach kodu, chyba że planujesz do ponownego zgłoszenia.  
  
 **X AVOID** Przechwytywanie `System.Exception` lub `System.SystemException`, z wyjątkiem programów obsługi wyjątków najwyższego poziomu.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** zgłosić lub pochodzić od <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** throw <xref:System.InvalidOperationException> Jeśli obiekt jest w nieodpowiednim stanie.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException ArgumentNullException i Trwa wyjątku ArgumentOutOfRangeException  
 **✓ DO** throw <xref:System.ArgumentException> lub jednego z jego podtypach jeśli złe argumenty są przekazywane do elementu członkowskiego. Preferuj najbardziej pochodny typ wyjątku, jeśli ma to zastosowanie.  
  
 **✓ DO** ustawić `ParamName` właściwości, gdy jeden podklasy zgłaszanie `ArgumentException`.  
  
 Ta właściwość reprezentuje nazwę parametru, który spowodował zgłoszenie wyjątku. Należy pamiętać, że właściwość można ustawić przy użyciu jednego z przeciążeń konstruktora.  
  
 **✓ DO** użyj `value` dla nazwy parametru niejawne wartości metody ustawiające właściwości.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>Obiektu NullReferenceException IndexOutOfRangeException i AccessViolationException  
 **X DO NOT** Zezwalaj publicznie można wywołać interfejsów API, aby jawnie lub niejawnie throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, lub <xref:System.IndexOutOfRangeException>. Wyjątki te są zarezerwowane i generowane przez aparat wykonywania i w większości przypadków wskazania błędu.  
  
 Wykonaj sprawdzanie, aby uniknąć generowania wyjątków tych argumentów. Zgłaszanie tych wyjątków przedstawia szczegóły implementacji metody, która może spowodować zmianę wraz z upływem czasu.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** jawne zgłaszanie <xref:System.StackOverflowException>. Powinny być jawnie wyjątku tylko przez środowisko CLR.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 Jest prawie niemożliwe do pisania kodu zarządzanego, które pozostają spójne obecności przepełnienia stosu dowolnego. Niezarządzane części środowiska CLR pozostają spójne, za pomocą sondy na potrzeby przeniesienia przepełnienie stosu do miejsc dobrze zdefiniowane, a nie przez cofanie się z przepełnienia stosu dowolnego.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** jawne zgłaszanie <xref:System.OutOfMemoryException>. Ten wyjątek jest zostanie wygenerowany tylko przez infrastrukturę CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, sehexception — i ExecutionEngineException  
 **X DO NOT** jawne zgłaszanie <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, i <xref:System.Runtime.InteropServices.SEHException>. Wyjątki te są zostanie wygenerowany tylko przez infrastrukturę CLR.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)
