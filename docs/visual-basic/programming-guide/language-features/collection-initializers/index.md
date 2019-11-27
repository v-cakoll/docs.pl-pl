---
title: Inicjatory kolekcji
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: fbdd116298c530ae54677631eff7dac2f22c0fe2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346783"
---
# <a name="collection-initializers-visual-basic"></a>Inicjatory kolekcji (Visual Basic)

*Inicjatory kolekcji* zapewniają skróconą składnię, która umożliwia utworzenie kolekcji i wypełnienie jej początkowym zestawem wartości. Inicjatory kolekcji są przydatne podczas tworzenia kolekcji z zestawu znanych wartości, na przykład listy opcji menu lub kategorii, początkowego zestawu wartości liczbowych, statycznej listy ciągów, takich jak nazwy dni lub miesięcy, lub lokalizacji geograficznych, takich jak Lista Stanów, które są używane na potrzeby walidacji.

Aby uzyskać więcej informacji na temat kolekcji, zobacz [kolekcje](../../../../visual-basic/programming-guide/concepts/collections.md).

Inicjator kolekcji jest identyfikowany za pomocą słowa kluczowego `From`, po którym następuje nawiasy klamrowe (`{}`). Jest to podobne do składni literału tablicowego, która jest opisana w [tablicach](../../../../visual-basic/programming-guide/language-features/arrays/index.md). W poniższych przykładach przedstawiono różne sposoby używania inicjatorów kolekcji do tworzenia kolekcji.

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> C#Program udostępnia także inicjatory kolekcji. C#Inicjatory kolekcji oferują te same funkcje co Visual Basic inicjatorów kolekcji. Aby uzyskać więcej informacji C# na temat inicjatorów kolekcji, zobacz [Inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="syntax"></a>Składnia

Inicjator kolekcji składa się z listy wartości rozdzielonych przecinkami, które są ujęte w nawiasy klamrowe (`{}`) poprzedzone słowem kluczowym `From`, jak pokazano w poniższym kodzie.

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

Podczas tworzenia kolekcji, takiej jak <xref:System.Collections.Generic.List%601> lub <xref:System.Collections.Generic.Dictionary%602>, należy podać typ kolekcji przed inicjatorem kolekcji, jak pokazano w poniższym kodzie.

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> Nie można połączyć inicjatora kolekcji i inicjatora obiektów w celu zainicjowania tego samego obiektu kolekcji. Inicjatorów obiektów można użyć do zainicjowania obiektów w inicjatorze kolekcji.

## <a name="creating-a-collection-by-using-a-collection-initializer"></a>Tworzenie kolekcji przy użyciu inicjatora kolekcji

Podczas tworzenia kolekcji przy użyciu inicjatora kolekcji każda wartość podana w inicjatorze kolekcji jest przekazywana do odpowiedniej metody `Add` kolekcji. Na przykład jeśli utworzysz <xref:System.Collections.Generic.List%601> przy użyciu inicjatora kolekcji, każda wartość ciągu w inicjatorze kolekcji zostanie przeniesiona do metody <xref:System.Collections.Generic.List%601.Add%2A>. Jeśli chcesz utworzyć kolekcję przy użyciu inicjatora kolekcji, określony typ musi być prawidłowym typem kolekcji. Przykłady prawidłowych typów kolekcji obejmują klasy implementujące interfejs <xref:System.Collections.Generic.IEnumerable%601> lub dziedziczenia klasy <xref:System.Collections.CollectionBase>. Określony typ musi również uwidaczniać metodę `Add`, która spełnia następujące kryteria.

- Metoda `Add` musi być dostępna z zakresu, w którym jest wywoływany inicjator kolekcji. Metoda `Add` nie musi być publiczna, jeśli używasz inicjatora kolekcji w scenariuszu, w którym można uzyskać dostęp do niepublicznych metod kolekcji.

- Metoda `Add` musi być elementem członkowskim wystąpienia lub `Shared` składową klasy kolekcji lub metodą rozszerzenia.

- Metoda `Add` musi istnieć, którą można dopasować, na podstawie reguł rozdzielczości przeciążenia, do typów, które są podane w inicjatorze kolekcji.

 Na przykład poniższy kod ilustruje sposób tworzenia kolekcji `List(Of Customer)` przy użyciu inicjatora kolekcji. Po uruchomieniu kodu każdy obiekt `Customer` jest przenoszona do metody `Add(Customer)` listy ogólnej.

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

Poniższy przykład kodu pokazuje równoważny kod, który nie używa inicjatora kolekcji.

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

Jeśli kolekcja ma metodę `Add`, która ma parametry, które pasują do konstruktora obiektu `Customer`, można zagnieżdżać wartości parametrów dla metody `Add` w inicjatorach kolekcji, jak opisano w następnej sekcji. Jeśli kolekcja nie ma takiej metody `Add`, można ją utworzyć jako metodę rozszerzenia. Aby zapoznać się z przykładem sposobu tworzenia metody `Add` jako metody rozszerzenia dla kolekcji, zobacz [How to: Create a Add Extension Metoda używana przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Aby zapoznać się z przykładem tworzenia kolekcji niestandardowej, która może być używana z inicjatorem kolekcji, zobacz [How to: Create a Collection używany przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).

## <a name="nesting-collection-initializers"></a>Zagnieżdżanie inicjatorów kolekcji

Można zagnieżdżać wartości w inicjatorze kolekcji, aby identyfikować określone Przeciążenie metody `Add` dla tworzonej kolekcji. Wartości przesyłane do metody `Add` muszą być oddzielone przecinkami i ujęte w nawiasy klamrowe (`{}`), tak jak w przypadku literału tablicy lub inicjatora kolekcji.

Podczas tworzenia kolekcji przy użyciu wartości zagnieżdżonych każdy element zagnieżdżonej listy wartości jest przenoszona jako argument do metody `Add`, która pasuje do typów elementów. Poniższy przykład kodu tworzy <xref:System.Collections.Generic.Dictionary%602>, w którym klucze są typu `Integer`, a wartości są typu `String`. Każda z zagnieżdżonych list wartości jest dopasowywana do metody <xref:System.Collections.Generic.Dictionary%602.Add%2A> `Dictionary`.

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

Poprzedni przykład kodu jest równoważny do poniższego kodu.

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

Tylko zagnieżdżone listy wartości z pierwszego poziomu zagnieżdżania są wysyłane do metody `Add` dla typu kolekcji. Dokładniejsze poziomy zagnieżdżania są traktowane jako literały tablicowe, a zagnieżdżone listy wartości nie są dopasowywane do metody `Add` dowolnej kolekcji.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|---|---|
|[Instrukcje: tworzenie i dodawanie metody rozszerzenia używanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Pokazuje, jak utworzyć metodę rozszerzenia o nazwie `Add`, która może być używana do wypełniania kolekcji wartościami z inicjatora kolekcji.|
|[Instrukcje: tworzenie kolekcji używanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Pokazuje, jak włączyć użycie inicjatora kolekcji, dołączając metodę `Add` w klasie kolekcji implementującej `IEnumerable`.|

## <a name="see-also"></a>Zobacz także

- [Kolekcje](../../../../visual-basic/programming-guide/concepts/collections.md)
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Operator New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Właściwości zaimplementowane automatycznie](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Instrukcje: Inicjowanie zmiennej tablicowej w Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Instrukcje: tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
