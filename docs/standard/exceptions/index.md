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
ms.openlocfilehash: 8e78b2a8d7a815637e143eeb88bcfb51ded33771
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75741353"
---
# <a name="handling-and-throwing-exceptions-in-net"></a>Obsługa i zgłaszanie wyjątków w .NET

Aplikacje muszą być w stanie obsługiwać błędy, które występują podczas wykonywania w sposób spójny. .NET udostępnia model powiadamiania aplikacji o błędach w jednolity sposób: operacje .NET wskazują na błąd, zgłaszając wyjątki.

## <a name="exceptions"></a>Wyjątki

Wyjątkiem jest dowolny warunek błędu lub nieoczekiwane zachowanie napotkane przez program wykonujący. Wyjątki mogą być generowane z powodu błędu w kodzie lub w kodzie, który wywołasz (na przykład biblioteki udostępnionej), niedostępnych zasobów systemu operacyjnego, nieoczekiwanych warunków, które napotka czas uruchomieniowy (takich jak kod, który nie może być zweryfikowany) i tak dalej. Aplikacja może odzyskać z niektórych z tych warunków, ale nie od innych. Mimo że można odzyskać z większości wyjątków aplikacji, nie można odzyskać z większości wyjątków czasu wykonywania.

W .NET wyjątek jest obiektem, który <xref:System.Exception?displayProperty=nameWithType> dziedziczy z klasy. Wyjątek jest zgłaszany z obszaru kodu, w którym wystąpił problem. Wyjątek jest przekazywany w górę stosu, dopóki aplikacja obsługuje go lub program kończy.

## <a name="exceptions-vs-traditional-error-handling-methods"></a>Wyjątki a tradycyjne metody obsługi błędów

Tradycyjnie model obsługi błędów języka opierał się na unikatowym sposobie wykrywania błędów i lokalizowaniu dla nich obsługi języka lub na mechanizmie obsługi błędów zapewnianym przez system operacyjny. Sposób, w jaki platforma .NET implementuje obsługę wyjątków, zapewnia następujące zalety:

- Zgłaszanie wyjątków i obsługa działa tak samo dla języków programowania .NET.

- Nie wymaga żadnej składni określonego języka do obsługi wyjątków, ale umożliwia każdemu językowi zdefiniowanie własnej składni.

- Wyjątki mogą być generowane przez proces, a nawet granice maszyny.

- Kod obsługi wyjątków można dodać do aplikacji, aby zwiększyć niezawodność programu.

Wyjątki oferują zalety w stosunku do innych metod powiadamiania o błędach, takich jak kody zwrotne. Błędy nie pozostają niezauważone, ponieważ jeśli wyjątek zostanie zgłoszony i nie obsługujesz go, czas wykonywania kończy działanie aplikacji. Nieprawidłowe wartości nie są nadal propagowane przez system w wyniku kodu, który nie może sprawdzić, czy kod zwrotny nie jest wynikiem błędu.

## <a name="common-exceptions"></a>Typowe wyjątki

W poniższej tabeli wymieniono niektóre typowe wyjątki z przykładami, co może je powodować.

| Typ wyjątku | Opis | Przykład |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | Klasa podstawowa dla wszystkich wyjątków. | Brak (użyj klasy pochodnej tego wyjątku). |
| <xref:System.IndexOutOfRangeException> | Generowane przez czas wykonywania tylko wtedy, gdy tablica jest indeksowana nieprawidłowo. | Indeksowanie tablicy poza jej prawidłowym zakresem: <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | Generowane przez czas wykonywania tylko wtedy, gdy odwołuje się do obiektu null. | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | Generowane przez metody, gdy w stanie nieprawidłowym. | Wywołanie `Enumerator.MoveNext()` po usunięciu elementu z podstawowej kolekcji. |
| <xref:System.ArgumentException> | Klasa podstawowa dla wszystkich wyjątków argumentów. | Brak (użyj klasy pochodnej tego wyjątku). |
| <xref:System.ArgumentNullException> | Generowane przez metody, które nie zezwalają na argument ma wartość null. | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | Generowane przez metody, które sprawdzają, czy argumenty znajdują się w danym zakresie. | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a>Zobacz też

- [Właściwości i klasy wyjątków](exception-class-and-properties.md)
- [Instrukcje: Używanie bloku try/catch do przechwytywania wyjątków](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [Instrukcje: Używanie określonych wyjątków w bloku catch](how-to-use-specific-exceptions-in-a-catch-block.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](how-to-explicitly-throw-exceptions.md)
- [Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika](how-to-create-user-defined-exceptions.md)
- [Używanie obsługi wyjątków filtrowanych przez użytkownika](using-user-filtered-exception-handlers.md)
- [Instrukcje: Używanie bloków finally](how-to-use-finally-blocks.md)
- [Obsługa wyjątków międzyoperacyjności COM](handling-com-interop-exceptions.md)
- [Najlepsze rozwiązania dotyczące wyjątków](best-practices-for-exceptions.md)
- [Co każdy deweloper musi wiedzieć o wyjątkach w czasie wykonywania](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
