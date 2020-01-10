---
title: zapieczętowany modyfikator- C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713108"
---
# <a name="sealed-c-reference"></a>sealed (odwołanie w C#)

W przypadku zastosowania do klasy modyfikator `sealed` uniemożliwia innym klasom dziedziczenie z tego typu. W poniższym przykładzie Klasa `B` dziedziczy po klasie `A`, ale żadna Klasa nie może dziedziczyć z klasy `B`.

```csharp
class A {}
sealed class B : A {}
```

Można również użyć modyfikatora `sealed` dla metody lub właściwości, która zastępuje wirtualną metodę lub właściwość w klasie bazowej. Dzięki temu można zezwolić klasom na pochodną klasy i uniemożliwić im zastępowanie określonych metod lub właściwości wirtualnych.

## <a name="example"></a>Przykład

W poniższym przykładzie `Z` dziedziczy po `Y`, ale `Z` nie może przesłonić funkcji wirtualnej `F` zadeklarowanej w `X` i zapieczętowanej w `Y`.

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Podczas definiowania nowych metod lub właściwości w klasie można zapobiegać występowaniu klas przez wyprowadzanie ich przez niezadeklarowanie ich jako [wirtualne](virtual.md).

Wystąpił błąd podczas używania modyfikatora [abstract](abstract.md) z klasą zapieczętowana, ponieważ Klasa abstrakcyjna musi być dziedziczona przez klasę, która dostarcza implementację metod abstrakcyjnych lub właściwości.

W przypadku zastosowania do metody lub właściwości modyfikator `sealed` musi być zawsze używany z [zastępowaniem](override.md).

Ponieważ struktury są niejawnie zapieczętowane, nie można ich dziedziczyć.

Aby uzyskać więcej informacji, zobacz [dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md).

Aby uzyskać więcej przykładów, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

W poprzednim przykładzie można spróbować dziedziczyć z klasy zapieczętowanej przy użyciu następującej instrukcji:

`class MyDerivedC: SealedClass {}   // Error`

Wynik jest komunikatem o błędzie:

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a>Uwagi

Aby określić, czy należy zapieczętować klasę, metodę lub właściwość, należy ogólnie wziąć pod uwagę następujące dwa punkty:

- Potencjalne korzyści wynikające z używania klas mogą uzyskać możliwość dostosowania klasy.

- Potencjalna Klasa może modyfikować klasy w taki sposób, że nie będą działać prawidłowo lub zgodnie z oczekiwaniami.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Modyfikatory](index.md)
- [override](override.md)
- [virtual](virtual.md)
