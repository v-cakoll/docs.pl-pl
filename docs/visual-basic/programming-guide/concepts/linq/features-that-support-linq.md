---
title: Funkcje, które obsługują LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 15585cd8277b1a0df7e3b262db7c9b7a231b16fa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383433"
---
# <a name="visual-basic-features-that-support-linq"></a>Funkcje Visual Basic obsługujące LINQ
Nazwa języka (LINQ) (Language-Integrated Query) odnosi się do technologii w Visual Basic, która obsługuje składnię zapytań i inne konstrukcje języka bezpośrednio w języku. Za pomocą LINQ nie trzeba uczyć się nowego języka do wykonywania zapytań względem zewnętrznego źródła danych. Możesz wykonywać zapytania dotyczące danych w relacyjnych bazach danych, sklepach XML lub obiektach przy użyciu Visual Basic. Ta integracja funkcji zapytania w języku umożliwia sprawdzanie w czasie kompilacji pod kątem błędów składni i bezpieczeństwa typów. Ta integracja zapewnia również, że znasz już większość informacji, które należy znać, aby pisać rozbudowane, różne zapytania w Visual Basic.  
  
 W poniższych sekcjach opisano konstrukcje języka, które obsługują LINQ w wystarczająco szczegółowy sposób, aby można było rozpocząć odczytywanie dokumentacji wprowadzającej, przykładów kodu i przykładowych aplikacji. Możesz również kliknąć linki, aby znaleźć bardziej szczegółowe wyjaśnienie sposobu, w jaki funkcje języka łączą się ze sobą, aby włączyć zapytanie zintegrowane z językiem. Dobrym miejscem do rozpoczęcia jest [Przewodnik: Pisanie zapytań w Visual Basic](walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Wyrażenia kwerend  
 Wyrażenia zapytań w Visual Basic mogą być wyrażone w składni deklaracyjnej podobnej do wartości SQL lub XQuery. W czasie kompilacji Składnia zapytania jest konwertowana na wywołania metody do implementacji dostawcy LINQ standardowych metod rozszerzenia operatora zapytania. Aplikacje kontrolują, które standardowe operatory zapytań znajdują się w zakresie, określając odpowiednią przestrzeń nazw z `Imports` instrukcją. Składnia wyrażenia zapytania Visual Basic wygląda następująco:  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](../../language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Niejawnie wpisane zmienne  
 Zamiast jawnie określić typ podczas deklarowania i inicjowania zmiennej, można włączyć kompilator do wnioskowania i przypisania typu. Jest to określane jako *wnioskowanie typu lokalnego*.  
  
 Zmienne, których typy są wywnioskowane, są silnie wpisywane, podobnie jak zmienne, których typ określono jawnie. Wnioskowanie o typie lokalnym działa tylko wtedy, gdy jest definiowana zmienna lokalna wewnątrz treści metody. Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](../../../language-reference/statements/option-infer-statement.md) i [wnioskowanie typu lokalnego](../../language-features/variables/local-type-inference.md).  
  
 Poniższy przykład ilustruje lokalne wnioskowanie o typie. Aby użyć tego przykładu, należy ustawić `Option Infer` na `On` .  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 Wnioskowanie o typie lokalnym umożliwia również tworzenie typów anonimowych, które są opisane w dalszej części tej sekcji i są niezbędne dla zapytań LINQ.  
  
 W poniższym przykładzie LINQ, wnioskowanie typu występuje, jeśli `Option Infer` jest albo `On` `Off` . Błąd czasu kompilacji występuje `Option Infer` , jeśli jest `Off` i ma wartość `Option Strict` `On` .  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>Inicjatory obiektów  
 Inicjatory obiektów są używane w wyrażeniach zapytań, gdy konieczne jest utworzenie typu anonimowego w celu przechowywania wyników zapytania. Mogą one również służyć do inicjowania obiektów nazwanych typów poza zapytaniami. Za pomocą inicjatora obiektów można zainicjować obiekt w pojedynczym wierszu bez jawnego wywołania konstruktora. Przy założeniu, że masz klasę o nazwie, `Customer` która ma charakter publiczny `Name` i `Phone` właściwości, wraz z innymi właściwościami, inicjator obiektu może być używany w ten sposób:  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów: typy nazwane i anonimowe](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Typy anonimowe  
 Typy anonimowe zapewniają wygodny sposób tymczasowego grupowania zestawu właściwości w element, który ma zostać uwzględniony w wyniku zapytania. Dzięki temu można wybrać dowolną kombinację dostępnych pól w zapytaniu w dowolnej kolejności, bez definiowania nazwanego typu danych dla elementu.  
  
 *Typ anonimowy* jest konstruowany dynamicznie przez kompilator. Nazwa typu jest przypisana przez kompilator i może ulec zmianie przy każdej nowej kompilacji. W związku z tym nie można używać bezpośrednio nazwy. Typy anonimowe są inicjowane w następujący sposób:  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozszerzania  
 Metody rozszerzające umożliwiają dodawanie metod do typu danych lub interfejsu spoza definicji. Ta funkcja umożliwia, w efekcie, dodawać nowe metody do istniejącego typu bez faktycznego modyfikowania typu. Standardowe operatory zapytań to zestawy metod rozszerzających, które udostępniają funkcje zapytań LINQ dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> . Inne rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> uwzględnienia <xref:System.Linq.Enumerable.Count%2A> , <xref:System.Linq.Enumerable.Union%2A> i <xref:System.Linq.Enumerable.Intersect%2A> .  
  
 Następujące metody rozszerzające umożliwiają dodanie metody Print do <xref:System.String> klasy.  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 Metoda jest wywoływana jak zwykła metoda wystąpienia <xref:System.String> :  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 Wyrażenie lambda jest funkcją bez nazwy, która oblicza i zwraca pojedynczą wartość. W przeciwieństwie do nazwanych funkcji wyrażenie lambda może być zdefiniowane i wykonywane w tym samym czasie. Poniższy przykład wyświetla 4.  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 Można przypisać definicję wyrażenia lambda do nazwy zmiennej, a następnie użyć nazwy do wywołania funkcji. W poniższym przykładzie jest również wyświetlana wartość 4.  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 W LINQ, wyrażenia lambda podstawą wiele standardowych operatorów zapytań. Kompilator tworzy wyrażenia lambda do przechwytywania obliczeń, które są zdefiniowane w podstawowych metodach zapytań, takich jak `Where` ,, `Select` `Order By` , `Take While` i innych.  
  
 Na przykład poniższy kod definiuje zapytanie, które zwraca wszystkich wyższych uczniów z listy uczniów.  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 Definicja zapytania jest kompilowana w kodzie, który jest podobny do poniższego przykładu, który używa dwóch wyrażeń lambda do określenia argumentów dla `Where` i `Select` .  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 Obie wersje można uruchomić przy użyciu `For Each` pętli:  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../../language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zapytanie zintegrowane z językiem (LINQ) (Visual Basic)](index.md)
- [Wprowadzenie do programu LINQ w Visual Basic](getting-started-with-linq.md)
- [LINQ i ciągi (Visual Basic)](linq-and-strings.md)
- [Option Infer — Instrukcja](../../../language-reference/statements/option-infer-statement.md)
- [Option Strict — Instrukcja](../../../language-reference/statements/option-strict-statement.md)
