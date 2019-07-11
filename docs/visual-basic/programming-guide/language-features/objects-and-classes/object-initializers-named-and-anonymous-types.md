---
title: 'Inicjatory obiektów: Typy nazwane i anonimowe (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 151c2f6cbb560d83ef0fcfef518bc50cec246ca2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783237"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Inicjatory obiektów: Typy nazwane i anonimowe (Visual Basic)
Inicjatory obiektów umożliwiają określenie właściwości dla obiektu złożonego za pomocą pojedynczego wyrażenia. One może służyć do tworzenia wystąpień nazwanych typów i typów anonimowych.  
  
## <a name="declarations"></a>Deklaracje  
 Deklaracje wystąpień nazwanych i anonimowych typów można sprawdzić niemal identyczne, ale ich skutki nie są takie same. Każda kategoria ma możliwości i ograniczenia dotyczące własne. W poniższym przykładzie pokazano wygodny sposób, aby zadeklarować i zainicjować wystąpienia klasy o nazwie `Customer`, za pomocą list inicjatora obiektu. Należy zauważyć, że określono nazwę klasy, po słowie kluczowym `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 Typ anonimowy nie ma użytecznych nazw. W związku z tym podczas tworzenia wystąpienia typu anonimowego nie może zawierać nazwy klasy.  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 Wymagania i wyniki dwie deklaracje nie są takie same. Aby uzyskać `namedCust`, `Customer` klasy, która ma `Name` właściwość musi już istnieć i deklaracja tworzy wystąpienie tej klasy. Aby uzyskać `anonymousCust`, kompilator określa nowej klasy, która ma jedną właściwość ciągu o nazwie `Name`i tworzy nowe wystąpienie klasy.  
  
## <a name="named-types"></a>Nazwane typy  
 Inicjatory obiektów zapewnia prostą metodę można wywołać konstruktora typu, a następnie ustaw wartości niektórych lub wszystkich właściwości w pojedynczej instrukcji. Kompilator wywołuje odpowiedniego konstruktora dla instrukcji: konstruktora bez parametrów, jeśli nie argumentów lub sparametryzowania konstruktora, jeśli jeden lub więcej argumentów są wysyłane. Po tym określone właściwości są inicjowane w kolejności, w jakiej są przedstawione na liście inicjatora.  
  
 Każdy inicjowania na liście inicjatora składa się z przypisania do składowej klasy wartości początkowej. Nazwy i typy danych elementów członkowskich są ustalane w momencie klasa jest zdefiniowana. W poniższych przykładach `Customer` klasy musi istnieć i musi mieć elementy członkowskie o nazwie `Name` i `City` który może akceptować wartości typu ciąg.  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 Alternatywnie możesz uzyskać ten sam wynik, używając następującego kodu:  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 Każdy z tych deklaracji jest równoważne z poniższego przykładu, który tworzy `Customer` obiektu za pomocą konstruktora bez parametrów, a następnie określa wartość początkową dla `Name` i `City` właściwości przy użyciu `With` Instrukcja.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 Jeśli `Customer` klasa zawiera sparametryzowane Konstruktor, który umożliwia wysyłanie wartość dla `Name`, można na przykład również zadeklarować i zainicjować `Customer` obiektu w następujący sposób:  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 Nie masz do zainicjowania wszystkich właściwości, co ilustruje poniższy kod.  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 Jednak listy inicjowania, nie może być pusta. Niezainicjowanych właściwości Zachowaj wartości domyślne.  
  
### <a name="type-inference-with-named-types"></a>Wnioskowanie o typie z typami nazwane  
 Możesz skrócić kodu do deklaracji `cust1` łącząc inicjatory obiektów i wnioskowanie o typie lokalnym. Dzięki temu można pominąć `As` klauzuli w deklaracji zmiennej. Typ danych zmiennej jest wnioskowany z typu obiektu, który jest tworzony przez przypisanie. W poniższym przykładzie typ `cust6` jest `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>Uwagi dotyczące typów o nazwie  
  
- Nie można zainicjować składowej klasy więcej niż jeden raz na liście inicjatora obiektu. Deklaracja `cust7` powoduje błąd.  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- Element członkowski może służyć do zainicjowania samego lub innego pola. Jeśli członek jest dostępny, przed jego został zainicjowany, tak jak w następującej deklaracji `cust8`, zostanie użyta wartość domyślna. Pamiętaj, że po przetworzeniu deklaracji, która korzysta z inicjatora obiektów, pierwszą rzeczą, która ma wywoływaną odpowiedniego konstruktora. Po tym są inicjowane poszczególnych pól na liście inicjatora. W poniższych przykładach, wartość domyślna `Name` przypisano do `cust8`, a wartością zainicjowane jest przypisana w `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     W poniższym przykładzie użyto parametryzowanym konstruktorem z `cust3` i `cust4` do zadeklarowania i zainicjowania `cust10` i `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- Inicjatory obiektów mogą być zagnieżdżone. W poniższym przykładzie `AddressClass` to klasa, która ma dwie właściwości `City` i `State`i `Customer` klasa ma `Address` właściwość, która jest wystąpieniem `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- Listy inicjowania, nie może być pusta.  
  
- Wystąpienie inicjowany nie może być typu Object.  
  
- Inicjowany elementów członkowskich klasy nie może być udostępniane elementy członkowskie, członków z prawami tylko do odczytu, stałe lub wywołania metody.  
  
- Inicjowany elementów członkowskich klasy nie może być indeksowane ani kwalifikowana. Poniższe przykłady zgłaszać błędy kompilatora:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Typy anonimowe  
 Typy anonimowe Użyj inicjalizatorów obiektów, aby tworzyć wystąpienia nowych typów, które nie zdefiniujesz jawnie i nazwy. Zamiast tego kompilator generuje typ zgodnie z właściwości, które należy wyznaczyć na liście inicjatora obiektu. Ponieważ nie określono nazwę typu, nazywa się *typu anonimowego*. Na przykład porównać następującą deklarację do przedstawionego wcześniej dla `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 Jedyną różnicą jest syntaktycznie, że nazwa nie zostanie określona po `New` dla typu danych. Co się stanie, jest jednak zupełnie inny. Kompilator określa nowym typem anonimowym ma dwie właściwości `Name` i `City`i tworzy jego wystąpienie z określonymi wartościami. Wnioskowanie o typie Określa typ `Name` i `City` w przykładzie jako ciągi.  
  
> [!CAUTION]
>  Nazwa typu anonimowego jest generowany przez kompilator i mogą się różnić od kompilacji do kompilacji. Kod powinien używać lub nie polegają na nazwie typu anonimowego.  
  
 Ponieważ nazwa typu nie jest dostępny, nie można użyć `As` klauzulę, aby zadeklarować `cust13`. Można wywnioskować jej typu. Bez korzystania z późnym wiązaniem ogranicza użycie typów anonimowych do zmiennych lokalnych.  
  
 Typy anonimowe umożliwiają krytycznych dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Aby uzyskać więcej informacji na temat używania typów anonimowych w zapytaniach zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) i [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Uwagi dotyczące typów anonimowych  
  
- Zazwyczaj wszystkich lub większości właściwości w deklaracji typu anonimowego będzie właściwości klucza, które są wskazane, wpisując słowa kluczowego `Key` przed nazwą właściwości.  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     Aby uzyskać więcej informacji na temat właściwości klucza, zobacz [klucz](../../../../visual-basic/language-reference/modifiers/key.md).  
  
- Jak o nazwie typów, list inicjatorów dla definicji typu anonimowego należy zadeklarować co najmniej jedną właściwość.  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- Gdy wystąpienie typu anonimowego jest zadeklarowany, kompilator generuje pasującego definicja typu anonimowego. Nazwy i typy danych właściwości są pobierane z deklaracji wystąpienia i są uwzględniane przez kompilator w definicji. Właściwości są nie o nazwie i z wyprzedzeniem, jaki byłyby dla typu nazwanego. Typy są wnioskowane. Typy danych właściwości nie można określić za pomocą `As` klauzuli.  
  
- Typy anonimowe można także udostępnić nazwy i wartości ich właściwości w inny sposób. Właściwości typu anonimowego może na przykład nazwę i wartość zmiennej, lub nazwę i wartość właściwości do innego obiektu.  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     Aby uzyskać więcej informacji na temat opcji do definiowania właściwości typów anonimowych, zobacz [jak: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Instrukcje: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [Instrukcje: Deklarowanie obiektu za pomocą inicjatora obiektów](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
