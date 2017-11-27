---
title: "Inicjatory obiektów: typy nazwane i anonimowe (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 349e4f7b4902eb18845fee7cb4d01b217849a4d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Inicjatory obiektów: typy nazwane i anonimowe (Visual Basic)
Inicjatory obiektów umożliwiają określenie właściwości dla obiekt złożony przy użyciu jedno wyrażenie. Mogą one służyć do tworzenia wystąpień typów o nazwie i typy anonimowe.  
  
## <a name="declarations"></a>Deklaracje  
 Deklaracje wystąpień typy nazwane i anonimowe można wyświetlać niemal identyczne, ale ich skutki nie są takie same. Każda kategoria ma możliwości i ograniczeń własnych. W poniższym przykładzie pokazano to wygodny sposób zadeklarować i Inicjowanie wystąpienia klasy o nazwie `Customer`, za pomocą listy inicjalizatora obiektu. Zwróć uwagę, że określono nazwę klasy, po słowie kluczowym `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 Typ anonimowy nie ma używać nazwy. W związku z tym podczas tworzenia wystąpienia typu anonimowego nie może zawierać nazwy klasy.  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 Wymagania i wyniki dwóch deklaracje nie są takie same. Aby uzyskać `namedCust`, `Customer` klasy, która ma `Name` właściwość musi istnieć i deklaracji tworzy wystąpienie tej klasy. Aby uzyskać `anonymousCust`, kompilator definiuje nowa klasa, która ma właściwość jednego ciągu o nazwie `Name`i tworzy nowe wystąpienie tej klasy.  
  
## <a name="named-types"></a>Nazwane typy  
 Inicjatory obiektów zapewniają prosty sposób można wywołać konstruktora z typem, a następnie ustaw wartości niektórych lub wszystkich właściwości w jednej instrukcji. Kompilator wywołuje odpowiedniego konstruktora dla instrukcji: Konstruktor domyślny, jeśli nie argumentów lub parametryzowanym konstruktorem, jeśli jeden lub więcej argumentów są wysyłane. Po wykonaniu tej określonej właściwości są inicjowane w kolejności, w którym mają być przedstawiane na liście inicjatora.  
  
 Każdy inicjowania na liście inicjatora składa się z przypisania początkowej wartości do elementu członkowskiego klasy. Nazwy i typy danych elementów członkowskich są ustalane w momencie klasa jest zdefiniowana. W poniższych przykładach `Customer` klasy musi istnieć i musi mieć elementy członkowskie o nazwie `Name` i `City` które przyjmują wartości ciągu.  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 Alternatywnie można uzyskać ten sam rezultat przy użyciu następującego kodu:  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 Każdy z tych deklaracji jest odpowiednikiem poniższy przykład tworzy `Customer` obiektu za pomocą konstruktora domyślnego, a następnie określa wartość początkową dla `Name` i `City` właściwości przy użyciu `With` instrukcji.  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 Jeśli `Customer` klasa zawiera sparametryzowane konstruktora, który umożliwia wysyłanie wartość w polu `Name`, można na przykład również deklarować i zainicjuj `Customer` obiektu w następujący sposób:  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 Nie masz zainicjować wszystkie właściwości, jak przedstawiono na poniższym kodem.  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 Jednak listy inicjowania, nie może być pusta. Właściwości niezainicjowanej Zachowaj wartości domyślne.  
  
### <a name="type-inference-with-named-types"></a>Wnioskowanie o typie z nazwanymi typami  
 W przypadku skrócenia kod dla deklaracji `cust1` łącząc inicjatory obiektów i wnioskowanie o typie lokalnym. Dzięki temu można pominąć `As` klauzuli w deklaracji zmiennej. Typ danych zmiennej jest wywnioskowany na podstawie typu obiektu, który jest tworzony przez przypisanie. W poniższym przykładzie typ `cust6` jest `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>Uwagi dotyczące typów o nazwie  
  
-   Element członkowski klasy nie można zainicjować więcej niż jeden raz na liście inicjatora obiektu. Deklaracja `cust7` powoduje błąd.  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   Element członkowski może służyć do zainicjowania samego lub innego pola. Jeśli element członkowski jest dostępny, zanim zostanie zainicjowana, tak jak w następującej deklaracji `cust8`, zostanie użyta wartość domyślna. Należy pamiętać, że podczas przetwarzania deklaracji, która korzysta z inicjatora obiektów, najpierw, która jest wywołaniu odpowiedniego konstruktora. Po wykonaniu tej są inicjowane poszczególnych pól na liście inicjatora. W poniższych przykładach, wartość domyślna dla `Name` jest przypisany do `cust8`, i wartość zainicjowane została przypisana w `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     W poniższym przykładzie użyto sparametryzowanym konstruktorze z `cust3` i `cust4` zadeklarować i zainicjować `cust10` i `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   Inicjatory obiektów mogą być zagnieżdżone. W poniższym przykładzie `AddressClass` jest klasa, która ma dwie właściwości `City` i `State`i `Customer` klasa ma `Address` właściwość, która jest wystąpieniem `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   Inicjowanie listy nie może być pusta.  
  
-   Zainicjowanie wystąpienie nie może być typu obiektu.  
  
-   Zainicjowanie elementów członkowskich klasy nie może być udostępniane elementy członkowskie, elementy członkowskie tylko do odczytu, stałe lub wywołania metody.  
  
-   Zainicjowanie elementów członkowskich klasy nie może być indeksowane ani kwalifikowana. Poniższe przykłady Zgłoś błędy kompilatora:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Typy anonimowe  
 Typy anonimowe umożliwia tworzenie wystąpień nowych typów, które nie zostaną jawnie zdefiniowane i nazwy inicjatory obiektów. Zamiast tego kompilator generuje typu zgodnie z właściwości, które można określić na liście inicjatora obiektu. Ponieważ nie określono nazwę typu, jest ona określana jako *typu anonimowego*. Na przykład porównać następujące oświadczenie do wcześniejszych jeden dla `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 Jedyną różnicą jest składnię, że nie określono nazwy po `New` dla typu danych. Co się stanie, jest jednak zupełnie różne. Kompilator definiuje nowy typ anonimowy, który ma dwie właściwości `Name` i `City`i tworzy wystąpienie z określonymi wartościami. Wnioskowanie o typie Określa typy `Name` i `City` w przykładzie jako ciągi.  
  
> [!CAUTION]
>  Nazwa typu anonimowego jest generowany przez kompilator i może się różnić od kompilacji do kompilacji. Kod nie należy używać ani polegać na nazwę typu anonimowego.  
  
 Ponieważ nazwa typu nie jest dostępny, nie można użyć `As` klauzuli, aby zadeklarować `cust13`. Można wywnioskować jej typu. Bez korzystania z późnym wiązaniem, ogranicza użycie typów anonimowych do zmiennych lokalnych.  
  
 Typy anonimowe obsługi krytycznych dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Aby uzyskać więcej informacji o używaniu typy anonimowe w zapytaniach, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) i [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Uwagi dotyczące typy anonimowe  
  
-   Zazwyczaj wszystkie lub większość z właściwości w deklaracji typu anonimowego jest właściwości klucza, które są wskazane, wpisując słowa kluczowego `Key` przed nazwą właściwości.  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     Aby uzyskać więcej informacji na temat właściwości klucza, zobacz [klucza](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   Tak samo, jak nazwy typów, listy inicjatorów dla definicji typu anonimowego muszą deklarować co najmniej jedną właściwość.  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   Wystąpienie typu anonimowego jest zadeklarowana, kompilator generuje pasującego definicja typu anonimowego. Nazwy i typy danych właściwości są pobierane z deklaracji wystąpienia, a znajdują się za pomocą kompilatora w definicji. Właściwości nie są o nazwie i określonych wcześniej, jakie byłyby dla nazwanego typu. Typy są wywnioskować. Typy danych właściwości nie można określić za pomocą `As` klauzuli.  
  
-   Typy anonimowe można także udostępnić nazwy i wartości właściwości w inny sposób. Na przykład właściwości typu anonimowego może zająć zarówno nazwę i wartość zmiennej, lub nazwy i wartości właściwości innego obiektu.  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     Aby uzyskać więcej informacji na temat opcji do definiowania właściwości typów anonimowych, zobacz [porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Porady: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Klucz](../../../../visual-basic/language-reference/modifiers/key.md)  
 [Porady: deklarowanie obiektu za pomocą inicjatora obiektów](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
