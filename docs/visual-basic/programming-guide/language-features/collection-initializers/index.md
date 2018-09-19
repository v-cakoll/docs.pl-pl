---
title: Inicjatory kolekcji (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: c22599f50ac071245a1381d267f3f7cb66806174
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991626"
---
# <a name="collection-initializers-visual-basic"></a>Inicjatory kolekcji (Visual Basic)
*Inicjatory kolekcji* zapewniają skróconą składnię, która umożliwia tworzenie kolekcji i wypełnianie jej początkowy zestaw wartości. Inicjatory kolekcji są przydatne, gdy tworzysz kolekcję z zestawu znane wartości, na przykład listę opcji menu lub kategorii, początkowy zestaw wartości liczbowych, statycznej listy ciągów, takich jak dzień lub miesiąc nazwy lub lokalizacje geograficzne, takich jak Lista stanów, który służy do sprawdzania poprawności.  
  
 Aby uzyskać więcej informacji na temat kolekcji, zobacz [kolekcje](../../../../visual-basic/programming-guide/concepts/collections.md).  
  
 Można zidentyfikować za pomocą inicjatora kolekcji `From` — słowo kluczowe następuje nawiasy klamrowe (`{}`). Jest to podobne do składni literału tablicy, opisaną w [tablic](../../../../visual-basic/programming-guide/language-features/arrays/index.md). W poniższych przykładach pokazano różne sposoby tworzenia kolekcji za pomocą inicjatory kolekcji.  
  
 [!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]  
  
> [!NOTE]
>  C# zawiera również inicjatory kolekcji. Inicjatory kolekcji języka C# zapewnia taką samą funkcjonalność jak inicjatory kolekcji języka Visual Basic. Aby uzyskać więcej informacji na temat inicjatory kolekcji języka C#, zobacz [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="syntax"></a>Składnia  
 Inicjator kolekcji zawiera listę wartości rozdzielonych przecinkami, które są ujęte w nawiasy klamrowe (`{}`), poprzedzającą `From` — słowo kluczowe, jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]  
  
 Podczas tworzenia kolekcji, takie jak <xref:System.Collections.Generic.List%601> lub <xref:System.Collections.Generic.Dictionary%602>, należy podać typ kolekcji przed inicjatora kolekcji, jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]  
  
> [!NOTE]
>  Nie można łączyć zarówno inicjatora kolekcji i inicjatora obiektów, aby zainicjować tego samego obiektu kolekcji. Inicjatory obiektów umożliwia inicjowanie obiektów w inicjatorze kolekcji.  
  
## <a name="creating-a-collection-by-using-a-collection-intializer"></a>Tworzenie kolekcji przy użyciu inicjatora kolekcji  
 Podczas tworzenia kolekcji za pomocą inicjatora kolekcji każdej wartości, które jest dostarczone w inicjatorze kolekcji jest przekazywany do odpowiedniej `Add` metody kolekcji. Na przykład, jeśli tworzysz <xref:System.Collections.Generic.List%601> za pomocą inicjatora kolekcji, każda wartość ciągu w inicjatora kolekcji jest przekazywany do <xref:System.Collections.Generic.List%601.Add%2A> metody. Jeśli chcesz utworzyć kolekcję przy użyciu inicjatora kolekcji, określony typ musi być prawidłową kolekcję typów. Typy kolekcji prawidłowe przykłady klas, które implementują <xref:System.Collections.Generic.IEnumerable%601> interfejs lub dziedziczyć <xref:System.Collections.CollectionBase> klasy. Określony typ musi również ujawnić `Add` metodę, która spełnia następujące kryteria.  
  
-   `Add` Metody muszą być dostępne z zakresu, w którym jest wywoływana inicjatora kolekcji. `Add` Metoda nie ma być publiczne, jeśli używasz inicjatora kolekcji w przypadku których można uzyskać dostępu do metod niepublicznych kolekcji.  
  
-   `Add` Metoda musi być składową wystąpienia lub `Shared` elementów członkowskich klasy kolekcji lub metodą rozszerzenia.  
  
-   `Add` Metody musi istnieć który można dopasować, na podstawie reguł rozdzielczość przeciążenia, na typy, które są dostarczane w inicjatorze kolekcji.  
  
 Na przykład, poniższy kod pokazuje, jak utworzyć `List(Of Customer)` kolekcji przy użyciu inicjatora kolekcji. Gdy kod jest uruchamiany, każdy `Customer` obiekt jest przekazywany do `Add(Customer)` metoda listy ogólnej.  
  
 [!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]  
  
 Poniższy przykład kodu pokazuje równoważny kod, który nie korzysta z inicjatora kolekcji.  
  
 [!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]  
  
 Jeśli kolekcja zawiera `Add` metodę, która ma następujące parametry, które odpowiadają Konstruktor `Customer` obiektu, można zagnieżdżać wartości parametrów `Add` metodę w ramach inicjatory kolekcji, zgodnie z opisem w następnej sekcji. Jeśli kolekcja nie ma takich `Add` metody, możesz utworzyć je jako metodę rozszerzenia. Aby uzyskać przykład sposobu tworzenia `Add` metodę jako metodę rozszerzenia dla kolekcji, zobacz [jak: tworzenie, Dodaj rozszerzenie metody używane przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Na przykład sposobu tworzenia niestandardowej kolekcji, która może służyć za pomocą inicjatora kolekcji zobacz [porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).  
  
## <a name="nesting-collection-initializers"></a>Zagnieżdżanie inicjatory kolekcji  
 Można zagnieżdżać wartości w ramach inicjatora kolekcji, aby zidentyfikować określonego przeciążenia `Add` metody dla kolekcji, która jest tworzona. Wartość przekazywana do `Add` metody musi być rozdzielane przecinkami i ujęte w nawiasy klamrowe (`{}`), tak samo, jak w inicjatorze tablicy literału lub kolekcji.  
  
 Po utworzeniu kolekcji przy użyciu zagnieżdżonych wartości każdy element na liście wartości zagnieżdżonej jest przekazywany jako argument do `Add` metodę, która pasuje do typów elementów. Na przykład, poniższy kod tworzy <xref:System.Collections.Generic.Dictionary%602> w którym klucze są typu `Integer` i wartości są typu `String`. Każdy z listy zagnieżdżone wartości jest dopasowywany do <xref:System.Collections.Generic.Dictionary%602.Add%2A> metodę `Dictionary`.  
  
 [!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]  
  
 W poprzednim przykładzie kodu jest równoważny z następującym kodem.  
  
 [!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]  
  
 Tylko wartości zagnieżdżonej listy z pierwszy poziom zagnieżdżenia są wysyłane do `Add` metody dla typu kolekcji. Bardziej poziomów zagnieżdżenia, są traktowane jako literały tablicowe i list wartości zagnieżdżone nie są dopasowywane do `Add` metody żadnych kolekcji.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|---|---|  
|[Instrukcje: tworzenie i dodawanie metody rozszerzenia używanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Pokazuje, jak utworzyć metodę rozszerzenia o nazwie `Add` można wypełnić kolekcję z wartościami z inicjatora kolekcji.|  
|[Instrukcje: tworzenie kolekcji używanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Pokazuje, jak włączyć użycie inicjatora kolekcji, w tym `Add` metody w klasie kolekcji, która implementuje `IEnumerable`.|  
  
## <a name="see-also"></a>Zobacz także

- [Kolekcje](../../../../visual-basic/programming-guide/concepts/collections.md)  
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
- [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
- [Operator New](../../../../visual-basic/language-reference/operators/new-operator.md)  
- [Właściwości zaimplementowane automatycznie](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
- [Porady: inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)  
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
- [Instrukcje: tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
