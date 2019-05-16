---
title: Wartości
description: Dowiedz się, jak wartości w F# są ilości, które mają określonego typu.
ms.date: 05/16/2016
ms.openlocfilehash: fe87bb568591b862737456ff92ba202ba7795e3d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641627"
---
# <a name="values"></a>Wartości

Wartości w F# są ilości, które mają określony typ; wartości mogą być liczb zmiennoprzecinkowych typu całkowitego lub zmiennoprzecinkowego, znaki lub tekst, list, sekwencji, tablice, krotek, związki dyskryminowane, rekordy, typy klas lub wartości funkcji.

## <a name="binding-a-value"></a>Powiązania wartości

Termin *powiązania* oznacza skojarzenie nazwy z definicji. `let` — Słowo kluczowe jest powiązana wartość, jak w następujących przykładach:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Typ wartości jest wnioskowany z definicji. Typ pierwotny, takich jak liczbą całkowitą lub zmiennoprzecinkową typ zależy od typu literału. W związku z tym, w poprzednim przykładzie, kompilator wnioskuje typ `b` jako `unsigned int`, podczas gdy kompilator wnioskuje typ `a` jako `int`. Typ wartości funkcji zależy od wartości zwracanej w treści funkcji. Aby uzyskać więcej informacji na temat typów wartości funkcji zobacz [funkcji](../functions/index.md). Aby uzyskać więcej informacji na temat typy literałów zobacz [literały](../literals.md).

Kompilator nie generuje diagnostycznych dotyczących powiązań nieużywane domyślnie. Aby otrzymywać te wiadomości, Włącz ostrzeżenie 1182 w pliku projektu lub podczas wywoływania kompilator (zobacz `--warnon` w obszarze [opcje kompilatora](../compiler-options.md)).

## <a name="why-immutable"></a>Dlaczego niezmienne?

Niezmienne wartości są wartościami, których nie można zmienić w czasie wykonywania programu. Jeśli są używane do języków, takich jak C++, Visual Basic lub C#, może okazać się zaskoczysz, F# umieszcza nadrzędności za pośrednictwem niezmienne wartości zamiast zmiennych, które można przypisać nowe wartości podczas wykonywania programu. Niezmienialnymi danymi jest istotnym elementem programowania funkcjonalnego. W środowisku wielowątkowym udostępnionego zmienne modyfikowalne, które mogą być zmieniane przez wielu inne wątki są trudne do zarządzania. Ponadto za pomocą zmienne modyfikowalne, czasami może być trudno stwierdzić, jeśli zmienna może ulec zmianie, gdy jest przekazywana do innej funkcji.

W czystych języków funkcjonalnych istnieją nie zmienne i funkcje zachowują się wyłącznie jako funkcji matematycznych. W przypadku, gdy kodu w języku procedurach używa przypisanie zmiennej, aby zmienić wartość, równoważny kod w języku funkcjonalności ma niezmienne wartość danych wejściowych, funkcję niezmienne i różne wartości niezmienne jako dane wyjściowe. Ta matematyczne poziom ścisłości umożliwia głębsze wnioskowania o zachowanie programu. Uzasadnienie większego jest kompilatory dokładniej sprawdzić kod i zoptymalizować bardziej efektywne i pomaga wykonywać stało się łatwiejsze do zrozumienia i wpisz poprawny kod. Funkcjonalny kod jest w związku z tym może być łatwiejszy do debugowania niż zwykłe kod proceduralny.

F#nie jest czysty język funkcjonalności, jeszcze w pełni obsługuje programowania funkcjonalnego. Za pomocą niezmienialnych wartości jest dobrym rozwiązaniem, ponieważ w ten sposób swój kod, aby korzystać z ważnym aspektem programowania funkcjonalnego.

## <a name="mutable-variables"></a>Zmienne modyfikowalne

Można użyć słowa kluczowego `mutable` można określić zmienną, którą można zmienić. Zmienne modyfikowalne w F# powinien mieć zwykle ograniczony zakres jako pole typu lub wartości lokalnej. Zmienne modyfikowalne o ograniczonym zakresie są łatwiejsze do kontroli i mniej prawdopodobne, można zmodyfikować w nieprawidłowy sposób.

Początkowa wartość można przypisać do modyfikowalnej zmiennej, za pomocą `let` — słowo kluczowe w taki sam sposób, jak definiuje się wartość. Jednak różnica polega na tym, można następnie przypisać nowe wartości zmienne modyfikowalne przy użyciu `<-` operatora, jak w poniższym przykładzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

Wartości oznaczone `mutable` może zostać automatycznie podwyższony do `'a ref` Jeśli przechwycone przez zamknięcie, w tym tworzenie zamknięć, takich jak formularze `seq` konstruktorów. Jeśli chcesz otrzymywać powiadomienia, gdy ten problem wystąpi, Włącz ostrzeżenie 3180 w pliku projektu lub podczas wywoływania kompilator.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Powiązania „let”](../functions/let-bindings.md)|Zawiera informacje o używaniu `let` — słowo kluczowe, aby powiązać nazwy wartości i funkcje.|
|[Funkcje](../functions/index.md)|Zawiera omówienie funkcji F#.|

## <a name="see-also"></a>Zobacz także

- [Wartości null](null-Values.md)
- [Dokumentacja języka F#](../index.md)
