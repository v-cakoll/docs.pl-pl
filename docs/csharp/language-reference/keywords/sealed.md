---
title: zapieczętowane modyfikator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 7b9551fe892b0335fb445ab9edce4facca0badbe
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833344"
---
# <a name="sealed-c-reference"></a>sealed (odwołanie w C#)

Po zastosowaniu do klasy, `sealed` modyfikator uniemożliwia innych klas z niego dziedziczącego. W poniższym przykładzie klasa `B` dziedziczy z klasy `A`, ale klasa nie może dziedziczyć z klasy `B`.

```csharp
class A {}
sealed class B : A {}
```

Można również użyć `sealed` modyfikator metoda lub właściwość, która zastępuje metodę wirtualną lub właściwości w klasie bazowej. Dzięki temu można umożliwić klasy pochodzi od klasy i uniemożliwić zastępowanie konkretnych metod wirtualnych lub właściwości.

## <a name="example"></a>Przykład

W poniższym przykładzie `Z` dziedziczy `Y` , ale `Z` nie może przesłonić funkcji wirtualnej `F` zadeklarowanego w `X` i zamkniętych w `Y`.

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Definiując nowe metody lub właściwości w klasie, można zapobiec klas pochodnych zastępowania ich nie deklarując je jako [wirtualnego](virtual.md).

Jest to błąd, aby użyć [abstrakcyjne](abstract.md) modyfikator za pomocą klasy zapieczętowanej ponieważ klasy abstrakcyjnej muszą być dziedziczone przez klasę, która dostarcza implementację metody abstrakcyjne lub właściwości.

Po zastosowaniu do metody lub właściwości, `sealed` modyfikator zawsze musi być używany z [zastąpienia](override.md).

Ponieważ struktury niejawnie są zamknięte, nie może być dziedziczona.

Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../programming-guide/classes-and-structs/inheritance.md).

Aby uzyskać więcej przykładów, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

W poprzednim przykładzie możesz spróbować dziedziczą z klasy zapieczętowanej przy użyciu następujących instrukcji:

`class MyDerivedC: SealedClass {}   // Error`

Wynik jest komunikat o błędzie:

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a>Uwagi

Aby ustalić, czy ma być Zapieczętuj klasę, metodę lub właściwość, zazwyczaj należy rozważyć następujące dwa punkty:

- Potencjalnych korzyści, że wyprowadzanie klas mogą uzyskać za pośrednictwem możliwość dostosowania swojej klasy.

- Ryzyko, że wyprowadzanie klas można zmodyfikować klas w taki sposób, że będzie już działać poprawnie lub oczekuje.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Modyfikatory](modifiers.md)
- [override](override.md)
- [virtual](virtual.md)
