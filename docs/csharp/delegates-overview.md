---
title: Wprowadzenie do delegatów
description: Dowiedz się więcej o pełnomocnikach w tym temacie przeglądu, który wprowadza podstawowe pojęcia i omawia cele projektowania języka dla pełnomocników.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: fd594f77c034533a1d5aee1d8279e9b727284311
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146232"
---
# <a name="introduction-to-delegates"></a>Wprowadzenie do delegatów

Delegaci zapewniają mechanizm *późnego wiązania* w .NET. Późne wiązanie oznacza, że można utworzyć algorytm, w którym obiekt wywołujący dostarcza również co najmniej jedną metodę, która implementuje część algorytmu.

Rozważmy na przykład sortowanie listy gwiazd w aplikacji astronomicznej.
Możesz posortować te gwiazdy według ich odległości od ziemi, wielkości gwiazdy lub ich postrzeganej jasności.

We wszystkich tych przypadkach Sort() Metoda zasadniczo to samo: rozmieszcza elementy na liście na podstawie porównania. Kod, który porównuje dwie gwiazdki jest inny dla każdego z kolejności sortowania.

Tego rodzaju rozwiązania są stosowane w oprogramowaniu od pół wieku.
Koncepcja delegata języka Języka C# zapewnia obsługę języka pierwszej klasy i bezpieczeństwo typu wokół koncepcji.

Jak zobaczysz w dalszej części tej serii, kod C# piszesz dla algorytmów, takich jak ten jest typ bezpieczny i wykorzystuje język i kompilator, aby upewnić się, że typy są zgodne dla argumentów i zwracanych typów.

## <a name="language-design-goals-for-delegates"></a>Cele projektowania języka dla delegatów

Projektanci języka wyliczono kilka celów dla funkcji, która ostatecznie stała się delegatów.

Zespół chciał wspólnej konstrukcji języka, który może być używany dla wszelkich algorytmów późnego wiązania. Dzięki temu deweloperzy mogą nauczyć się jednej koncepcji i używać tej samej koncepcji w wielu różnych problemach z oprogramowaniem.

Po drugie, zespół chciał obsługiwać wywołania metodą pojedynczej i multiemisji. (Delegatów multiemisji są delegatów, które łańcuch razem wiele wywołań metody.
Przykłady w [dalszej części tej serii](delegate-class.md).)

Zespół chciał delegatów do obsługi tego samego typu bezpieczeństwa, które deweloperzy oczekują od wszystkich konstrukcji języka C#.

Na koniec zespół rozpoznał, że wzorzec zdarzenia jest jeden wzorzec, w którym delegatów lub wszelkie algorytmy późnego wiązania, jest bardzo przydatne. Zespół chciał upewnić się, że kod dla delegatów może stanowić podstawę wzorca zdarzenia .NET.

Wynikiem całej tej pracy był pełnomocnik i obsługa zdarzeń w językach C# i .NET. Pozostałe artykuły w tej sekcji omówi funkcje języka, obsługę biblioteki i wspólne idiomy, które są używane podczas pracy z delegatami.

Dowiesz się o `delegate` sutece kluczowej i o tym, jaki kod generuje. Dowiesz się o funkcjach `System.Delegate` w klasie i jak te funkcje są używane. Dowiesz się, jak utworzyć typ bezpiecznych delegatów i jak utworzyć metody, które mogą być wywoływane za pośrednictwem delegatów. Dowiesz się również, jak pracować z delegatów i zdarzeń przy użyciu wyrażeń Lambda. Zobaczysz, gdzie delegaci stają się jednym z bloków konstrukcyjnych dla LINQ. Dowiesz się, jak delegaci są podstawą wzorca zdarzenia .NET i jak są one różne.

Ogólnie rzecz biorąc, zobaczysz, jak delegaci są integralną częścią programowania w .NET i pracy z ramowych interfejsów API.

Zacznijmy.

[Dalej](delegate-class.md)
