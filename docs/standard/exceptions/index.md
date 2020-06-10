---
title: Obsługa i zgłaszanie wyjątków w programie .NET
description: Dowiedz się, jak obsługiwać i generować wyjątki w programie .NET. Wyjątki to sposób, w jaki operacje .NET wskazują niepowodzenie aplikacji.
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
ms.openlocfilehash: 89d88e3128917125d1a09466ed4e230604d6978c
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662774"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>Obsługa i zgłaszanie wyjątków w programie .NET

Aplikacje muszą być w stanie obsługiwać błędy występujące podczas wykonywania w spójny sposób. Platforma .NET udostępnia model do powiadamiania aplikacji o błędach w jednolity sposób: operacje platformy .NET wskazują na awarię przez wyrzucanie wyjątków.

## <a name="exceptions"></a>Wyjątki

Wyjątek jest dowolnym warunkiem błędu lub nieoczekiwanym zachowaniem napotkanym przez program wykonujący. Wyjątki mogą być zgłaszane z powodu błędu w kodzie lub kodu, który jest wywoływany (na przykład biblioteki udostępnionej), niedostępnych zasobów systemu operacyjnego, nieoczekiwanych warunków napotkanych przez środowisko uruchomieniowe (takich jak kod, którego nie można zweryfikować) itd. Aplikacja może wykonać odzyskiwanie z niektórych z tych warunków, ale nie od innych. Chociaż można wykonać odzyskiwanie z większości wyjątków aplikacji, nie można odzyskać sprawności z większości wyjątków czasu wykonywania.

W programie .NET wyjątek jest obiektem, który dziedziczy z <xref:System.Exception?displayProperty=nameWithType> klasy. Wyjątek jest generowany z obszaru kodu, w którym wystąpił problem. Wyjątek jest przenoszona do momentu, aż aplikacja obsłuży go lub zakończy działanie programu.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Wyjątki a tradycyjne metody obsługi błędów

Tradycyjnie model obsługi błędów języka opiera się na unikatowym sposobie wykrywania błędów i lokalizowania programów obsługi albo w mechanizmie obsługi błędów dostarczonym przez system operacyjny. Sposób, w jaki program .NET implementuje obsługę wyjątków, zapewnia następujące korzyści:

- Przerzucanie i obsługa wyjątków działa tak samo dla języków programowania .NET.

- Nie wymaga żadnej określonej składni języka do obsługi wyjątków, ale umożliwia każdemu językowi zdefiniowanie własnej składni.

- Wyjątki mogą być zgłaszane między procesami, a nawet granicami maszyn.

- Kod obsługi wyjątków można dodać do aplikacji w celu zwiększenia niezawodności programu.

Wyjątki oferują zalety w porównaniu z innymi metodami powiadamiania o błędach, takich jak kody powrotne. Niepowodzenia nie są wyrzucane, ponieważ jeśli wystąpi wyjątek, a jego nie obsłużysz, środowisko uruchomieniowe zakończy działanie aplikacji. Nieprawidłowe wartości nie są nadal propagowane przez system w wyniku kodu, który nie może sprawdzić kodu powrotu błędu.

## <a name="common-exceptions"></a>Typowe wyjątki

W poniższej tabeli wymieniono niektóre typowe wyjątki z przykładami, które mogą je spowodować.

| Typ wyjątku | Opis | Przykład |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Klasa bazowa dla wszystkich wyjątków. | Brak (Użyj klasy pochodnej tego wyjątku). |
| <xref:System.IndexOutOfRangeException> | Zgłoszone przez środowisko uruchomieniowe tylko wtedy, gdy tablica jest indeksowana nieprawidłowo. | Indeksowanie tablicy poza prawidłowym zakresem: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Zgłoszone przez środowisko uruchomieniowe tylko wtedy, gdy istnieje odwołanie do obiektu o wartości null. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Zgłoszone przez metody w nieprawidłowym stanie. | Wywoływanie `Enumerator.MoveNext()` po usunięciu elementu z kolekcji źródłowej. |
| <xref:System.ArgumentException> | Klasa bazowa dla wszystkich wyjątków argumentów. | Brak (Użyj klasy pochodnej tego wyjątku). |
| <xref:System.ArgumentNullException> | Zgłoszone przez metody, które nie zezwalają argumentu na wartość null. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Zgłoszone przez metody, które weryfikują, że argumenty znajdują się w danym zakresie. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Zobacz także

- [Klasa wyjątku i właściwości](exception-class-and-properties.md)
- [Instrukcje: Używanie bloku try/catch do przechwytywania wyjątków](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [Instrukcje: Używanie określonych wyjątków w bloku catch](how-to-use-specific-exceptions-in-a-catch-block.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](how-to-explicitly-throw-exceptions.md)
- [Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika](how-to-create-user-defined-exceptions.md)
- [Używanie obsługi wyjątków filtrowanych przez użytkownika](using-user-filtered-exception-handlers.md)
- [Instrukcje: Używanie bloków finally](how-to-use-finally-blocks.md)
- [Obsługa wyjątków międzyoperacyjności COM](handling-com-interop-exceptions.md)
- [Najlepsze rozwiązania dotyczące wyjątków](best-practices-for-exceptions.md)
- [Co każdy Deweloper musi wiedzieć o wyjątkach w środowisku uruchomieniowym](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
