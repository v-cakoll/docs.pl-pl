---
title: "Funkcje Visual Basic obsługujące LINQ"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42465dbb168b7961792aec6b3c2bb7ae8f0a3355
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-features-that-support-linq"></a>Funkcje Visual Basic obsługujące LINQ
Nazwa [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] odwołuje się do technologii w języku Visual Basic, czy składnia kwerendy obsługuje i inny język konstruuje bezpośrednio w języku. Z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], nie masz nauczyć się nowego języka aby zapytanie dla zewnętrznego źródła danych. W języku Visual Basic można badać danych relacyjnych baz danych, Magazyny XML lub obiektów. Integracja funkcji kwerendy w języku umożliwia kompilacji sprawdzanie błędów składni i bezpieczeństwo typów. Integracja ta zapewnia również znanych większość musi wiedzieć, aby zapisać rozbudowane, zróżnicowane kwerendy w języku Visual Basic.  
  
 W poniższych sekcjach opisano konstrukcji języka, które obsługują LINQ za mało szczegółowo ułatwia rozpoczęcie pracy podczas odczytywania wprowadzające dokumentacji, przykłady kodu i przykładowe aplikacje. Możesz również kliknąć łącza do bardziej szczegółowych wyjaśnień jak funkcje językowe grupuje umożliwiające zapytanie o języku zintegrowanym znaleźć. Jest dobrym miejscem do rozpoczęcia [wskazówki: Pisanie zapytań w języku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Wyrażenia zapytań  
 Wyrażenia zapytań w języku Visual Basic można wyrazić w składni deklaratywnej podobny do bazy danych SQL lub XQuery. W czasie kompilacji Składnia kwerendy jest konwertowany na wywołania metody do dostawcy LINQ implementacja metody rozszerzenia operator standardowej kwerendy. Określanie aplikacji standardowych operatorów zapytań należą do zakresu, określając odpowiedni obszar nazw o `Imports` instrukcji. Składnia wyrażenia zapytania języka Visual Basic wygląda następująco:  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Niejawnie wpisane zmienne  
 Zamiast jawnego określania typu po zadeklarowaniu i zainicjuj zmienną, można włączyć kompilatora wnioskować i przypisać typu. Jest to określane jako *wnioskowanie o typie lokalnym*.  
  
 Zmienne, których typy są wywnioskować są silnie typizowane, podobnie jak zmienne o typie, określ w sposób jawny. Wnioskowanie o typie lokalnym działa tylko wtedy, gdy są definiowane zmiennej lokalnej wewnątrz treści metody. Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Poniższy przykład przedstawia wnioskowanie o typie lokalnym. Aby użyć tego przykładu, należy ustawić `Option Infer` do `On`.  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 Wnioskowanie o typie lokalnym również umożliwia tworzenie typy anonimowe, które zostały opisane dalej w tej sekcji oraz są niezbędne do kwerend LINQ.  
  
 W poniższym przykładzie LINQ wnioskowanie o typie występuje, gdy `Option Infer` jest `On` lub `Off`. Błąd kompilacji występuje, gdy `Option Infer` jest `Off` i `Option Strict` jest `On`.  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>Inicjatory obiektów  
 Inicjatory obiektów są używane w wyrażeniach zapytań, podczas tworzenia typu anonimowego dla wyników zapytania. Ich można również zainicjować obiektów o nazwie typów poza zapytania. Za pomocą inicjatora obiektów, można zainicjować obiektu w jednym wierszu bez jawnego wywołania konstruktora. Zakładając, że istnieje klasa o nazwie `Customer` mający publicznego `Name` i `Phone` właściwości, oraz inne właściwości inicjatora obiektów mogą być używane w ten sposób:  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Typy anonimowe  
 Typy anonimowe zapewnić wygodny sposób tymczasowo grupy zbiór właściwości do elementu, który ma być uwzględniony w wyniku zapytania. Dzięki temu można wybrać dowolną kombinację dostępnych pól w zapytaniu, w dowolnej kolejności bez zdefiniowania typu danych nazwanego elementu.  
  
 *Typu anonimowego* jest tworzony dynamicznie przez kompilator. Nazwa typu jest przypisywany przez kompilator i mogą ulec zmianie z każdej nowej kompilacji. W związku z tym nie można użyć nazwy bezpośrednio. Typy anonimowe są inicjowane w następujący sposób:  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozszerzeń  
 Metody rozszerzenia umożliwiają dodanie metody typu danych lub interfejsu poza definicją. Ta funkcja umożliwia, w efekcie Dodawanie nowych metod do istniejącego typu nie modyfikując typu. Standardowe operatory zapytań są zestawem metody rozszerzenia, które zapewniają [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania funkcji dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Inne rozszerzenia <xref:System.Collections.Generic.IEnumerable%601> obejmują <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, i <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 Następującą metodę rozszerzenie dodaje metodę wydruku <xref:System.String> klasy.  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 Metoda jest wywoływana jak metod wystąpień zwykłej <xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 Wyrażenie lambda jest funkcją bez nazwy, która jest obliczana i zwraca pojedynczą wartość. W przeciwieństwie do funkcji o nazwie wyrażenia lambda mogą być definiowane i wykonywane w tym samym czasie. W poniższym przykładzie przedstawiono 4.  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 Można przypisać definicji wyrażenia lambda na nazwę zmiennej, a następnie użyj nazwy do wywołania tej funkcji. W poniższym przykładzie przedstawiono również 4.  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], wyrażenia lambda opierają się wiele standardowych operatorów zapytań. Kompilator tworzy wyrażenia lambda do przechwytywania obliczeń, które są zdefiniowane w metody podstawowych zapytań, takich jak `Where`, `Select`, `Order By`, `Take While`i inne.  
  
 Na przykład poniższy kod definiuje kwerendę, która zwraca wszystkich studentów wyższych z listy studentów.  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 Definicja zapytania jest kompilowany do kodu, który jest podobny do poniższego przykładu, które używa dwóch wyrażeń lambda, aby określić argumenty `Where` i `Select`.  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 Można uruchomić przy użyciu danej wersji `For Each` Pętla:  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Wprowadzenie do korzystania z LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
