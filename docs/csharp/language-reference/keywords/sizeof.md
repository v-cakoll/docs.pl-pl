---
title: sizeof (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 37eb9345edc31a8d318540fd528f311059225de4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184208"
---
# <a name="sizeof-c-reference"></a>sizeof (odwołanie w C#)

Używany do uzyskiwania rozmiar w bajtach dla typu niezarządzanego.

Typy niezarządzanwe obejmują:

- Typy proste, które są wymienione w poniższej tabeli:

   |Wyrażenie|Stała wartość|
   |----------------|--------------------|
   |`sizeof(sbyte)`|1|
   |`sizeof(byte)`|1|
   |`sizeof(short)`|2|
   |`sizeof(ushort)`|2|
   |`sizeof(int)`|4|
   |`sizeof(uint)`|4|
   |`sizeof(long)`|8|
   |`sizeof(ulong)`|8|
   |`sizeof(char)`|2 (Unicode)|
   |`sizeof(float)`|4|
   |`sizeof(double)`|8|
   |`sizeof(decimal)`|16|
   |`sizeof(bool)`|1|

- Typy wyliczenia.

- Typy wskaźników.

- Struktury zdefiniowany przez użytkownika, które nie zawierają żadnych pól wystąpień lub automatycznie implementowane właściwości wystąpienia, które są typami odwołań lub typy utworzone.

Poniższy przykład pokazuje, jak pobrać rozmiar `int`:

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a>Uwagi

Począwszy od wersji 2.0 języka C#, stosowanie `sizeof` prostego lub typu wyliczeniowego typów nie wymaga już czy kod jest kompilowany w [niebezpieczne](unsafe.md) kontekstu.

Operator `sizeof` nie może być przeciążony. Wartości zwracane przez `sizeof` operator są typu `int`. W poprzedniej tabeli przedstawiono wartości stałych, które są zastępowane dla `sizeof` wyrażenia, które mają pewne proste typy jako argumenty operacji.

Dla wszystkich innych typów, w tym struktur, `sizeof` operatora można używać tylko w blokach niebezpieczny kod. Chociaż można używać <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, wartość zwracana przez tę metodę nie zawsze jest taka sama jak wartość zwrócona przez obiekt `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> Zwraca rozmiar po typ został przekazany, natomiast `sizeof` zwraca rozmiar, ponieważ zawiera ona przydzielone przez środowisko uruchomieniowe języka wspólnego, włączając wszelkie dopełnienie.

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Słowa kluczowe operatora](operator-keywords.md)
- [enum](enum.md)
- [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)
- [Struktury](../../programming-guide/classes-and-structs/structs.md)
- [Stałe](../../programming-guide/classes-and-structs/constants.md)