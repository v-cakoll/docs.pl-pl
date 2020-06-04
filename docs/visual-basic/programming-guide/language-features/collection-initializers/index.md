---
title: Inicjatory kolekcji
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: 1d2d5adc7266faaa1636e568d6433429761eeaab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414546"
---
# <a name="collection-initializers-visual-basic"></a>Inicjatory kolekcji (Visual Basic)

*Inicjatory kolekcji* zapewniają skróconą składnię, która umożliwia utworzenie kolekcji i wypełnienie jej początkowym zestawem wartości. Inicjatory kolekcji są przydatne podczas tworzenia kolekcji na podstawie zestawu znanych wartości, na przykład listy opcji menu lub kategorii, początkowego zestawu wartości liczbowych, statycznej listy ciągów, takich jak nazwy dni lub miesięcy, lub lokalizacji geograficznych, takich jak lista stanów, która jest używana na potrzeby walidacji.

Aby uzyskać więcej informacji na temat kolekcji, zobacz [kolekcje](../../concepts/collections.md).

Inicjator kolekcji można zidentyfikować za pomocą `From` słowa kluczowego, po którym następuje nawiasy klamrowe ( `{}` ). Jest to podobne do składni literału tablicowego, która jest opisana w [tablicach](../arrays/index.md). W poniższych przykładach przedstawiono różne sposoby używania inicjatorów kolekcji do tworzenia kolekcji.

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> Język C# zawiera również Inicjatory kolekcji. Inicjatory kolekcji języka C# zapewniają te same funkcje co Visual Basic inicjatorów kolekcji. Aby uzyskać więcej informacji na temat inicjatorów kolekcji C#, zobacz [Inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="syntax"></a>Składnia

Inicjator kolekcji składa się z listy wartości rozdzielonych przecinkami, które są ujęte w nawiasy klamrowe ( `{}` ) poprzedzone `From` słowem kluczowym, jak pokazano w poniższym kodzie.

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

Podczas tworzenia kolekcji, takiej jak <xref:System.Collections.Generic.List%601> lub <xref:System.Collections.Generic.Dictionary%602> , należy podać typ kolekcji przed inicjatorem kolekcji, jak pokazano w poniższym kodzie.

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> Nie można połączyć inicjatora kolekcji i inicjatora obiektów w celu zainicjowania tego samego obiektu kolekcji. Inicjatorów obiektów można użyć do zainicjowania obiektów w inicjatorze kolekcji.

## <a name="creating-a-collection-by-using-a-collection-initializer"></a>Tworzenie kolekcji przy użyciu inicjatora kolekcji

Podczas tworzenia kolekcji przy użyciu inicjatora kolekcji każda wartość podana w inicjatorze kolekcji jest przekazywana do odpowiedniej `Add` metody kolekcji. Na przykład, jeśli tworzysz <xref:System.Collections.Generic.List%601> przy użyciu inicjatora kolekcji, każda wartość ciągu w inicjatorze kolekcji jest przenoszona do <xref:System.Collections.Generic.List%601.Add%2A> metody. Jeśli chcesz utworzyć kolekcję przy użyciu inicjatora kolekcji, określony typ musi być prawidłowym typem kolekcji. Przykłady prawidłowych typów kolekcji obejmują klasy implementujące <xref:System.Collections.Generic.IEnumerable%601> interfejs lub dziedziczenia <xref:System.Collections.CollectionBase> klasy. Określony typ musi również uwidaczniać `Add` metodę, która spełnia następujące kryteria.

- `Add`Metoda musi być dostępna z zakresu, w którym jest wywoływany inicjator kolekcji. `Add`Metoda nie musi być publiczna, jeśli używasz inicjatora kolekcji w scenariuszu, w którym można uzyskać dostęp do niepublicznych metod kolekcji.

- `Add`Metoda musi być elementem członkowskim wystąpienia lub `Shared` członkiem klasy kolekcji lub metodą rozszerzenia.

- `Add`Musi istnieć Metoda, która może być dopasowana na podstawie reguł rozdzielczości przeciążenia, do typów, które są podane w inicjatorze kolekcji.

 Poniższy przykład kodu pokazuje, jak utworzyć `List(Of Customer)` kolekcję przy użyciu inicjatora kolekcji. Gdy kod jest uruchamiany, każdy `Customer` obiekt jest przesyłany do `Add(Customer)` metody listy ogólnej.

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

Poniższy przykład kodu pokazuje równoważny kod, który nie używa inicjatora kolekcji.

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

Jeśli kolekcja ma `Add` metodę, która ma parametry, które pasują do konstruktora `Customer` obiektu, można zagnieżdżać wartości parametrów dla `Add` metody w inicjatorach kolekcji, jak to opisano w następnej sekcji. Jeśli kolekcja nie ma takiej `Add` metody, można ją utworzyć jako metodę rozszerzenia. Aby zapoznać się z przykładem sposobu tworzenia `Add` metody jako metody rozszerzenia dla kolekcji, zobacz [How to: Create a Add Extension Method, używany przez inicjator kolekcji](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Aby zapoznać się z przykładem tworzenia kolekcji niestandardowej, która może być używana z inicjatorem kolekcji, zobacz [How to: Create a Collection używany przez inicjator kolekcji](how-to-create-a-collection-used-by-a-collection-initializer.md).

## <a name="nesting-collection-initializers"></a>Zagnieżdżanie inicjatorów kolekcji

Można zagnieżdżać wartości w inicjatorze kolekcji, aby identyfikować określone Przeciążenie `Add` metody dla tworzonej kolekcji. Wartości przesyłane do `Add` metody muszą być oddzielone przecinkami i ujęte w nawiasy klamrowe ( `{}` ), tak jak w przypadku literału tablicy lub inicjatora kolekcji.

Podczas tworzenia kolekcji przy użyciu wartości zagnieżdżonych każdy element zagnieżdżonej listy wartości jest przenoszona jako argument do `Add` metody, która pasuje do typów elementów. Poniższy przykład kodu tworzy na przykład, <xref:System.Collections.Generic.Dictionary%602> w którym klucze są typu `Integer` , a wartości są typu `String` . Każda z zagnieżdżonych list wartości jest dopasowywana do <xref:System.Collections.Generic.Dictionary%602.Add%2A> metody dla `Dictionary` .

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

Poprzedni przykład kodu jest równoważny do poniższego kodu.

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

Tylko zagnieżdżone listy wartości z pierwszego poziomu zagnieżdżania są wysyłane do `Add` metody dla typu kolekcji. Dokładniejsze poziomy zagnieżdżania są traktowane jako literały tablicowe, a zagnieżdżone listy wartości nie są dopasowywane do `Add` metody żadnej kolekcji.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|---|---|
|[Instrukcje: tworzenie i dodawanie metody rozszerzenia używanej przez inicjator kolekcji](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Pokazuje, jak utworzyć metodę rozszerzenia o nazwie `Add` , która może być używana do wypełniania kolekcji wartościami z inicjatora kolekcji.|
|[Instrukcje: tworzenie kolekcji używanej przez inicjator kolekcji](how-to-create-a-collection-used-by-a-collection-initializer.md)|Pokazuje, jak włączyć użycie inicjatora kolekcji, dołączając `Add` metodę w klasie kolekcji implementującej `IEnumerable` .|

## <a name="see-also"></a>Zobacz też

- [Kolekcje](../../concepts/collections.md)
- [Tablice](../arrays/index.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Operator new](../../../language-reference/operators/new-operator.md)
- [Właściwości zaimplementowane automatycznie](../procedures/auto-implemented-properties.md)
- [Porady: inicjowanie zmiennej tablicy w języku Visual Basic](../arrays/how-to-initialize-an-array-variable.md)
- [Wnioskowanie o typie lokalnym](../variables/local-type-inference.md)
- [Typy anonimowe](../objects-and-classes/anonymous-types.md)
- [Wprowadzenie do LINQ w Visual Basic](../linq/introduction-to-linq.md)
- [Instrukcje: tworzenie listy elementów](../../concepts/linq/how-to-create-a-list-of-items.md)
