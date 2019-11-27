---
title: 'Inicjatory obiektów: typy nazwane i anonimowe'
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
ms.openlocfilehash: 20e46d7ecc206abb28240075d9ec5f764ab78d01
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346137"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Inicjatory obiektów: typy nazwane i anonimowe (Visual Basic)
Inicjatory obiektów umożliwiają określanie właściwości dla obiektu złożonego za pomocą jednego wyrażenia. Mogą służyć do tworzenia wystąpień nazwanych typów i typów anonimowych.  
  
## <a name="declarations"></a>Deklaracje  
 Deklaracje wystąpień typów nazwanych i anonimowych mogą wyglądać niemal identycznie, ale ich efekty nie są takie same. Każda kategoria ma możliwości i ograniczenia własnych. Poniższy przykład przedstawia wygodny sposób deklarowania i inicjowania wystąpienia nazwanej klasy, `Customer`przy użyciu listy inicjatorów obiektów. Zauważ, że nazwa klasy jest określona po słowie kluczowym `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 Typ anonimowy nie ma użytecznych nazw. W związku z tym wystąpienie typu anonimowego nie może zawierać nazwy klasy.  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 Wymagania i wyniki dwóch deklaracji nie są takie same. W przypadku `namedCust`Klasa `Customer`, która ma właściwość `Name` musi już istnieć, a deklaracja tworzy wystąpienie tej klasy. W przypadku `anonymousCust`kompilator definiuje nową klasę, która ma jedną właściwość, ciąg o nazwie `Name`i tworzy nowe wystąpienie tej klasy.  
  
## <a name="named-types"></a>Nazwane typy  
 Inicjatory obiektów zapewniają prosty sposób wywoływania konstruktora typu, a następnie ustawiania wartości niektórych lub wszystkich właściwości w pojedynczej instrukcji. Kompilator wywołuje odpowiedni Konstruktor dla instrukcji: bezparametrowego konstruktora, jeśli nie są wyświetlane żadne argumenty lub jeśli zostanie wysłany jeden lub więcej argumentów. Po tym określone właściwości są inicjowane w kolejności, w jakiej są wyświetlane na liście inicjatorów.  
  
 Każda Inicjalizacja na liście inicjatora składa się z przypisania wartości początkowej do składowej klasy. Nazwy i typy danych elementów członkowskich są określane, gdy Klasa jest zdefiniowana. W poniższych przykładach Klasa `Customer` musi istnieć i musi mieć elementy członkowskie o nazwach `Name` i `City`, które mogą akceptować wartości ciągu.  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 Alternatywnie można uzyskać ten sam wynik przy użyciu następującego kodu:  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 Każda z tych deklaracji jest równoważna z poniższym przykładem, który tworzy obiekt `Customer` przy użyciu konstruktora bez parametrów, a następnie określa początkowe wartości właściwości `Name` i `City` przy użyciu instrukcji `With`.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 Jeśli Klasa `Customer` zawiera sparametryzowany Konstruktor, który umożliwia wysyłanie w wartości dla `Name`, można również zadeklarować i zainicjować obiekt `Customer` w następujący sposób:  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 Nie trzeba inicjować wszystkich właściwości, jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 Jednak lista inicjalizacji nie może być pusta. Niezainicjowane właściwości zachowują wartości domyślne.  
  
### <a name="type-inference-with-named-types"></a>Wnioskowanie o typie z nazwanymi typami  
 Można skrócić kod dla deklaracji `cust1` przez połączenie inicjatorów obiektów i wnioskowania o typie lokalnym. Pozwala to pominąć klauzulę `As` w deklaracji zmiennej. Typ danych zmiennej jest wywnioskowany na podstawie typu obiektu, który jest tworzony przez przypisanie. W poniższym przykładzie typ `cust6` jest `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>Uwagi dotyczące nazwanych typów  
  
- Nie można zainicjować składowej klasy więcej niż jeden raz na liście inicjatora obiektów. Deklaracja `cust7` powoduje błąd.  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- Elementu członkowskiego można użyć do zainicjowania samego lub innego pola. Jeśli dostęp do elementu członkowskiego jest możliwy przed jego zainicjowaniem, jak w następującej deklaracji `cust8`, zostanie użyta wartość domyślna. Należy pamiętać, że gdy przetwarzana jest deklaracja, która używa inicjatora obiektów, pierwszym krokiem jest to, że odpowiedni Konstruktor jest wywoływany. Następnie poszczególne pola na liście inicjatorów są inicjowane. W poniższych przykładach wartość domyślna dla `Name` jest przypisana do `cust8`, a zainicjowana wartość jest przypisana w `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     W poniższym przykładzie używa konstruktora sparametryzowanego z `cust3` i `cust4` do deklarowania i zainicjowania `cust10` i `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- Inicjatory obiektów mogą być zagnieżdżane. W poniższym przykładzie `AddressClass` jest klasą, która ma dwie właściwości, `City` i `State`, a Klasa `Customer` ma właściwość `Address`, która jest wystąpieniem `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- Lista inicjalizacji nie może być pusta.  
  
- Inicjowane wystąpienie nie może być typu Object.  
  
- Inicjowane składowe klas nie mogą być udostępnionymi elementami członkowskimi, elementami członkowskimi tylko do odczytu, stałymi lub wywołaniami metod.  
  
- Inicjowane składowe klas nie mogą być indeksowane ani kwalifikowane. Następujące przykłady powodują wystąpienie błędów kompilatora:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Typy anonimowe  
 Typy anonimowe używają inicjatorów obiektów do tworzenia wystąpień nowych typów, które nie są jawnie definiowane i nazwy. Zamiast tego kompilator generuje typ zgodnie z właściwościami wyznaczonymi na liście inicjatora obiektów. Ponieważ nazwa typu nie jest określona, jest określana jako *Typ anonimowy*. Na przykład Porównaj następującą deklarację z wcześniejszą wersją dla `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 Jedyną różnicą składnią jest to, że po `New` dla typu danych nie określono nazwy. Zdarza się jednak, że jest to zupełnie inne. Kompilator definiuje nowy typ anonimowy, który ma dwie właściwości, `Name` i `City`, i tworzy jego wystąpienie z określonymi wartościami. Wnioskowanie o typie określa typy `Name` i `City` w przykładach, które mają być ciągami.  
  
> [!CAUTION]
> Nazwa typu anonimowego jest generowana przez kompilator i może się różnić w zależności od kompilacji do kompilacji. Kod nie powinien używać nazwy typu anonimowego ani nie polega na nim.  
  
 Ponieważ nazwa typu jest niedostępna, nie można zadeklarować `cust13`za pomocą klauzuli `As`. Jego typ musi być wywnioskowany. Bez używania późnego wiązania, to ogranicza użycie typów anonimowych do zmiennych lokalnych.  
  
 Typy anonimowe zapewniają krytyczną obsługę zapytań [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Aby uzyskać więcej informacji o korzystaniu z typów anonimowych w zapytaniach, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) i [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Uwagi dotyczące typów anonimowych  
  
- Zwykle wszystkie lub większość właściwości w deklaracji typu anonimowego będą właściwościami klucza, które są wskazywane przez wpisanie słowa kluczowego `Key` przed nazwą właściwości.  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     Aby uzyskać więcej informacji na temat właściwości klucza, zobacz [Key](../../../../visual-basic/language-reference/modifiers/key.md).  
  
- Podobnie jak nazwane typy, listy inicjatorów dla definicji typu anonimowego muszą deklarować co najmniej jedną właściwość.  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- Gdy zadeklarowane jest wystąpienie typu anonimowego, kompilator generuje zgodną definicję typu anonimowego. Nazwy i typy danych właściwości są pobierane z deklaracji wystąpienia i są uwzględniane przez kompilator w definicji. Właściwości nie są nazwane i zdefiniowane z góry, ponieważ byłyby dla nazwanego typu. Ich typy są wywnioskowane. Nie można określić typów danych właściwości przy użyciu klauzuli `As`.  
  
- Typy anonimowe mogą również określać nazwy i wartości swoich właściwości na kilka innych sposobów. Na przykład właściwość typu anonimowego może przyjmować zarówno nazwę, jak i wartość zmiennej, lub nazwę i wartość właściwości innego obiektu.  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     Aby uzyskać więcej informacji o opcjach definiowania właściwości w typach anonimowych, zobacz [How to: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [Instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
