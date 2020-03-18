---
title: Typy wskaźników — przewodnik programowania C#
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: dc03744559a87a2548c5bee9452c22cd20f337b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627713"
---
# <a name="pointer-types-c-programming-guide"></a>Typy wskaźników (Przewodnik programowania w języku C#)

W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym. Deklaracja typu wskaźnika ma jedną z następujących form:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Typ określony przed `*` typem wskaźnika jest nazywany **typem referent**. Tylko [typ niezarządzany](../../language-reference/builtin-types/unmanaged-types.md) może być typem referent.

Typy wskaźników nie dziedziczą z [obiektu](../../language-reference/builtin-types/reference-types.md) i `object`nie istnieją żadne konwersje między typami wskaźników i . Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania. Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.

W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika. Przykład:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Wskaźnik nie może wskazywać odwołania lub [struktury,](../../language-reference/builtin-types/struct.md) która zawiera odwołania, ponieważ odwołanie do obiektu może być zbierane elementów, nawet jeśli wskaźnik wskazuje na niego. Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.

Wartość zmiennej wskaźnika `myType*` typu jest adresem zmiennej `myType`typu . Poniżej przedstawiono przykłady deklaracji typów wskaźnika:

|Przykład|Opis|
|-------------|-----------------|
|`int* p`|`p`jest wskaźnikiem do liczby całkowitej.|
|`int** p`|`p`jest wskaźnikiem do wskaźnika do liczby całkowitej.|
|`int*[] p`|`p`jest jednowymiarową tablicą wskaźników do liczb całkowitych.|
|`char* p`|`p`jest wskaźnikiem do znaku.|
|`void* p`|`p`jest wskaźnikiem do nieznanego typu.|

Operatora pośredniego wskaźnika * można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową. Na przykład przeanalizujmy następującą deklarację:

```csharp
int* myVariable;
```

Wyrażenie `*myVariable` oznacza zmienną `int` znalezioną pod adresem `myVariable`zawartą w pliku .

Istnieje kilka przykładów wskaźników w tematach [stałych konwersji instrukcji](../../language-reference/keywords/fixed-statement.md) i [wskaźnika](./pointer-conversions.md). W poniższym `unsafe` przykładzie użyto słowa kluczowego `fixed` i instrukcji oraz pokazano, jak zwiększać wskaźnik wnętrza.  Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić. Te przykłady muszą być skompilowane z zestawem opcji [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilatora.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Nie można zastosować operatora pośredni do `void*`wskaźnika typu . Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.

Wskaźnik może `null`być . Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.

Przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie. Należy wziąć pod uwagę metodę, która `in`zwraca `out`wskaźnik `ref` do zmiennej lokalnej za pośrednictwem , lub parametru lub jako wynik funkcji. Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.

W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:

|Operator/instrukcja|Użycie|
|-------------------------|---------|
|`*`|Wykonuje operację wskaźnika pośredniego.|
|`->`|Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.|
|`[]`|Indeksuje wskaźnik.|
|`&`|Uzyskuje adres zmiennej.|
|`++` i `--`|Zwiększa i zmniejsza wartość wskaźnika.|
|`+` i `-`|Wykonuje operacje arytmetyczne na wskaźniku.|
|`==``!=`, `<`, `>` `<=`, oraz`>=`|Porównuje wskaźniki.|
|[`stackalloc`Operator](../../language-reference/operators/stackalloc.md)|Przydziela pamięć na stosie.|
|[`fixed`Instrukcja](../../language-reference/keywords/fixed-statement.md)|Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.|

Aby uzyskać więcej informacji na temat operatorów związanych ze wskaźnikiem, zobacz [Operatory powiązane ze wskaźnikiem](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [pointer typy](~/_csharplang/spec/unsafe-code.md#pointer-types) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [Konwersje wskaźników](pointer-conversions.md)
- [Typy odwołań](../../language-reference/keywords/reference-types.md)
- [Typy wartości](../../language-reference/builtin-types/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
