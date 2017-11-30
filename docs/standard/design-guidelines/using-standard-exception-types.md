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
# <a name="using-standard-exception-types"></a>Używanie typów wyjątków standardowe
W tej sekcji opisano wyjątki standardowe dostarczane przez platformę i szczegóły ich użycia. Lista w żadnym wypadku nie jest kompletną. Skontaktuj się z dokumentacją odwołanie .NET Framework użycia innych typów wyjątków Framework.  
  
## <a name="exception-and-systemexception"></a>Wyjątek i SystemException  
 **X nie** throw <xref:System.Exception?displayProperty=nameWithType> lub <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X nie** catch `System.Exception` lub `System.SystemException` w ramach kodu, chyba że planujesz do ponownego zgłoszenia.  
  
 **X należy UNIKAĆ** Przechwytywanie `System.Exception` lub `System.SystemException`, z wyjątkiem programów obsługi wyjątków najwyższego poziomu.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X nie** zgłosić lub pochodzić od <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **CZY ✓** throw <xref:System.InvalidOperationException> Jeśli obiekt jest w nieodpowiednim stanie.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException argumentnullexception — i ArgumentOutOfRangeException  
 **CZY ✓** throw <xref:System.ArgumentException> lub jednego z jego podtypach jeśli złe argumenty są przekazywane do elementu członkowskiego. Preferowane najdalszych pochodnych typ wyjątku, jeśli ma to zastosowanie.  
  
 **CZY ✓** ustawić `ParamName` właściwości, gdy jeden podklasy zgłaszanie `ArgumentException`.  
  
 Ta właściwość reprezentuje nazwę parametru, który spowodował wyjątek zostanie wygenerowany. Należy pamiętać, że właściwość można ustawić przy użyciu jednego z przeciążeń konstruktora.  
  
 **CZY ✓** użyj `value` dla nazwy parametru niejawne wartości metody ustawiające właściwości.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException i accessviolationexception —  
 **X nie** Zezwalaj publicznie można wywołać interfejsów API, aby jawnie lub niejawnie throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, lub <xref:System.IndexOutOfRangeException>. Wyjątki te są zarezerwowane i zgłaszanych przez aparat wykonywania i w większości przypadków wskazuje błąd.  
  
 Wykonaj sprawdzanie, aby uniknąć generowania wyjątków tych argumentów. Wyrzucanie wyjątków te przedstawia szczegóły implementacji metody, która może ulec zmianie.  
  
## <a name="stackoverflowexception"></a>Stackoverflowexception —  
 **X nie** jawne zgłaszanie <xref:System.StackOverflowException>. Wyjątek powinien jawnie zgłoszony tylko przez środowisko CLR.  
  
 **X nie** catch `StackOverflowException`.  
  
 Jest praktycznie niemożliwe napisać kod zarządzany, które pozostają spójne obecności przepełnienia stosu dowolnego. Niezarządzane części środowiska CLR zachować spójność za pomocą sond przenoszenia przepełnienie stosu dobrze zdefiniowany miejsca, a nie przez wycofaniu z przepełnienia stosu dowolnego.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X nie** jawne zgłaszanie <xref:System.OutOfMemoryException>. Ten wyjątek ma być zgłoszony tylko przez infrastrukturę CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, sehexception — i ExecutionEngineException  
 **X nie** jawne zgłaszanie <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, i <xref:System.Runtime.InteropServices.SEHException>. Te wyjątki powinny być zgłoszony tylko przez infrastrukturę CLR.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówek dotyczących wyjątków](../../../docs/standard/design-guidelines/exceptions.md)
