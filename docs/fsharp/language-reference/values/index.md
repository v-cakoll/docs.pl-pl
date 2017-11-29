---
title: "Wartości (F#)"
description: "Dowiedz się, jak wartości w języku F # to ilości, które mają określonego typu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5e1e73c3-5adb-4bba-9976-d57f1ff6cd8d
ms.openlocfilehash: a1e077552ba39a483be3129c89af48b547219733
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="values"></a>Wartości

Wartości w języku F # to ilości, które mają określony typ; wartości mogą być liczbami całkowitą lub zmiennoprzecinkową, znaków lub tekstu, list, sekwencji, tablic, krotek, rozłączne, rekordy, typu klasy lub wartości funkcji.


## <a name="binding-a-value"></a>Powiązania wartości
Termin *powiązania* oznacza skojarzenie nazwy z definicji. `let` — Słowo kluczowe wiąże wartość, na przykład:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Typ wartości jest wywnioskowany na podstawie definicji. Dla typu pierwotnego, takie jak liczbą całkowitą lub zmiennoprzecinkową typ zależy od typu literału. W związku z tym w poprzednim przykładzie, kompilator wnioskuje typ `b` jako `unsigned int`, podczas gdy kompilator wnioskuje typ `a` jako `int`. Typ wartości funkcji zależy od wartości zwracanej w treści funkcji. Aby uzyskać więcej informacji o typach wartości funkcji, zobacz [funkcji](../functions/index.md). Aby uzyskać więcej informacji na temat typów literału, zobacz [literały](../literals.md).


## <a name="why-immutable"></a>Dlaczego niezmienne?
Niezmienne wartości są wartości, których nie można zmieniać w trakcie wykonywania programu. Jeśli używasz dla języków C++, Visual Basic lub C#, może znaleźć zaskakująco, że F # umieszcza nadrzędności za pośrednictwem modyfikować wartości, a nie zmienne, które można przypisać nowe wartości podczas wykonywania programu. Niezmienne danych jest ważnym elementem programowanie funkcjonalne. W środowisku wielowątkowym udostępnionego zmienne modyfikowalne, które może zostać zmieniona przez wiele różnych wątkach są trudne do zarządzania. Ponadto z zmienne modyfikowalne czasami można stwierdzić, jeśli zmienna może ulec zmianie, gdy jest przekazywana do innej funkcji.

W czystym języków funkcjonalności istnieją żadnych zmiennych i funkcje działają wyłącznie jako funkcje matematyczne. W przypadku, gdy kodu w języku procedurach używa przypisanie zmiennej, aby zmienić wartość, odpowiednik kodu w języku funkcjonalności ma niezmienne wartość danych wejściowych, funkcja niezmienne i różne wartości niezmienne jako dane wyjściowe. Ta matematyczne poziom ścisłości umożliwia większego wnioskowania o zachowaniu program. Zwiększenie poziomu uzasadnienie jest temu kompilatory dokładniej Sprawdź kod i zoptymalizować efektywniej i podnosi poziom stało się łatwiejsze do zrozumienia i zapisać prawidłowego kodu. Funkcjonalny kod jest w związku z tym mogą być łatwiejsze do debugowania niż zwykłe kod procedurach.

F # nie jest czysty język funkcjonalności jeszcze w pełni obsługuje programowanie funkcjonalne. Przy użyciu wartości niezmienne jest dobrym rozwiązaniem, ponieważ w ten sposób swój kod, aby korzystać z ważnym aspektem programowanie funkcjonalne.


## <a name="mutable-variables"></a>Zmienne modyfikowalne
Można użyć słowa kluczowego `mutable` określić zmienną, które można zmienić. Zmienne modyfikowalne w języku F # ma zazwyczaj ograniczonym zakresie, albo jako pola typu wartości lokalnej. Zmienne modyfikowalne o ograniczonym zakresie są łatwiejsze do formantu i mniej mogą być modyfikowane w nieprawidłowy sposób.

Wartość początkowa można przypisać do modyfikowalnej zmiennej, za pomocą `let` — słowo kluczowe w taki sam sposób, jak należy zdefiniować wartość. Jednak różnica jest, że można następnie przypisać nowe wartości zmienne modyfikowalne przy użyciu `<-` operatora, jak w poniższym przykładzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]
    
## <a name="related-topics"></a>Tematy pokrewne


|Tytuł|Opis|
|-----|-----------|
|[Let — powiązania](../functions/let-bindings.md)|Zawiera informacje dotyczące używania `let` — słowo kluczowe można powiązać nazwy wartości i funkcje.|
|[Funkcje](../functions/index.md)|Zawiera omówienie funkcji w języku F #.|

## <a name="see-also"></a>Zobacz też
[Wartości zerowe](null-Values.md)

[Dokumentacja języka F #](../index.md)
