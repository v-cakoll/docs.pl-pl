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
ms.openlocfilehash: 6b202d618d9d2216c8998181303250081de6781c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708987"
---
# <a name="using-standard-exception-types"></a>Używanie standardowych typów wyjątków
W tej sekcji opisano standardowe wyjątki udostępniane przez środowisko oraz szczegóły ich użycia. Lista nie jest kompletna. Zapoznaj się z dokumentacją dotyczącą .NET Framework, aby uzyskać informacje na temat użycia innych typów wyjątków struktury.  
  
## <a name="exception-and-systemexception"></a>Wyjątek i SystemException  
 **X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> lub <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` lub `System.SystemException` w ramach kodu, chyba że planujesz do ponownego zgłoszenia.  
  
 **X AVOID** Przechwytywanie `System.Exception` lub `System.SystemException`, z wyjątkiem programów obsługi wyjątków najwyższego poziomu.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** zgłosić lub pochodzić od <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** throw <xref:System.InvalidOperationException> Jeśli obiekt jest w nieodpowiednim stanie.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>Argumentyexception, ArgumentNullException i wyjątku ArgumentOutOfRangeException  
 **✓ DO** throw <xref:System.ArgumentException> lub jednego z jego podtypach jeśli złe argumenty są przekazywane do elementu członkowskiego. Preferuj najbardziej pochodny typ wyjątku, jeśli ma zastosowanie.  
  
 **✓ DO** ustawić `ParamName` właściwości, gdy jeden podklasy zgłaszanie `ArgumentException`.  
  
 Ta właściwość reprezentuje nazwę parametru, który spowodował zgłoszenie wyjątku. Należy pamiętać, że właściwość można ustawić przy użyciu jednego z przeciążeń konstruktora.  
  
 **✓ DO** użyj `value` dla nazwy parametru niejawne wartości metody ustawiające właściwości.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException i AccessViolationException  
 **X DO NOT** Zezwalaj publicznie można wywołać interfejsów API, aby jawnie lub niejawnie throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, lub <xref:System.IndexOutOfRangeException>. Te wyjątki są zastrzeżone i zgłaszane przez aparat wykonywania, a w większości przypadków wskazują usterkę.  
  
 Wykonaj sprawdzanie argumentów, aby uniknąć zgłaszania tych wyjątków. Zgłaszanie tych wyjątków ujawnia szczegóły implementacji metody, która może ulec zmianie w czasie.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** jawne zgłaszanie <xref:System.StackOverflowException>. Wyjątek powinien być jawnie wygenerowany tylko przez środowisko CLR.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 Niemal niemożliwe jest zapisanie kodu zarządzanego, który pozostaje spójny w obecności dowolnego przepełnienia stosu. Niezarządzane części środowiska CLR pozostają spójne przy użyciu sond do przenoszenia nadprzepływów stosu do dobrze zdefiniowanych miejsc, a nie do tworzenia kopii zapasowych z dowolnego przepełnienia stosu.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** jawne zgłaszanie <xref:System.OutOfMemoryException>. Ten wyjątek jest zgłaszany tylko przez infrastrukturę środowiska CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, SEHException — i ExecutionEngineException  
 **X DO NOT** jawne zgłaszanie <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, i <xref:System.Runtime.InteropServices.SEHException>. Te wyjątki są zgłaszane tylko przez infrastrukturę środowiska CLR.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)
