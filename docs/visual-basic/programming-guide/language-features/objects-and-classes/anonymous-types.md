---
title: Typy anonimowe (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 451fe45c9b5efbeb64b1066d6ba8e5f9b27300c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-types-visual-basic"></a>Typy anonimowe (Visual Basic)
Visual Basic obsługuje typy anonimowe, które umożliwiają tworzenie obiektów bez pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma używać nazwy, bezpośrednio dziedziczy <xref:System.Object>i zawiera właściwości określonej w odwołaniu do obiektu. Ponieważ nie określono nazwę typu danych, jest ona określana jako *typu anonimowego*.  
  
 W poniższym przykładzie deklaruje i tworzy zmienną `product` jako wystąpienie typu anonimowego, który ma dwie właściwości `Name` i `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 A *zapytania wyrażenie* używa typy anonimowe połączenie kolumn danych wybranych przez zapytanie. Nie można zdefiniować typu wyniku z wyprzedzeniem, ponieważ nie można przewidzieć kolumny, które mogą wybrać określonego zapytania. Typy anonimowe umożliwiają Napisz zapytanie, które wybiera dowolną liczbę kolumn, w dowolnej kolejności. Kompilator tworzy typ danych odpowiadający określonej właściwości i określonej kolejności.  
  
 W poniższych przykładach `products` znajduje się lista obiektów produktu, z których każdy ma wiele właściwości. Zmienna `namePriceQuery` zawiera definicję zapytanie po jego wykonaniu zwraca kolekcję wystąpień typu anonimowego, który ma dwie właściwości `Name` i `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 Zmienna `nameQuantityQuery` zawiera definicję zapytanie po jego wykonaniu zwraca kolekcję wystąpień typu anonimowego, który ma dwie właściwości `Name` i `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 Aby uzyskać więcej informacji na temat kod, który został utworzony przez kompilator dla typu anonimowego, zobacz [definicja typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
>  Nazwa typu anonimowego jest kompilatora wygenerowany i może się różnić od kompilacji do kompilacji. Kod nie należy używać ani polegać na nazwę typu anonimowego, ponieważ może zmienić nazwy, gdy projekt jest ponownie kompilowana.  
  
## <a name="declaring-an-anonymous-type"></a>Deklarowanie typu anonimowego  
 Deklaracja typu anonimowego wystąpienia użyto listy inicjalizatora do określenia właściwości typu. Można określić tylko właściwości w deklaracji typu anonimowego, nie innych elementów klasy, takich jak metody lub zdarzenia. W poniższym przykładzie `product1` jest wystąpieniem typu anonimowego, który ma dwie właściwości: `Name` i `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 Jeżeli możesz określić właściwości jako właściwości klucza, może ich użyć, aby porównać dwa wystąpienia typu anonimowego pod kątem równości. Jednak nie można zmienić wartości właściwości klucza. Zobacz sekcję właściwości klucza w dalszej części tego tematu, aby uzyskać więcej informacji.  
  
 Należy zauważyć, że wystąpienie typu anonimowego deklarowanie przypomina deklarowanie wystąpienia nazwanego typu za pomocą inicjatora obiektów:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 Aby uzyskać więcej informacji na temat innych sposobów określić właściwości typu anonimowego, zobacz [porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza różnią się od niż właściwości klucza na kilka sposobów podstawowe:  
  
-   Tylko wartości właściwości klucza są porównywane w celu określenia, czy dwa wystąpienia są takie same.  
  
-   Wartości właściwości klucza są tylko do odczytu i nie można zmienić.  
  
-   Tylko wartości właściwości klucza są uwzględniane w algorytm wyznaczania wartości skrótu generowane przez kompilator kodu typu anonimowego.  
  
### <a name="equality"></a>Równość  
 Wystąpień typów anonimowych może wynosić tylko wtedy, gdy są one wystąpień tego samego typu anonimowego. Kompilator traktuje dwa wystąpienia jako wystąpień tego samego typu, jeśli są spełnione następujące warunki:  
  
-   Są one zadeklarowany w tym samym zestawie.  
  
-   Ich właściwości o takich samych nazwach takich samych typach wykrywany oraz są zadeklarowane w tej samej kolejności. Nazwa porównania nie jest rozróżniana.  
  
-   Te same właściwości w każdym zostały oznaczone jako właściwości klucza.  
  
-   Co najmniej jedna właściwość w każdej deklaracji jest właściwość klucza.  
  
 Wystąpienie typy anonimowe nie ma klucza właściwości jest równa tylko samej siebie.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 Dwa wystąpienia tego samego typu anonimowego są takie same, jeśli wartości ich właściwości klucza są takie same. Poniższe przykłady pokazują, jak został przetestowany równości.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### <a name="read-only-values"></a>Wartości tylko do odczytu  
 Nie można zmienić wartości właściwości klucza. Na przykład w `prod8` w poprzednim przykładzie `Name` i `Price` pola są `read-only`, ale `OnHand` można zmienić.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Typy anonimowe z wyrażenia zapytania  
 Wyrażenia zapytań nie zawsze wymagają utworzenia typy anonimowe. Jeśli to możliwe, używają istniejącego typu do przechowywania danych kolumny. Dzieje się tak, gdy kwerenda zwraca albo całego rekordy ze źródła danych lub tylko jedno pole z każdego rekordu. W poniższych przykładach kodu `customers` to zbiór obiektów `Customer` klasy. Klasa ma wiele właściwości, oraz może zawierać co najmniej jeden z nich, które znajdują się w wyniku kwerendy w dowolnej kolejności. W przykładach dwóch pierwszych nie typy anonimowe są wymagane, ponieważ zapytania wybierz elementy typów o nazwie:  
  
-   `custs1` zawiera kolekcję parametrów, ponieważ `cust.Name` jest ciągiem.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   `custs2` zawiera kolekcję `Customer` obiektów, ponieważ każdy element `customers` jest `Customer` obiektu, a cały element jest wybierany przez zapytanie.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 Jednak odpowiednie nazwane typy nie są zawsze dostępne. Możesz chcieć wybierz nazwy klientów i adresy jeden cel, identyfikatorów klientów i lokalizacje i nazwy klientów, adresy i kolejność historii dla innej. Typy anonimowe umożliwiają wybrać dowolną kombinację właściwości, w dowolnej kolejności bez pierwszy deklarowania nowego typu o nazwie do przechowywania wyniku. Zamiast tego kompilator tworzy typu anonimowego dla każdej kompilacji właściwości. Następujące zapytanie wybiera tylko przez klienta nazwa i numer identyfikacyjny z każdej `Customer` obiektu w `customers`. W związku z tym kompilator tworzy typu anonimowego, który zawiera tylko te dwie właściwości.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 Zarówno nazwy i typy danych właściwości typu anonimowego są pobierane z argumenty `Select`, `cust.Name` i `cust.ID`. Właściwości typu anonimowego, który jest tworzony przez zapytanie są zawsze właściwości klucza. Gdy `custs3` są wykonywane w następujących `For Each` pętla, wynik jest kolekcja wystąpień typu anonimowego z dwóch właściwości klucza, `Name` i `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 Elementy w kolekcji reprezentowany przez `custs3` są silnie typizowane i przeglądanie dostępnych właściwości i sprawdzić ich typy, można użyć funkcji IntelliSense.  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Podjęcie decyzji o użyciu typy anonimowe  
 Przed utworzeniem obiektu jako wystąpienia klasy anonimowy, należy wziąć pod uwagę czy, który jest najlepszym rozwiązaniem. Na przykład jeśli chcesz utworzyć tymczasowego obiektu zawiera powiązane dane, a użytkownik nie ma potrzeby dla innych pól i metod, które mogą zawierać pełnej klasy, typu anonimowego jest dobrym rozwiązaniem. Typy anonimowe są również wygodne inny zbiór właściwości dla każdej deklaracji, lub jeśli chcesz zmienić kolejność właściwości. Jednak jeśli projekt zawiera kilka obiektów, które mają takie same właściwości w ustalonej kolejności, można zadeklarować je łatwiej przy użyciu nazwanego typu z konstruktorem klas. Na przykład z odpowiedniego konstruktora, łatwiej jest zadeklarować kilka wystąpień `Product` klasy nie można zadeklarować kilka wystąpień typu anonimowego.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 Inną zaletą nazwanymi typami jest kompilator może przechwycić, przypadkowe błędne nazwę właściwości. W poprzednich przykładach `firstProd2`, `secondProd2`, i `thirdProd2` powinny być wystąpień tego samego typu anonimowego. Jednak jeśli przypadkowo zostały zadeklarować `thirdProd2` w jednym z następujących sposobów jego typ będzie inny niż `firstProd2` i `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 Co więcej są ograniczenia użycia anonimowych typów, które nie dotyczą wystąpień typów o nazwie. `firstProd2`, `secondProd2`, i `thirdProd2` wystąpień tego samego typu anonimowego. Jednak nazwa udostępnionego typu anonimowego jest niedostępna i nie może występować, gdy nazwa typu jest oczekiwany w kodzie. Na przykład typ anonimowy nie może służyć do definiowania podpis metody, aby zadeklarować innej zmiennej lub pola lub w dowolnym deklaracji typu. W związku z tym typy anonimowe nie są odpowiednie, jeśli masz udostępnianie informacji przez metody.  
  
## <a name="an-anonymous-type-definition"></a>Definicja typu anonimowego  
 W odpowiedzi na deklaracji wystąpienia typu anonimowego kompilator tworzy nową definicję klasy zawierające określonej właściwości.  
  
 Jeśli typ anonimowy zawiera co najmniej jedną właściwość klucza, definicji zastąpienia trzech członków dziedziczonych po elemencie <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, i <xref:System.Object.ToString%2A>. Utworzony kod testowanie równości i określanie, czy wartość skrótu kodu uwzględnia tylko właściwości klucza. Jeśli typ anonimowy nie zawiera żadnych właściwości klucza, tylko <xref:System.Object.ToString%2A> zostanie zastąpiona. Jawnie nazwane właściwości typu anonimowego nie powodują konflikt z tych metod wygenerowany. Oznacza to, że nie można użyć `.Equals`, `.GetHashCode`, lub `.ToString` nazwę właściwości.  
  
 Definicje typu anonimowego, które mają co najmniej jedną właściwość klucza również wdrożenie <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu, gdzie `T` to rodzaj typu anonimowego.  
  
 Aby uzyskać więcej informacji o kodzie utworzony przez kompilator i funkcjonalność przesłoniętych metod, zobacz [definicja typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Definicja typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)
