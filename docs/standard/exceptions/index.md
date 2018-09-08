---
title: Obsługa i zgłaszanie wyjątków na platformie .NET
ms.date: 06/19/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263e6394a57ec3e7ef00eb79671d9b8ac47e724f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177238"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>Obsługa i zgłaszanie wyjątków na platformie .NET

Aplikacje muszą mieć możliwość obsługi błędów występujących podczas wykonywania w spójny sposób. .NET udostępnia model dotyczące powiadamiania aplikacji o błędach w jednolity sposób: operacje .NET wskazać błąd przez zgłaszanie wyjątków.

## <a name="exceptions"></a>Wyjątki

Wyjątek to każdy warunek błędu i nieoczekiwane zachowanie, które zostanie osiągnięty, wykonywania programu. Wyjątki mogą zostać wygenerowane z powodu błędów w kodzie lub kod, który można wywoływać (np. biblioteki udostępnionej), zasobów niedostępny systemu operacyjnego, nieoczekiwane warunki, które środowisko uruchomieniowe napotka (na przykład kod, którego nie można zweryfikować) i tak dalej. Aplikację można odzyskać z niektórych z tych warunków, ale nie od innych użytkowników. Mimo że można odzyskać z większości aplikacji wyjątki, nie można odzyskać z większości wyjątki środowiska uruchomieniowego.

Na platformie .NET, wyjątek jest obiektem, który dziedziczy z <xref:System.Exception?displayProperty=nameWithType> klasy. Wyjątek jest generowany przy użyciu obszaru kodu, w którym wystąpił problem. Wyjątek jest przekazywany w górę stosu, dopóki aplikacja obsługuje ją lub program zakończy.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Wyjątki a tradycyjnych metod obsługi błędów

Tradycyjnie modelu obsługi błędów języka skorzystała w unikatowy sposób wykrywania błędów i lokalizowania programy obsługi dla nich zarówno w języku lub na mechanizmu obsługi błędów, dostarczone przez system operacyjny. Sposób .NET implementuje obsługę wyjątków zapewnia następujące korzyści:

- Wyjątek zostanie zgłoszony i obsługa działa tak samo, dla języków programowania .NET.

- Nie wymaga żadnych składni konkretnego języka dla obsługi wyjątków, ale pozwala zdefiniować własną składnię dla każdego języka.

- Wyjątki mogą zostać wygenerowane w procesie i nawet granic.

- Kod obsługi wyjątków, można dodać do aplikacji w celu zwiększenia niezawodności programu.

Wyjątki oferują przewagę nad innymi metodami powiadomienia o błędzie, takich jak kody powrotne. Błędy nie niezauważone, ponieważ jeśli wyjątek jest generowany i nie można go obsłużyć, środowisko uruchomieniowe kończy działanie aplikacji. Nieprawidłowe wartości nie w dalszym ciągu propagować przez system w wyniku kod, który zakończy się niepowodzeniem, aby sprawdzić, czy zwracany kod błędu.

## <a name="common-exceptions"></a>Typowe wyjątki

W poniższej tabeli wymieniono niektóre typowe wyjątki z przykładami co mogą być ich przyczyną.

| Typ wyjątku | Opis | Przykład |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Klasa bazowa dla wszystkich wyjątków. | Brak (Użyj klasy pochodnej tego wyjątku). |
| <xref:System.IndexOutOfRangeException> | Element zgłaszany przez środowisko uruchomieniowe, tylko wtedy, gdy tablica jest indeksowana nieprawidłowo. | Indeksowanie tablicy poza prawidłowym zakresem: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Element zgłaszany przez środowisko uruchomieniowe, tylko wtedy, gdy odwołuje się do obiektu o wartości null. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Zgłoszony przez metody, gdy jest w nieprawidłowym stanie. | Wywoływanie `Enumerator.MoveNext()` po usunięciu elementu z kolekcji źródłowej. |
| <xref:System.ArgumentException> | Klasa bazowa dla wszystkich wyjątków argumentów. | Brak (Użyj klasy pochodnej tego wyjątku). |
| <xref:System.ArgumentNullException> | Zgłoszony przez metody, które nie zezwalają na argument mieć wartości null. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Zgłoszony przez metody, które Sprawdź, czy argumenty są w danym zakresie. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Zobacz także

- [Właściwości i klasy wyjątków](exception-class-and-properties.md)  
- [Instrukcje: Używanie bloku try/catch do przechwytywania wyjątków](how-to-use-the-try-catch-block-to-catch-exceptions.md)  
- [Instrukcje: Używanie określonych wyjątków w bloku catch](how-to-use-specific-exceptions-in-a-catch-block.md)  
- [Instrukcje: Jawne zgłaszanie wyjątków](how-to-explicitly-throw-exceptions.md)  
- [Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika](how-to-create-user-defined-exceptions.md)  
- [Używanie obsługi wyjątków filtrowanych przez użytkownika](using-user-filtered-exception-handlers.md)  
- [Instrukcje: Używanie bloków finally](how-to-use-finally-blocks.md)  
- [Obsługa wyjątków międzyoperacyjności COM](handling-com-interop-exceptions.md)  
- [Najlepsze rozwiązania dotyczące wyjątków](best-practices-for-exceptions.md)  
- [Co Dev co trzeba wiedzieć o wyjątków w środowisku uruchomieniowym](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).
