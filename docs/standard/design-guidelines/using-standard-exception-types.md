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
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743543"
---
# <a name="using-standard-exception-types"></a>Używanie standardowych typów wyjątków
W tej sekcji opisano standardowe wyjątki udostępniane przez środowisko oraz szczegóły ich użycia. Lista nie jest kompletna. Zapoznaj się z dokumentacją dotyczącą .NET Framework, aby uzyskać informacje na temat użycia innych typów wyjątków struktury.

## <a name="exception-and-systemexception"></a>Wyjątek i SystemException
 ❌ nie Generuj <xref:System.Exception?displayProperty=nameWithType> lub <xref:System.SystemException?displayProperty=nameWithType>.

 ❌ nie przechwycić `System.Exception` lub `System.SystemException` w kodzie struktury, chyba że zamierzasz ponownie zgłosić.

 ❌ unikać przechwytywania `System.Exception` lub `System.SystemException`, z wyjątkiem obsługi wyjątków najwyższego poziomu.

## <a name="applicationexception"></a>ApplicationException
 ❌ nie zgłaszaj ani nie pochodzą z <xref:System.ApplicationException>.

## <a name="invalidoperationexception"></a>InvalidOperationException
 ✔️ zgłosić <xref:System.InvalidOperationException>, jeśli obiekt jest w niewłaściwym stanie.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>Argumentyexception, ArgumentNullException i wyjątku ArgumentOutOfRangeException
 ✔️ zgłosić <xref:System.ArgumentException> lub jeden z jego podtypów, jeśli do elementu członkowskiego są przekazane złe argumenty. Preferuj najbardziej pochodny typ wyjątku, jeśli ma zastosowanie.

 ✔️ ustawia właściwość `ParamName` podczas zgłaszania jednej z podklas `ArgumentException`.

 Ta właściwość reprezentuje nazwę parametru, który spowodował zgłoszenie wyjątku. Należy pamiętać, że właściwość można ustawić przy użyciu jednego z przeciążeń konstruktora.

 ✔️ używać `value` jako nazwy niejawnego parametru wartości metod ustawiających właściwości.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException i AccessViolationException
 ❌ nie umożliwiają publicznie wywoływanych interfejsów API jawnie lub niejawnie zgłosić <xref:System.NullReferenceException>, <xref:System.AccessViolationException>lub <xref:System.IndexOutOfRangeException>. Te wyjątki są zastrzeżone i zgłaszane przez aparat wykonywania, a w większości przypadków wskazują usterkę.

 Wykonaj sprawdzanie argumentów, aby uniknąć zgłaszania tych wyjątków. Zgłaszanie tych wyjątków ujawnia szczegóły implementacji metody, która może ulec zmianie w czasie.

## <a name="stackoverflowexception"></a>StackOverflowException
 NIE należy jawnie zgłosić <xref:System.StackOverflowException>❌. Wyjątek powinien być jawnie wygenerowany tylko przez środowisko CLR.

 NIE przechwytuje `StackOverflowException`❌.

 Niemal niemożliwe jest zapisanie kodu zarządzanego, który pozostaje spójny w obecności dowolnego przepełnienia stosu. Niezarządzane części środowiska CLR pozostają spójne przy użyciu sond do przenoszenia nadprzepływów stosu do dobrze zdefiniowanych miejsc, a nie do tworzenia kopii zapasowych z dowolnego przepełnienia stosu.

## <a name="outofmemoryexception"></a>OutOfMemoryException
 NIE należy jawnie zgłosić <xref:System.OutOfMemoryException>❌. Ten wyjątek jest zgłaszany tylko przez infrastrukturę środowiska CLR.

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, SEHException — i ExecutionEngineException
 ❌ nie zgłaszaj jawnie <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>i <xref:System.Runtime.InteropServices.SEHException>. Te wyjątki są zgłaszane tylko przez infrastrukturę środowiska CLR.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)
