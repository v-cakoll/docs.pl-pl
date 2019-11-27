---
title: Typy anonimowe
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 064c43274069be3951f816eaafafac0bbece7651
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347159"
---
# <a name="anonymous-types-visual-basic"></a>Typy anonimowe (Visual Basic)
Visual Basic obsługuje typy anonimowe, które umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma użytecznych nazw, dziedziczy bezpośrednio z <xref:System.Object>i zawiera właściwości określone w deklaracji obiektu. Ponieważ nazwa typu danych nie jest określona, jest określana jako *Typ anonimowy*.  
  
 Poniższy przykład deklaruje i tworzy zmienną `product` jako wystąpienie typu anonimowego, który ma dwie właściwości, `Name` i `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 *Wyrażenie zapytania* używa typów anonimowych do łączenia kolumn danych wybranych przez zapytanie. Nie można zdefiniować typu wyniku z wyprzedzeniem, ponieważ nie można przewidzieć kolumn, które mogą zostać wybrane dla konkretnego zapytania. Typy anonimowe umożliwiają pisanie zapytania, które wybiera dowolną liczbę kolumn w dowolnej kolejności. Kompilator tworzy typ danych, który jest zgodny z określonymi właściwościami i określoną kolejnością.  
  
 W poniższych przykładach `products` jest lista obiektów produktu, z których każdy ma wiele właściwości. Zmienna `namePriceQuery` przechowuje definicję zapytania, które po jego wykonaniu zwraca kolekcję wystąpień typu anonimowego, który ma dwie właściwości, `Name` i `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 Zmienna `nameQuantityQuery` przechowuje definicję zapytania, które po jego wykonaniu zwraca kolekcję wystąpień typu anonimowego, który ma dwie właściwości, `Name` i `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 Aby uzyskać więcej informacji na temat kodu utworzonego przez kompilator dla typu anonimowego, zobacz [definicja typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
> Nazwa typu anonimowego jest generowana przez kompilator i może się różnić od kompilacji do kompilacji. Kod nie powinien używać nazwy typu anonimowego ani polegać na niej, ponieważ nazwa może ulec zmianie podczas ponownej kompilacji projektu.  
  
## <a name="declaring-an-anonymous-type"></a>Deklarowanie typu anonimowego  
 Deklaracja wystąpienia typu anonimowego używa listy inicjatorów do określenia właściwości typu. Podczas deklarowania typu anonimowego można określić tylko właściwości, a nie inne elementy klasy, takie jak metody lub zdarzenia. W poniższym przykładzie `product1` jest wystąpieniem typu anonimowego, który ma dwie właściwości: `Name` i `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 Jeśli wyznaczysz właściwości jako właściwości klucza, możesz użyć ich do porównania dwóch anonimowych wystąpień typu dla równości. Nie można jednak zmienić wartości właściwości klucza. Aby uzyskać więcej informacji, zobacz sekcję właściwości klucza w dalszej części tego tematu.  
  
 Należy zauważyć, że deklarowanie wystąpienia typu anonimowego jest podobne do deklarującego wystąpienia nazwanego typu za pomocą inicjatora obiektów:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 Aby uzyskać więcej informacji na temat innych metod określania właściwości typu anonimowego, zobacz [How to: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza różnią się od właściwości niebędących kluczami na kilka podstawowych sposobów:  
  
- Tylko wartości właściwości klucza są porównywane w celu określenia, czy dwa wystąpienia są równe.  
  
- Wartości właściwości klucza są tylko do odczytu i nie można ich zmienić.  
  
- Tylko wartości właściwości klucza są zawarte w algorytmie kodu skrótu wygenerowanego przez kompilator dla typu anonimowego.  
  
### <a name="equality"></a>Równości  
 Wystąpienia typów anonimowych mogą być równe tylko wtedy, gdy są wystąpieniami tego samego typu anonimowego. Kompilator traktuje dwa wystąpienia jako wystąpienia tego samego typu, jeśli spełniają następujące warunki:  
  
- Są one deklarowane w tym samym zestawie.  
  
- Ich właściwości mają takie same nazwy, te same wywnioskowane typy i są deklarowane w tej samej kolejności. W porównaniach nazw nie jest rozróżniana wielkość liter.  
  
- Te same właściwości w każdej z nich są oznaczane jako właściwości klucza.  
  
- Co najmniej jedna właściwość w każdej deklaracji jest właściwością klucza.  
  
 Wystąpienie typów anonimowych, które nie ma właściwości klucza, jest równe tylko sobie.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 Dwa wystąpienia tego samego typu anonimowego są równe, jeśli wartości właściwości klucza są równe. W poniższych przykładach pokazano, jak równość jest testowana.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>Wartości tylko do odczytu  
 Nie można zmienić wartości właściwości klucza. Na przykład w `prod8` w poprzednim przykładzie pola `Name` i `Price` są `read-only`, ale `OnHand` można zmienić.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Typy anonimowe z wyrażeń zapytania  
 Wyrażenia zapytań nie zawsze wymagają tworzenia typów anonimowych. Jeśli to możliwe, używa istniejącego typu do przechowywania danych kolumny. Dzieje się tak, gdy zapytanie zwraca wszystkie rekordy ze źródła danych lub tylko jedno pole z każdego rekordu. W poniższych przykładach kodu `customers` jest kolekcją obiektów klasy `Customer`. Klasa ma wiele właściwości i można w dowolnej kolejności uwzględnić jeden lub więcej z nich w wyniku zapytania. W pierwszych dwóch przykładach nie są wymagane żadne typy anonimowe, ponieważ zapytania wybierają elementy nazwanych typów:  
  
- `custs1` zawiera kolekcję ciągów, ponieważ `cust.Name` jest ciągiem.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- `custs2` zawiera kolekcję obiektów `Customer`, ponieważ każdy element `customers` jest obiektem `Customer`, a cały element jest wybierany przez zapytanie.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 Jednak odpowiednie nazwane typy nie są zawsze dostępne. Możesz chcieć wybrać nazwy i adresy klientów w jednym celu, numery IDENTYFIKACYJNe klienta i lokalizacje dla innych, nazwy klientów, adresy i historie uporządkowane. Typy anonimowe umożliwiają wybranie dowolnej kombinacji właściwości w dowolnej kolejności, bez uprzedniego deklarowania nowego typu nazwanego do przechowywania wyniku. Zamiast tego kompilator tworzy typ anonimowy dla każdej kompilacji właściwości. Poniższe zapytanie wybiera tylko nazwę klienta i numer IDENTYFIKACYJNy z każdego obiektu `Customer` w `customers`. W związku z tym kompilator tworzy typ anonimowy, który zawiera tylko te dwie właściwości.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 Zarówno nazwy, jak i typy danych właściwości w typie anonimowym są pobierane z argumentów do `Select`, `cust.Name` i `cust.ID`. Właściwości typu anonimowego, który jest tworzony przez zapytanie, są zawsze właściwościami klucza. Gdy `custs3` jest wykonywane w następującej pętli `For Each`, wynik jest kolekcją wystąpień typu anonimowego z dwoma kluczowymi właściwościami, `Name` i `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 Elementy w kolekcji reprezentowane przez `custs3` są silnie wpisane i można używać funkcji IntelliSense do nawigowania po dostępnych właściwościach i weryfikowania ich typów.  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Decydowanie o tym, czy mają być używane typy anonimowe  
 Przed utworzeniem obiektu jako wystąpieniem klasy anonimowej, należy rozważyć, czy jest to najlepsza opcja. Na przykład, jeśli chcesz utworzyć tymczasowy obiekt, aby zawierał powiązane dane, i nie ma potrzeby dla innych pól i metod, które może zawierać kompletna Klasa, typ anonimowy jest dobrym rozwiązaniem. Typy anonimowe są również wygodne, jeśli chcesz wybrać różne właściwości dla każdej deklaracji, lub jeśli chcesz zmienić kolejność właściwości. Jeśli jednak projekt zawiera kilka obiektów, które mają te same właściwości, w ustalonej kolejności można zadeklarować je łatwiej przy użyciu nazwanego typu z konstruktorem klasy. Na przykład, z odpowiednim konstruktorem, łatwiej jest zadeklarować kilka wystąpień klasy `Product` niż w celu deklarowania kilku wystąpień typu anonimowego.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 Inną zaletą typów nazwanych jest to, że kompilator może przechwytywać przypadkowe błędne wpisywanie nazwy właściwości. W poprzednich przykładach `firstProd2`, `secondProd2`i `thirdProd2` mają być wystąpieniami tego samego typu anonimowego. Jeśli jednak przypadkowo zadeklarujesz `thirdProd2` w jeden z następujących sposobów, jego typ będzie inny niż `firstProd2` i `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 Co ważniejsze, istnieją ograniczenia dotyczące użycia anonimowych typów, które nie mają zastosowania do wystąpień nazwanych typów. `firstProd2`, `secondProd2`i `thirdProd2` są wystąpieniami tego samego typu anonimowego. Jednak nazwa udostępnionego typu anonimowego jest niedostępna i nie może się pojawić w przypadku, gdy w kodzie nie oczekiwano nazwy typu. Na przykład typu anonimowego nie można użyć do zdefiniowania podpisu metody, do deklarowania innej zmiennej lub pola lub deklaracji typu. W związku z tym typy anonimowe nie są odpowiednie w przypadku konieczności udostępniania informacji między metodami.  
  
## <a name="an-anonymous-type-definition"></a>Definicja typu anonimowego  
 W odpowiedzi na deklarację wystąpienia typu anonimowego kompilator tworzy nową definicję klasy, która zawiera określone właściwości.  
  
 Jeśli typ anonimowy zawiera co najmniej jedną właściwość klucza, definicja przesłania trzy składowe dziedziczone z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>i <xref:System.Object.ToString%2A>. Kod przeznaczony do testowania równości i określania wartości kodu skrótu uwzględnia tylko właściwości klucza. Jeśli typ anonimowy nie zawiera właściwości klucza, tylko <xref:System.Object.ToString%2A> jest zastępowany. Właściwości jawnie nazwane typu anonimowego nie mogą powodować konfliktu z tymi wygenerowanymi metodami. Oznacza to, że nie można użyć `.Equals`, `.GetHashCode`lub `.ToString` do nazwy właściwości.  
  
 Definicje typu anonimowego, które mają co najmniej jedną właściwość klucza, również implementują interfejs <xref:System.IEquatable%601?displayProperty=nameWithType>, gdzie `T` jest typem typu anonimowego.  
  
 Aby uzyskać więcej informacji na temat kodu utworzonego przez kompilator i funkcji przesłoniętych metod, zobacz [definicja typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Zobacz także

- [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Definicja typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
