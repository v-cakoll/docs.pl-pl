---
title: Funkcje Visual Basic obsługujące LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 155d5c36483accc12d066a5530fea20a563e1498
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977564"
---
# <a name="visual-basic-features-that-support-linq"></a>Funkcje Visual Basic obsługujące LINQ
Nazwa [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] odnosi się do technologii w języku Visual Basic, że obsługuje składni zapytania i innym języku tworzy bezpośrednio w języku. Za pomocą [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], nie trzeba uczenia się nowego języka dla zewnętrznego źródła danych zapytania. Aby wykonać zapytanie względem danych w relacyjnych baz danych, Magazyny XML lub obiektów w języku Visual Basic. Ta integracja możliwości kwerend języka umożliwia kompilacji sprawdzania pod kątem błędów składniowych i bezpieczeństwo typów. Ta integracja zapewnia również znanych większość co musisz wiedzieć, aby pisać rozbudowane, zróżnicowane zapytania w języku Visual Basic.  
  
 W poniższych sekcjach opisano konstrukcji języka, które obsługuje LINQ w wystarczającą ilość szczegółów, aby umożliwić wprowadzenie odczytywanie dokumentację wprowadzającą, przykłady kodu i przykładowe aplikacje. Możesz również kliknąć linki można znaleźć bardziej szczegółowe objaśnienia dotyczące jak funkcje językowe grupuje umożliwiające zapytanie o języku zintegrowanym. Jest dobrym miejscem do rozpoczęcia [instruktażu: Pisanie zapytań w języku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Wyrażenia kwerend  
 Wyrażenia zapytań w języku Visual Basic mogą być wyrażone w składni deklaratywnej, podobnie jak w przypadku bazy danych SQL lub XQuery. W czasie kompilacji Składnia kwerendy jest konwertowane na wywołania metody dostawcę LINQ implementacji metody standardowego operatora zapytań rozszerzenia. Kontrolowanie aplikacji standardowych operatorów zapytań znajdują się w zakresie, określając odpowiedni obszar nazw z `Imports` instrukcji. Składnia wyrażenia zapytania języka Visual Basic wygląda następująco:  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Niejawnie wpisane zmienne  
 Zamiast jawnego określania typu, jeśli zadeklarujesz i zainicjalizujesz zmienną, aby umożliwić kompilatorowi wywnioskowania i przypisać typu. Jest to określane jako *wnioskowanie o typie lokalnym*.  
  
 Zmienne, których typy są wnioskowane są silnie typizowane, podobnie jak zmienne o typie należy jawnie określić. Wnioskowanie o typie lokalnym działa tylko wtedy, gdy definiujesz zmienną lokalną wewnątrz treści metody. Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Poniższy przykład ilustruje wnioskowanie o typie lokalnym. Aby wykorzystać ten przykład, należy ustawić `Option Infer` do `On`.  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 Wnioskowanie o typie lokalnym również umożliwia tworzenie anonimowych typów, które są opisane w dalszej części w tej sekcji i są konieczne do zapytań LINQ.  
  
 W poniższym przykładzie LINQ, wnioskowanie o typie występuje, gdy `Option Infer` jest `On` lub `Off`. Występuje błąd kompilacji, jeśli `Option Infer` jest `Off` i `Option Strict` jest `On`.  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>Inicjatory obiektów  
 Inicjatory obiektów są używane w wyrażeniach zapytań, gdy trzeba utworzyć typ anonimowy do przechowywania wyników zapytania. One może również inicjować obiekty nazwanych typów poza zapytania. Za pomocą inicjatora obiektów, można zainicjować obiektu w pojedynczym wierszu bez jawnego wywołania konstruktora. Przy założeniu, że masz klasę o nazwie `Customer` ma publiczny `Name` i `Phone` właściwości, oraz inne właściwości inicjatora obiektów mogą być używane w ten sposób:  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 Aby uzyskać więcej informacji, zobacz [inicjatory obiektów: Typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Typy anonimowe  
 Typy anonimowe zapewniają wygodny sposób w celu tymczasowego grupowania zestawu właściwości do elementu, który chcesz uwzględnić w wyniku zapytania. Dzięki temu można wybrać dowolną kombinację dostępnych pól w zapytaniu, w dowolnej kolejności bez zdefiniowania typu danych o nazwie elementu.  
  
 *Typu anonimowego* jest tworzony dynamicznie przez kompilator. Nazwa typu jest przypisywany przez kompilator i mogą ulec zmianie z każdej nowej kompilacji. W związku z tym, nie można użyć nazwy bezpośrednio. Typy anonimowe są inicjowane w następujący sposób:  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozszerzeń  
 Metody rozszerzające umożliwiają dodawanie metod do typu danych lub interfejs z poza definicją. Ta funkcja umożliwia, w efekcie dodanie nowych metod do istniejącego typu nie modyfikując typu. Standardowe operatory zapytań są same zestaw metod rozszerzenia, które zapewniają [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania funkcji dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>. Inne rozszerzenia <xref:System.Collections.Generic.IEnumerable%601> obejmują <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, i <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 Następujące metody rozszerzenia dodaje metodę drukowania <xref:System.String> klasy.  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 Metoda jest wywoływana, takich jak to metoda zwykłego wystąpienia <xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 Wyrażenie lambda jest funkcją bez nazwy, który oblicza i zwraca wartość typu single. W przeciwieństwie do funkcji o nazwie wyrażenia lambda mogą być definiowane i wykonywane w tym samym czasie. Poniższy przykład wyświetla 4.  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 Można przypisać Definicja wyrażenia lambda do nazwy zmiennej, a następnie użyj nazwy w wywołaniu funkcji. Poniższy przykład wyświetla również 4.  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], wyrażenia lambda podstawą wiele standardowych operatorów zapytań. Kompilator tworzy wyrażenia lambda do przechwytywania obliczenia, które są zdefiniowane w metody zapytań podstawowych, takich jak `Where`, `Select`, `Order By`, `Take While`i innym osobom.  
  
 Na przykład poniższy kod definiuje zapytanie zwracające wszyscy uczniowie starszy z listy studentów.  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 Definicja zapytania jest skompilowany na kod, który jest podobny do poniższego przykładu, który używa dwóch wyrażeń lambda, aby określić argumenty `Where` i `Select`.  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 Danej wersji, można uruchomić za pomocą `For Each` Pętla:  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Option Infer, instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
