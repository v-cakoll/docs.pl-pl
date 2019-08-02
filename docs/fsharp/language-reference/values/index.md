---
title: Wartości
description: Dowiedz się, F# w jaki sposób wartości w są ilościami o określonym typie.
ms.date: 05/16/2016
ms.openlocfilehash: ed7a5b069a5a47aacf0cce4cfa754ded46f6e84a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630800"
---
# <a name="values"></a>Wartości

Wartości w F# to ilości, które mają określony typ; wartości mogą być liczbami całkowitymi lub zmiennoprzecinkowymi, znakami lub tekstem, listami, sekwencjami, tablicami, krotkami, związkami rozłącznych, rekordami, typami klas lub wartościami funkcji.

## <a name="binding-a-value"></a>Powiązanie wartości

Termin *powiązania* oznacza skojarzenie nazwy z definicją. `let` Słowo kluczowe wiąże wartość, jak w następujących przykładach:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Typ wartości jest wywnioskowany na podstawie definicji. Dla typu pierwotnego, takiego jak liczba całkowita lub zmiennoprzecinkowa, typ jest określany na podstawie typu literału. W związku z tym w poprzednim przykładzie `b` kompilator wnioskuje typ, który ma być `unsigned int`, podczas gdy `a` kompilator wnioskuje typ, który ma `int`być. Typ wartości funkcji jest określany na podstawie wartości zwracanej w treści funkcji. Aby uzyskać więcej informacji na temat typów wartości funkcji [](../functions/index.md), zobacz Functions. Aby uzyskać więcej informacji na temat typów literałów, zobacz [literały](../literals.md).

Kompilator nie wystawia domyślnie diagnostyki nieużywanych powiązań. Aby otrzymywać te komunikaty, Włącz Ostrzeżenie 1182 w pliku projektu lub podczas wywoływania kompilatora (zobacz `--warnon` w obszarze [Opcje kompilatora](../compiler-options.md)).

## <a name="why-immutable"></a>Dlaczego jest to niezmienne?

Niezmienne wartości to wartości, których nie można zmienić w trakcie wykonywania programu. Jeśli są używane do języków takich jak C++, Visual Basic lub C#, może się okazać, że F# zaskakujące Primacy zbyt zmienne wartości, a nie zmienne, które mogą przypisywać nowe wartości podczas wykonywania programu. Niezmienne dane to istotny element programowania funkcjonalnego. W środowisku wielowątkowym trudno jest zarządzać udostępnionymi zmiennymi modyfikowalnymi, które mogą być zmieniane przez wiele różnych wątków. Ponadto ze zmiennymi modyfikowalnymi może być czasami trudno stwierdzić, czy zmienna może zostać zmieniona, gdy zostanie ona przeniesiona do innej funkcji.

W czystych językach funkcjonalnych nie ma żadnych zmiennych, a funkcje zachowują się wyłącznie jako funkcje matematyczne. Gdzie kod w języku proceduralnym używa przypisania zmiennej do zmiany wartości, odpowiedni kod w języku funkcjonalnym ma niemodyfikowalną wartość, która jest danymi wejściowymi, niemodyfikowalną funkcją i różne zmienne wartości jako dane wyjściowe. Ten matematyczny efekt daje ściślejszy powód zachowania programu. To ściślejsze przyczyny to umożliwienie kompilatorom dokładniejszego sprawdzenia kodu i bardziej wydajnego optymalizowania oraz ułatwia deweloperom zrozumienie i pisanie poprawnego kodu. Z tego względu kod funkcjonalny jest łatwiejszy do debugowania niż zwykły kod proceduralny.

F#to nie jest czysty język funkcjonalny, ale w pełni obsługuje programowanie funkcjonalne. Korzystanie z niezmiennych wartości jest dobrym sposobem, ponieważ dzięki temu kod może korzystać z ważnego aspektu programowania funkcjonalnego.

## <a name="mutable-variables"></a>Zmienne modyfikowalne

Możesz użyć słowa kluczowego `mutable` , aby określić zmienną, którą można zmienić. Zmienne modyfikowalne F# w programie powinny zwykle mieć ograniczony zakres, jako pole typu lub jako wartość lokalną. Zmienne modyfikowalne z ograniczonym zakresem są łatwiejsze w kontroli i nie mogą być modyfikowane w nieprawidłowy sposób.

Można przypisać wartość początkową do zmiennej modyfikowalnej za pomocą `let` słowa kluczowego w taki sam sposób jak w przypadku definiowania wartości. Jednak różnica polega na tym, że można później przypisywać nowe wartości do zmiennych modyfikowalnych za `<-` pomocą operatora, jak w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

Wartości oznaczone `mutable` mogą zostać automatycznie podwyższone `'a ref` do, jeśli zostały przechwycone przez zamknięcie, w tym formularze tworzące zamknięcia, `seq` takie jak konstruktory. Jeśli chcesz otrzymywać powiadomienia, gdy wystąpi taka sytuacja, Włącz Ostrzeżenie 3180 w pliku projektu lub podczas wywoływania kompilatora.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Powiązania „let”](../functions/let-bindings.md)|Zawiera informacje dotyczące używania `let` słowa kluczowego do powiązania nazw z wartościami i funkcjami.|
|[Funkcje](../functions/index.md)|Zawiera omówienie funkcji w programie F#.|

## <a name="see-also"></a>Zobacz także

- [Wartości null](null-Values.md)
- [Dokumentacja języka F#](../index.md)
