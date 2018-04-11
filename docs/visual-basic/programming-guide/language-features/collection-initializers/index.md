---
title: Inicjatory kolekcji (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ec0179df50df453d6058a4b910d17561394140d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="collection-initializers-visual-basic"></a>Inicjatory kolekcji (Visual Basic)
*Inicjatory kolekcji* Podaj skróconą składnię, która umożliwia tworzenie kolekcji i wypełnić ją początkowego zestawu wartości. Inicjatory kolekcji są przydatne podczas tworzenia kolekcji z zestawu znane wartości, na przykład listę opcji menu lub kategorii, początkowego zestawu wartości liczbowe, natomiast statyczną listę ciągów, takich jak nazwy dnia i miesiąca lub lokalizacje geograficzne, takie jak Lista stanów, który jest używany do sprawdzania poprawności.  
  
 Aby uzyskać więcej informacji o kolekcjach, zobacz [kolekcji](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).  
  
 Należy określić przy użyciu inicjatora kolekcji `From` — słowo kluczowe następuje nawiasy klamrowe (`{}`). Jest to podobne do składni literału array opisany w [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md). W poniższych przykładach pokazano różne sposoby użycia inicjatory kolekcji do tworzenia kolekcji.  
  
 [!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]  
  
> [!NOTE]
>  C# są także inicjatory kolekcji. Inicjatory kolekcji C# zapewniają te same funkcje co inicjatory kolekcji Visual Basic. Aby uzyskać więcej informacji na temat inicjatory kolekcji C#, zobacz [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="syntax"></a>Składnia  
 Inicjator kolekcji zawiera listę z wartościami rozdzielanymi przecinkami ujętych w nawiasy klamrowe (`{}`), poprzedzającą `From` — słowo kluczowe, jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]  
  
 Podczas tworzenia kolekcji, takie jak <xref:System.Collections.Generic.List%601> lub <xref:System.Collections.Generic.Dictionary%602>, należy podać typ kolekcji przed inicjatora kolekcji, jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]  
  
> [!NOTE]
>  Nie można łączyć zarówno inicjatora kolekcji, jak i inicjatora obiektów do zainicjowania tego samego obiektu kolekcji. Inicjatory obiektów służy do zainicjowania obiekty inicjatora kolekcji.  
  
## <a name="creating-a-collection-by-using-a-collection-intializer"></a>Tworzenie kolekcji za pomocą inicjatora kolekcji  
 Po utworzeniu kolekcji za pomocą inicjatora kolekcji każdej wartości, która jest dostarczana w inicjatora kolekcji jest przekazywany do odpowiedniego `Add` metody kolekcji. Na przykład w przypadku utworzenia <xref:System.Collections.Generic.List%601> za pomocą inicjatora kolekcji, każda wartość ciągu w inicjatora kolekcji jest przekazywana do <xref:System.Collections.Generic.List%601.Add%2A> metody. Jeśli chcesz utworzyć kolekcję przy użyciu inicjatora kolekcji, określony typ musi być typem prawidłowej kolekcji. Typy kolekcji prawidłowe przykłady klas implementujących <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub dziedziczyć <xref:System.Collections.CollectionBase> klasy. Określony typ musi również ujawniać `Add` metodę, która spełnia następujące kryteria.  
  
-   `Add` Metody muszą być dostępne z zakresu, w którym jest wywoływana inicjatora kolekcji. `Add` Metoda nie ma być publiczne, jeśli używasz inicjatora kolekcji w przypadku której można uzyskać dostęp do metody niepublicznej kolekcji.  
  
-   `Add` Metody musi być członkiem wystąpienia lub `Shared` elementu członkowskiego klasy kolekcji lub metody rozszerzenia.  
  
-   `Add` Musi istnieć metoda który można dopasować, na podstawie reguł rozpoznawanie przeciążenia, do typów, które są dostarczane w inicjatora kolekcji.  
  
 Na przykład następujący przykładowy kod przedstawia sposób tworzenia `List(Of Customer)` kolekcji za pomocą inicjatora kolekcji. Gdy jest on uruchamiany, każdy `Customer` obiekt jest przekazywany do `Add(Customer)` metody listy ogólnej.  
  
 [!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]  
  
 Poniższy przykład kodu pokazuje równoważne kod, który nie korzysta z inicjatora kolekcji.  
  
 [!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]  
  
 Jeśli kolekcja zawiera `Add` metodę, która ma parametry, które Konstruktor `Customer` obiektu, można zagnieżdżać wartości parametrów dla `Add` metodę inicjatory kolekcji, zgodnie z opisem w następnej sekcji. Jeśli kolekcja nie ma takich `Add` metody, możesz utworzyć je jako metodę rozszerzenie. Przykład sposobu tworzenia `Add` metody jako metodę rozszerzenie dla kolekcji, zobacz [porady: tworzenie dodać rozszerzenie metody używane przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Na przykład sposobu tworzenia niestandardowej kolekcji, która może być używany z inicjatora kolekcji, zobacz [porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).  
  
## <a name="nesting-collection-initializers"></a>Inicjatory kolekcji zagnieżdżenia  
 Można zagnieżdżać wartości w ramach inicjatora kolekcji, aby zidentyfikować określonego przeciążenia `Add` metody dla kolekcji, która jest tworzona. Wartości przekazanych do `Add` — metoda muszą być oddzielone przecinkami i ujęte w nawiasy klamrowe (`{}`), jak należy inicjatora tablicy literał lub kolekcji.  
  
 Po utworzeniu kolekcji przy użyciu wartości zagnieżdżonych każdego elementu listy zagnieżdżonej wartości jest przekazywany jako argument `Add` metodę, która odpowiada typów elementów. Na przykład poniższy przykładowy kod tworzy <xref:System.Collections.Generic.Dictionary%602> , w której klucze są typu `Integer` i wartości są typu `String`. Każdy z listy zagnieżdżonej wartości jest dopasowywany do <xref:System.Collections.Generic.Dictionary%602.Add%2A> metodę `Dictionary`.  
  
 [!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]  
  
 W poprzednim przykładzie kodu jest odpowiednikiem następującego kodu.  
  
 [!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]  
  
 Tylko wartości zagnieżdżone listy z pierwszy poziom zagnieżdżenia są wysyłane do `Add` metody dla typu kolekcji. Lepszy poziomów zagnieżdżenia są traktowane jako literały tablicy i listy zagnieżdżonej wartości nie są zgodne z żadną `Add` metody żadnej kolekcji.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|---|---|  
|[Porady: tworzenie Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Przedstawia sposób tworzenia metodę rozszerzenia o nazwie `Add` można wypełnić kolekcji wartościami z inicjatora kolekcji.|  
|[Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Pokazuje, jak włączyć korzystanie z inicjatora kolekcji, umieszczając w niej `Add` metodę w klasie kolekcji, który implementuje `IEnumerable`.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Inicjatory obiektów: Typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [New — Operator](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Właściwości zaimplementowane automatycznie](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Porady: inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Porady: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
