---
title: Typy wskaźników (Przewodnik programowania w języku C#)
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 124cc98b6f73b6014ab845ce5b9331e9f5292757
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146844"
---
# <a name="pointer-types-c-programming-guide"></a>Typy wskaźników (Przewodnik programowania w języku C#)

W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym. Deklaracja typu wskaźnika ma jedną z następujących form:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Typ określony przed `*` w wskaźnik typu jest nazywana **typu Obiekt obsługujący**. Dowolne z następujących typów może być typem obiekt obsługujący:

- Dowolnego typu całkowitoliczbowego: [sbyte](../../language-reference/keywords/sbyte.md), [bajtów](../../language-reference/keywords/byte.md), [krótki](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [długie](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).
- Wszystkie typy zmiennoprzecinkowe: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).
- [CHAR](../../language-reference/keywords/char.md).
- [wartość logiczna](../../language-reference/keywords/bool.md).
- [dziesiętna](../../language-reference/keywords/decimal.md).
- Wszelkie [wyliczenia](../../language-reference/keywords/enum.md) typu.
- Dowolny typ wskaźnika. Dzięki temu wyrażenia takie jak `void**`.
- Dowolny typ struktury zdefiniowany przez użytkownika, który zawiera tylko pola niezarządzanych typów.

Typy wskaźnika nie dziedziczą [obiektu](../../language-reference/keywords/object.md) i nie występują konwersje między typami wskaźnika a `object`. Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania. Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.

W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika. Na przykład:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Wskaźnik nie może wskazywać odwołania ani do [struktury](../../language-reference/keywords/struct.md) zawierającej odwołania, ponieważ odwołanie do obiektu może zostać usunięte nawet wtedy, gdy jest wskazywane przez wskaźnik do niego. Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.

Wartość zmiennej wskaźnika typu `myType*` to adres zmiennej typu `myType`. Poniżej przedstawiono przykłady deklaracji typów wskaźnika:

|Przykład|Opis|
|-------------|-----------------|
|`int* p`|`p` to wskaźnik do liczby całkowitej.|
|`int** p`|`p` to wskaźnik do wskaźnika do liczby całkowitej.|
|`int*[] p`|`p` to Jednowymiarowa tablica wskaźników do liczb całkowitych.|
|`char* p`|`p` jest wskaźnik do znaku.|
|`void* p`|`p` to wskaźnik do nieznanego typu.|

Operatora pośredniego wskaźnika * można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową. Na przykład przeanalizujmy następującą deklarację:

```csharp
int* myVariable;
```

Wyrażenie `*myVariable` oznacza `int` znaleziono pod adresem zawartym w zmiennej `myVariable`.

Istnieje kilka przykładów wskaźników można znaleźć w tematach [fixed Statement](../../language-reference/keywords/fixed-statement.md) i [konwersje wskaźników](../../programming-guide/unsafe-code-pointers/pointer-conversions.md). W poniższym przykładzie użyto `unsafe` — słowo kluczowe i `fixed` instrukcji i pokazuje, jak zwiększyć wartość wskaźnika wewnętrznego.  Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić. Przykłady te muszą być skompilowane z [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) zestaw opcji kompilatora.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Nie można zastosować operatora pośredniego do wskaźnika typu `void*`. Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.

Wskaźnik może mieć `null`. Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.

Przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie. Należy wziąć pod uwagę metodę, która zwraca wskaźnik do zmiennej lokalnej za pośrednictwem `in`, `out`, lub `ref` parametru lub jako wynik funkcji. Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.

W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:

|Operator/instrukcja|Zastosowanie|
|-------------------------|---------|
|*|Wykonuje operację wskaźnika pośredniego.|
|->|Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.|
|[]|Indeksuje wskaźnik.|
|`&`|Uzyskuje adres zmiennej.|
|++ oraz --|Zwiększa i zmniejsza wartość wskaźnika.|
|+ oraz -|Wykonuje operacje arytmetyczne na wskaźniku.|
|==,! =, \<, >, \<= i > =|Porównuje wskaźniki.|
|`stackalloc`|Przydziela pamięć na stosie.|
|`fixed` Instrukcja|Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.|

## <a name="c-language-specification"></a>Specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)  
- [Niebezpieczny kod i wskaźniki](index.md)  
- [Konwersje wskaźników](pointer-conversions.md)  
- [Wyrażenia wskaźników](pointer-expressions.md)  
- [Typy](../../language-reference/keywords/types.md)  
- [unsafe](../../language-reference/keywords/unsafe.md)  
- [fixed, instrukcja](../../language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../language-reference/keywords/stackalloc.md)  
- [Konwersja boxing i konwersja unboxing](../types/boxing-and-unboxing.md)
