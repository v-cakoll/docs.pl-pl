---
title: modyfikator zapieczętowany - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713108"
---
# <a name="sealed-c-reference"></a>sealed (odwołanie w C#)

Po zastosowaniu do klasy `sealed` modyfikator uniemożliwia innym klasom dziedziczenie z niego. W poniższym przykładzie `B` klasa dziedziczy z klasy `A`, `B`ale żadna klasa nie może dziedziczyć z klasy .

```csharp
class A {}
sealed class B : A {}
```

Można również użyć `sealed` modyfikatora na metodę lub właściwość, która zastępuje metodę wirtualną lub właściwość w klasie podstawowej. Dzięki temu można zezwolić klas pochodzić z klasy i uniemożliwić im zastępowanie określonych metod wirtualnych lub właściwości.

## <a name="example"></a>Przykład

W poniższym `Z` przykładzie dziedziczy `Y` z, ale `F` `X` `Y` `Z` nie można zastąpić funkcji wirtualnej, która jest zadeklarowana i zapieczętowane w .

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Podczas definiowania nowych metod lub właściwości w klasie, można zapobiec klas pochodnych z zastępowania ich, nie deklarując je jako [wirtualne](virtual.md).

Jest to błąd, aby użyć [modyfikatora abstrakcyjnego](abstract.md) z zapieczętowaną klasą, ponieważ klasa abstrakcyjna musi być dziedziczona przez klasę, która zapewnia implementację metod abstrakcyjnych lub właściwości.

Po zastosowaniu do metody lub `sealed` właściwości, modyfikator musi być zawsze używany z [override](override.md).

Ponieważ struktury są niejawnie zapieczętowane, nie mogą być dziedziczone.

Aby uzyskać więcej informacji, zobacz [Dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md).

Aby uzyskać więcej przykładów, zobacz [klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klasy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

W poprzednim przykładzie można spróbować dziedziczyć z zapieczętowanej klasy przy użyciu następującej instrukcji:

`class MyDerivedC: SealedClass {}   // Error`

Rezultatem jest komunikat o błędzie:

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a>Uwagi

Aby ustalić, czy należy uszczelnić klasę, metodę lub właściwość, należy ogólnie rozważyć następujące dwa punkty:

- Potencjalne korzyści, które klasy pochodne mogą uzyskać poprzez możliwość dostosowania klasy.

- Potencjał, że klasy pochodne może modyfikować klas w taki sposób, że nie będą już działać poprawnie lub zgodnie z oczekiwaniami.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Klasy statyczne i statyczni członkowie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Modyfikatory](index.md)
- [override](override.md)
- [virtual](virtual.md)
