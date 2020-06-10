---
title: Używanie standardowych typów wyjątków
description: Przeczytaj o standardowych typach wyjątków w programie .NET. Dowiedz się więcej na temat SystemException, ApplicationException, ArgumentException, ComException i innych.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: f95529eabd87d9ec7c379b9f790e039e1192ac53
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663060"
---
# <a name="using-standard-exception-types"></a>Używanie standardowych typów wyjątków
W tej sekcji opisano standardowe wyjątki udostępniane przez środowisko oraz szczegóły ich użycia. Lista nie jest kompletna. Zapoznaj się z dokumentacją dotyczącą .NET Framework, aby uzyskać informacje na temat użycia innych typów wyjątków struktury.

## <a name="exception-and-systemexception"></a>Wyjątek i SystemException
 ❌NIE zgłaszaj <xref:System.Exception?displayProperty=nameWithType> ani <xref:System.SystemException?displayProperty=nameWithType> .

 ❌NIE należy przechwytywać `System.Exception` ani `System.SystemException` w kodzie struktury, chyba że zamierzasz ponownie zgłosić.

 ❌UNIKAj przechwytywania `System.Exception` lub `System.SystemException` , z wyjątkiem obsługi wyjątków najwyższego poziomu.

## <a name="applicationexception"></a>ApplicationException
 ❌NIE zgłaszaj ani nie wyprowadzaj z <xref:System.ApplicationException> .

## <a name="invalidoperationexception"></a>InvalidOperationException
 ✔️ zgłosić, <xref:System.InvalidOperationException> czy obiekt jest w niewłaściwym stanie.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>Argumentyexception, ArgumentNullException i wyjątku ArgumentOutOfRangeException
 ✔️ DO rzutowania <xref:System.ArgumentException> lub jednego z jego podtypów, jeśli do elementu członkowskiego są przekazane złe argumenty. Preferuj najbardziej pochodny typ wyjątku, jeśli ma zastosowanie.

 ✔️ ustawia `ParamName` Właściwość podczas zgłaszania jednej z podklas `ArgumentException` .

 Ta właściwość reprezentuje nazwę parametru, który spowodował zgłoszenie wyjątku. Należy pamiętać, że właściwość można ustawić przy użyciu jednego z przeciążeń konstruktora.

 ✔️ użyć `value` jako nazwy niejawnego parametru wartości metod ustawiających właściwości.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException i AccessViolationException
 ❌NIE Zezwalaj na publicznie wywoływane interfejsy API, aby jawnie lub niejawnie zgłosić <xref:System.NullReferenceException> , <xref:System.AccessViolationException> lub <xref:System.IndexOutOfRangeException> . Te wyjątki są zastrzeżone i zgłaszane przez aparat wykonywania, a w większości przypadków wskazują usterkę.

 Wykonaj sprawdzanie argumentów, aby uniknąć zgłaszania tych wyjątków. Zgłaszanie tych wyjątków ujawnia szczegóły implementacji metody, która może ulec zmianie w czasie.

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌NIE zgłaszaj jawnie <xref:System.StackOverflowException> . Wyjątek powinien być jawnie wygenerowany tylko przez środowisko CLR.

 ❌NIE należy przechwytywać `StackOverflowException` .

 Niemal niemożliwe jest zapisanie kodu zarządzanego, który pozostaje spójny w obecności dowolnego przepełnienia stosu. Niezarządzane części środowiska CLR pozostają spójne przy użyciu sond do przenoszenia nadprzepływów stosu do dobrze zdefiniowanych miejsc, a nie do tworzenia kopii zapasowych z dowolnego przepełnienia stosu.

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌NIE zgłaszaj jawnie <xref:System.OutOfMemoryException> . Ten wyjątek jest zgłaszany tylko przez infrastrukturę środowiska CLR.

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, SEHException — i ExecutionEngineException
 ❌NIE należy jawnie zgłaszać <xref:System.Runtime.InteropServices.COMException> , <xref:System.ExecutionEngineException> i <xref:System.Runtime.InteropServices.SEHException> . Te wyjątki są zgłaszane tylko przez infrastrukturę środowiska CLR.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
- [Wyjątki — zalecenia dotyczące projektowania](exceptions.md)
