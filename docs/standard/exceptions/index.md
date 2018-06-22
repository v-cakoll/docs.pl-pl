---
title: Obsługa i zgłaszanie wyjątków w .NET
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
ms.openlocfilehash: a278940528966e32646a3551b4c133223de9746e
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298347"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>Obsługa i zgłaszanie wyjątków w .NET

Aplikacji musi mieć możliwość obsługi błędów występujących podczas wykonywania w sposób ciągły. .NET udostępnia model dotyczące powiadamiania aplikacji błędy ujednolicone: operacje .NET wskazania błędu przez zgłaszanie wyjątków.

## <a name="exceptions"></a>Wyjątki

Wyjątkiem jest żadnego warunku błędu nieoczekiwanego zachowania, które napotkano przez wykonywania programu. Wyjątki może zostać wygenerowany z powodu błędów w kodzie lub kod, który wywołania (na przykład biblioteki udostępnionej), zasobów niedostępny systemu operacyjnego, nieoczekiwane warunki, które napotyka środowiska uruchomieniowego (na przykład kod, którego nie można zweryfikować) i tak dalej. Aplikację można odzyskać z niektórych z tych warunków, ale nie od innych użytkowników. Mimo że można odzyskać z większości wyjątków aplikacji, nie można odzyskać z większości wyjątków w czasie wykonywania.

W środowisku .NET, wyjątek jest obiekt, który dziedziczy <xref:System.Exception?displayProperty=nameWithType> klasy. Wyjątek z obszaru kodu, w którym wystąpił problem. Wyjątek jest przekazywany w górę stosu, dopóki aplikacja obsługuje ją lub program zakończy.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Wyjątki, a tradycyjnych metod obsługi błędów

Tradycyjnie model Obsługa błędów języka stosowane w sposób unikatowy zarówno w języku wykrywanie błędów i lokalizowanie programy obsługi dla nich lub mechanizm obsługi błędów dostarczane przez system operacyjny. Sposób obsługi wyjątków implementuje platformy .NET ma następujące zalety:

- Wyjątek zgłaszanie i obsługa działa tak samo dla języków programowania .NET.

- Nie wymaga żadnych składni konkretnego języka do obsługi wyjątków, ale umożliwia każdego języka zdefiniować własny składni.

- Wyjątki może zostać wygenerowany przez proces, a nawet granic.

- Kod obsługi wyjątków można dodać do aplikacji w celu zwiększenia niezawodności programu.

Wyjątki oferują zalet w porównaniu z innych metod powiadomienie o błędzie, takich jak kody powrotu. Błędy nie niezauważone, ponieważ jest zgłaszany wyjątek, nie Obsługuj go środowiska uruchomieniowego kończy aplikacji. Nieprawidłowe wartości nie dalej propagowany za pośrednictwem systemu wyniku kodu, który zakończy się niepowodzeniem, aby wyszukać zwracając kod błędu.

## <a name="common-exceptions"></a>Typowe wyjątków

W poniższej tabeli przedstawiono niektóre typowe wyjątki z przykładami, co może spowodować ich.

| Typ wyjątku | Opis | Przykład |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Klasa podstawowa dla wszystkich wyjątków. | Brak (Użyj klasy pochodnej tego wyjątku). |
| <xref:System.IndexOutOfRangeException> | Wyjątek w czasie wykonywania tylko wtedy, gdy tablica jest indeksowana nieprawidłowo. | Indeksowanie tablicy poza prawidłowym zakresem: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Wyjątek w czasie wykonywania tylko wtedy, gdy odwołuje się obiekt zerowy. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Element zgłaszany, za pomocą metod w nieprawidłowym stanie. | Wywoływanie `Enumerator.MoveNext()` po usunięciu elementu z kolekcji źródłowej. |
| <xref:System.ArgumentException> | Klasa podstawowa dla wszystkich wyjątków argumentów. | Brak (Użyj klasy pochodnej tego wyjątku). |
| <xref:System.ArgumentNullException> | Element zgłaszany, za pomocą metod, które nie zezwalają na argument mieć wartości null. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Element zgłaszany, za pomocą metod, które pozwalają sprawdzić, czy argumenty w danym zakresie. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Zobacz także

[Właściwości i klasy wyjątków](exception-class-and-properties.md)  
[Instrukcje: Używanie bloku try/catch do przechwytywania wyjątków](how-to-use-the-try-catch-block-to-catch-exceptions.md)  
[Instrukcje: Używanie określonych wyjątków w bloku catch](how-to-use-specific-exceptions-in-a-catch-block.md)  
[Instrukcje: Jawne zgłaszanie wyjątków](how-to-explicitly-throw-exceptions.md)  
[Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika](how-to-create-user-defined-exceptions.md)  
[Używanie obsługi wyjątków filtrowanych przez użytkownika](using-user-filtered-exception-handlers.md)  
[Instrukcje: Używanie bloków finally](how-to-use-finally-blocks.md)  
[Obsługa wyjątków międzyoperacyjności COM](handling-com-interop-exceptions.md)  
[Najlepsze rozwiązania dotyczące wyjątków](best-practices-for-exceptions.md)  
[Dev co należy wiedzieć o wyjątków w czasie wykonywania](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).
