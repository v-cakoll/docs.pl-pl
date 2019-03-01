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
ms.openlocfilehash: 5ff3b12e85b9ab7fb8341bb8665a057165e78816
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968028"
---
# <a name="anonymous-types-visual-basic"></a>Typy anonimowe (Visual Basic)
Visual Basic obsługuje typy anonimowe, które pozwalają na tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma użytecznych nazw, dziedziczy bezpośrednio z <xref:System.Object>i zawiera właściwości określone w odwołaniu do obiektu. Ponieważ nazwa typu danych nie jest określona, nazywa się *typu anonimowego*.  
  
 Poniższy przykład deklaruje i tworzy zmienną `product` jako wystąpienie typu anonimowego, który ma dwie właściwości `Name` i `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 A *wyrażeniu zapytania* używa typów anonimowych połączyć kolumny danych, wybrana przez zapytanie. Nie można zdefiniować typ wyniku z wyprzedzeniem, ponieważ nie można przewidzieć kolumn, które może wybrać określone zapytanie. Typy anonimowe umożliwiają pisanie zapytań, który wybiera dowolną liczbę kolumn, w dowolnej kolejności. Kompilator tworzy typ danych, który pasuje do określonych właściwości i w określonej kolejności.  
  
 W poniższych przykładach `products` znajduje się lista obiektów produktu, z których każdy zawiera wiele właściwości. Zmienna `namePriceQuery` zawiera definicję zapytanie, które, gdy jest wykonywany, zwraca kolekcję wystąpień typ anonimowy, który ma dwie właściwości `Name` i `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 Zmienna `nameQuantityQuery` zawiera definicję zapytanie, które, gdy jest wykonywany, zwraca kolekcję wystąpień typ anonimowy, który ma dwie właściwości `Name` i `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 Aby uzyskać więcej informacji na temat kod utworzony przez kompilator dla typu anonimowego, zobacz [definicja typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
>  Nazwa typu anonimowego jest kompilatora generowane i mogą się różnić od kompilacji do kompilacji. Kod powinien używać lub nie polegają na nazwę typu anonimowego, ponieważ nazwa mogą ulec zmianie, gdy projekt jest kompilowany ponownie.  
  
## <a name="declaring-an-anonymous-type"></a>Deklarowanie typu anonimowego  
 Deklaracja typu anonimowego wystąpienia używa listy inicjalizatora w celu określenia właściwości typu. W przypadku deklarowania typu anonimowego, nie innych klas elementów takich jak metody lub zdarzenia, można określić tylko właściwości. W poniższym przykładzie `product1` jest wystąpieniem typu anonimowego, który ma dwie właściwości: `Name` i `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 Po wyznaczeniu właściwości jako właściwości klucza, można użyć ich do porównywania dwóch wystąpień typu anonimowego pod kątem równości. Jednak nie można zmienić wartości właściwości klucza. Sekcja właściwości klucza w dalszej części tego tematu, aby uzyskać więcej informacji.  
  
 Należy zauważyć, że deklarowanie wystąpienie typu anonimowego jest podobne do deklarowania wystąpienia typu o nazwie za pomocą inicjatora obiektów:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 Aby uzyskać więcej informacji na temat innych sposobów, aby określić właściwości typu anonimowego, zobacz [jak: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza różnią się od niekluczowych właściwości na kilka sposobów podstawowe:  
  
-   Tylko wartości właściwości klucza są porównywane w celu ustalenia, czy dwa wystąpienia są takie same.  
  
-   Wartości właściwości klucza są przeznaczone tylko do odczytu i nie można jej zmienić.  
  
-   Tylko wartości kluczy właściwości znajdują się w algorytmie kod generowany przez kompilator wyznaczania wartości skrótu dla typu anonimowego.  
  
### <a name="equality"></a>Równości  
 Wystąpień typów anonimowych może być taki sam, tylko wtedy, gdy są one wystąpień tego samego typu anonimowego. Kompilator traktuje dwa wystąpienia jako wystąpień tego samego typu, jeśli są spełnione następujące warunki:  
  
-   Są one zadeklarowane w tym samym zestawie.  
  
-   Ich właściwości takich samych nazwach takich samych typach wykrywany i są deklarowane w tej samej kolejności. Nazwa porównania nie jest rozróżniana wielkość liter.  
  
-   Te same właściwości w każdym są oznaczone jako właściwości klucza.  
  
-   Co najmniej jedna właściwość w każdej deklaracji jest właściwość klucza.  
  
 Wystąpienie anonimowe typy, które nie ma klucza właściwości jest taki sam, tylko do samego siebie.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 Dwa wystąpienia tego samego typu anonimowego są równe, jeśli wartości ich właściwości klucza są takie same. Poniższe przykłady ilustrują, jak równości jest testowana.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>Wartości tylko do odczytu  
 Nie można zmienić wartości właściwości klucza. Na przykład w `prod8` w poprzednim przykładzie `Name` i `Price` pola są `read-only`, ale `OnHand` można zmienić.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Anonimowe typy w wyrażeniach zapytań  
 Wyrażenia zapytań nie zawsze należy wymagać utworzenia typy anonimowe. Jeśli to możliwe, używają istniejącego typu do przechowywania danych kolumny. Dzieje się tak, gdy kwerenda zwraca albo całego rekordy ze źródła danych lub tylko jedno pole z każdego rekordu. W poniższych przykładach kodu `customers` to zbiór obiektów `Customer` klasy. Klasa ma wiele właściwości i może zawierać co najmniej jeden z nich, które znajdują się w wyniku zapytania w dowolnej kolejności. W pierwszych dwóch przykładach nie typy anonimowe są wymagane, ponieważ zapytania wybierz elementy nazwane typy:  
  
-   `custs1` zawiera kolekcję parametrów, ponieważ `cust.Name` jest ciągiem.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
-   `custs2` zawiera kolekcję `Customer` obiektów, ponieważ każdy element obiektu `customers` jest `Customer` obiektu, a cały element jest wybrany przez zapytanie.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 Jednak odpowiednie nazwane typy nie są zawsze dostępne. Możesz chcieć wybierz nazwy klientów i adresy jeden cel, numery identyfikatorów klientów i lokalizacji do innej i nazw klientów, adresów i historie zamówienia dla innego. Typy anonimowe umożliwiają wybrać dowolną kombinację właściwości, w dowolnej kolejności bez pierwszy deklarowania nowego typu nazwanego na potrzeby przechowywania wyniku. Zamiast tego kompilator tworzy dla każdej kompilacji właściwości typu anonimowego. Następujące zapytanie wybiera tylko przez klienta nazwa i numer identyfikacyjny każdego z nich `Customer` obiektu `customers`. W związku z tym kompilator tworzy typ anonimowy, który zawiera tylko te dwie właściwości.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 Nazwy i typy danych właściwości typu anonimowego są pobierane z argumentów `Select`, `cust.Name` i `cust.ID`. Właściwości w typ anonimowy, który jest tworzony przez zapytanie są zawsze właściwości klucza. Gdy `custs3` jest wykonywany w następującym `For Each` pętli, wynik jest kolekcją wystąpień typu anonimowego z dwóch właściwości klucza, `Name` i `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 Elementy w kolekcji, reprezentowane przez `custs3` są silnie typizowane i można użyć funkcji IntelliSense, nawigowanie po dostępnych właściwości i sprawdź ich typy.  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Podjęcie decyzji o użyciu typy anonimowe  
 Przed przystąpieniem do tworzenia obiektów jako wystąpienia klasy anonimowe, należy wziąć pod uwagę niezależnie czy dotyczyć to najlepsze rozwiązanie. Na przykład jeśli chcesz utworzyć obiekt tymczasowy powiązanych danych, a użytkownik nie ma potrzeby dla innych pól i metod, które mogą zawierać pełnej klasy, typu anonimowego jest doskonałym rozwiązaniem. Typy anonimowe są również wygodne, jeśli ma inny zestaw właściwości dla każdej deklaracji lub jeśli chcesz zmienić kolejność właściwości. Jednakże jeśli projekt zawiera kilka obiektów, które mają te same właściwości w ustalonej kolejności, można zadeklarować je łatwiej przy użyciu typu nazwanego konstruktora klasy. Na przykład za pomocą odpowiedniego konstruktora, łatwiej jest zadeklarować kilka wystąpień `Product` klasy nie można zadeklarować kilka wystąpień typu anonimowego.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 Inną zaletą nazwane typy to, że kompilator może przechwycić przypadkowym błędne nazwę właściwości. W poprzednich przykładach `firstProd2`, `secondProd2`, i `thirdProd2` mają być wystąpieniami tego samego typu anonimowego. Jednak jeśli przypadkowo zadeklarować `thirdProd2` w jednym z następujących sposobów będzie inny niż jego typ `firstProd2` i `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 Co ważniejsze ma ograniczeń dotyczących używania typy anonimowe, które nie dotyczą wystąpień nazwanych typów. `firstProd2`, `secondProd2`, i `thirdProd2` wystąpień tego samego typu anonimowego. Jednak nazwę udostępnionego typu anonimowego jest niedostępna i nie może występować, gdzie nazwa typu, który jest oczekiwany w kodzie. Na przykład typ anonimowy nie może służyć do definiowania podpis metody, aby zadeklarować innej zmiennej lub pola lub w dowolnym deklaracji typu. W rezultacie typy anonimowe nie są odpowiednie w przypadku udostępniania informacji o różnych metod.  
  
## <a name="an-anonymous-type-definition"></a>Definicja typu anonimowego  
 W odpowiedzi na deklarację wystąpienia typu anonimowego kompilator utworzy nową definicję klasy, która zawiera określone właściwości.  
  
 Jeśli typ anonimowy zawiera co najmniej jedną właściwość klucza, definicja zastępuje trzech członków dziedziczonych po elemencie <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, i <xref:System.Object.ToString%2A>. Kod generowany testowanie równości i określania, że wartość Kod skrótu uwzględnia tylko właściwości klucza. Jeśli typu anonimowego nie zawiera żadnych właściwości klucza, tylko <xref:System.Object.ToString%2A> zostanie zastąpiona. Jawnie nazwane właściwości typu anonimowego nie może powodować konflikt z tych metod wygenerowany. Oznacza to, że nie można użyć `.Equals`, `.GetHashCode`, lub `.ToString` nazwę właściwości.  
  
 Definicji typu anonimowego, które mają co najmniej jeden klucz właściwości również implementują <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu, gdzie `T` to rodzaj typu anonimowego.  
  
 Aby uzyskać więcej informacji na temat kod utworzony przez kompilator i funkcje zastąpionych metod zobacz [definicja typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Zobacz także
- [Inicjatory obiektów: Typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Instrukcje: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Definicja typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
