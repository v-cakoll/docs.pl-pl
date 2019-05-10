---
title: Metody rozszerzeń (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 48a2609a1931e55d24d98cd2b336fc16c520c948
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649640"
---
# <a name="extension-methods-visual-basic"></a>Metody rozszerzeń (Visual Basic)
Metody rozszerzające umożliwiają programistom dodawanie niestandardowych funkcji do typów danych, które są już zdefiniowane bez tworzenia nowego typu pochodnego. Metody rozszerzające umożliwiają napisanie metody, która może być wywoływany tak, jakby jego była wystąpieniem metody istniejącego typu.  
  
## <a name="remarks"></a>Uwagi  
 Metoda rozszerzenia może być tylko `Sub` procedury lub `Function` procedury. Nie można zdefiniować właściwości rozszerzenia, pola lub zdarzenia. Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw.  
  
 Pierwszy parametr w definicji metody rozszerzenie Określa typ danych, które rozszerza metoda. Gdy metoda jest uruchomiona, pierwszy parametr jest powiązany do wystąpienia typu danych, który wywołuje tę metodę.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie zdefiniowano `Print` rozszerzenie <xref:System.String> — typ danych. Metoda używa `Console.WriteLine` do wyświetlenia ciągu. Wartość parametru `Print` metody `aString`, ustala, że metoda rozszerza <xref:System.String> klasy.  
  
 [!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]  
  
 Należy zauważyć, że definicja metody rozszerzenia jest oznaczona atrybutem rozszerzenia `<Extension()>`. Oznaczanie modułu, w którym metoda jest określona jest opcjonalne, ale każda metoda rozszerzenia musi być oznaczona. <xref:System.Runtime.CompilerServices> muszą być importowane w celu uzyskania dostępu do atrybutu rozszerzenia.  
  
 Metody rozszerzenia mogą być deklarowane tylko w modułach. Zazwyczaj moduł, w którym zdefiniowano metody rozszerzenia nie jest tym samym module, w którym jest wywoływana. Zamiast tego modułu, który zawiera metodę rozszerzająca jest importowany, jeśli wymagane jest, aby wprowadzić dane do zakresu. Po tym jak moduł zawierający `Print` jest w zakresie, można wywołać metody, tak jakby był metodą instancji zwykłej, która nie przyjmuje żadnych argumentów, takich jak `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]  
  
 Następny przykład `PrintAndPunctuate`, również jest rozszerzeniem <xref:System.String>, tym razem zdefiniowane za pomocą dwóch parametrów. Pierwszy parametr `aString`, ustala, że metoda rozszerzenia rozszerza <xref:System.String>. Drugi parametr `punc`, ma być ciągiem znaków interpunkcyjnych, który jest przekazywany jako argument przy wywołaniu metody. Metoda wyświetla ciąg, a następnie znaków interpunkcyjnych.  
  
 [!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]  
  
 Metoda jest wywoływana przez wysłanie argumentu ciągu dla `punc`: `example.PrintAndPunctuate(".")`  
  
 W poniższym przykładzie przedstawiono `Print` i `PrintAndPunctuate` zdefiniowane i wywoływane. <xref:System.Runtime.CompilerServices> jest importowany w module definicji w celu umożliwienia dostępu do atrybutu rozszerzenia.  
  
### <a name="code"></a>Kod  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 Następnie metody rozszerzające są dostosowane do zakresu i o nazwie.  
  
```vb  
Imports ConsoleApplication2.StringExtensions  
Module Module1  
  
    Sub Main()  
  
        Dim example As String = "Example string"  
        example.Print()  
  
        example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Komentarze  
 Wszystko co jest wymagane, aby można było uruchomić te lub podobne metody rozszerzenia jest, aby były one w zakresie. Jeśli moduł, który zawiera metodę rozszerzającą znajduje się w zakresie, jest widoczny w technologii IntelliSense i może być wywoływany tak, jakby był metodą instancji zwykłej.  
  
 Należy zauważyć, że gdy metody są wywołane, żaden argument nie jest wysyłany jako pierwszy parametr. Parametr `aString` w poprzedniej metody jest powiązana definicje `example`, wystąpienie `String` które je wywołuje. Kompilator będzie używał `example` jako argumentu wysyłanego do pierwszego parametru.  
  
 Jeśli metoda rozszerzająca zostanie wywołana dla obiektu, który jest ustawiony na `Nothing`, metoda rozszerzająca zostanie wykonana. To nie ma zastosowania do metod zwykłego wystąpienia. Możesz jawnie szukać `Nothing` w metodzie rozszerzenia.  
  
## <a name="types-that-can-be-extended"></a>Typy, które mogą zostać rozszerzone  
 Można zdefiniować metodę rozszerzenia w większości typów, które mogą być reprezentowane w liście parametrów języka Visual Basic, takie jak następujące:  
  
- Klasy (typy odwołań)  
  
- Struktury (typy wartości)  
  
- Interfejsy  
  
- Delegaty  
  
- Argumenty ByRef i ByVal  
  
- Parametry metody ogólnej  
  
- Tablice  
  
 Ponieważ pierwszy parametr określa typ danych, który rozszerza metoda rozszerzenia, jest wymagana i nie może być opcjonalny. Z tego powodu `Optional` parametrów i `ParamArray` parametrów nie może być pierwszym parametrem na liście parametrów.  
  
 Metody rozszerzenia nie są uwzględniane w późnym wiązaniu. W poniższym przykładzie instrukcja `anObject.PrintMe()` zgłasza <xref:System.MissingMemberException> wyjątek, ten sam wyjątek zostałby wyświetlony, gdyby drugi `PrintMe` definicja metody rozszerzenia zostały usunięte.  
  
 [!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Metody rozszerzenia zapewniają wygodny, zaawansowany sposób rozszerzenia istniejącego typu. Aby ich używać, istnieją pewne kwestie do rozważenia. Te zagadnienia dotyczą głównie autorów bibliotek klas, ale mogą mieć wpływ na dowolnej aplikacji, która wykorzystuje metody rozszerzeń.  
  
 Najogólniej mówiąc metody rozszerzenia, które można dodać do typów, które nie są jego własnością są bardziej narażone niż metody rozszerzające dodane do typów, które możesz kontrolować. Kilka rzeczy, może wystąpić w klasach, których nie jesteś właścicielem, które mogą zakłócać Twoje rozszerzenia metody.  
  
- Jeśli istnieje jakikolwiek dostępny członek wystąpienia, który ma podpis, który jest zgodny z argumentami w instrukcji wywołujące, bez konwersji zawężającej wymaganej od argumentu do parametru, metoda wystąpienia będą używane zamiast dowolnej metody. W związku z tym jeśli odpowiednia metoda wystąpienia jest dodawany do klasy w jakimś momencie, istniejący element członkowski rozszerzenia, które korzystają z może stać się niedostępny.  
  
- Autor metody rozszerzenia nie może uniemożliwić innym programistom od pisania niezgodnych metod rozszerzeń, które mogą mieć pierwszeństwo nad oryginalnym rozszerzeniem.  
  
- Możesz ulepszyć odporność umieszczając metody rozszerzeń w ich przestrzeniach nazw. Konsumenci biblioteki mogą następnie włączyć obszar nazw lub go wykluczyć lub wybrać wśród obszarów nazw, niezależnie od pozostałej części biblioteki.  
  
- Bezpieczniejsze może być rozszerzenie interfejsów niż rozszerzenie klas, zwłaszcza, jeśli nie posiadasz interfejsu lub klasy. Zmiany w interfejsie dotyczą każdej klasy, która implementuje go. W związku z tym Autor może być mniej prawdopodobne dodać lub zmienić metodę w interfejsie. Jeśli jednak klasa implementuje dwa interfejsy, które mają metodę rozszerzającą o tej samej sygnaturze, żadna metoda rozszerzenia jest widoczne.  
  
- Rozszerz najbardziej szczegółowy typ. możesz. W hierarchii typów, w przypadku wybrania typu, od których pochodzą wiele innych typów, istnieją warstwy możliwości wprowadzenia metod instancji lub innych metod rozszerzających, które mogą kolidować z Twoimi.  
  
## <a name="extension-methods-instance-methods-and-properties"></a>Metody rozszerzające, wystąpienia metod i właściwości  
 Gdy w zakresie metoda wystąpień posiada oznaczenie, które są zgodne z argumentami instrukcji wywołania, metoda wystąpienia jest wybierana mieszcząca wszystkich metod rozszerzenia. Metoda instancji ma pierwszeństwo, nawet jeśli metoda rozszerzenia ma lepsze dopasowanie. W poniższym przykładzie `ExampleClass` zawiera metodę instancji o nazwie `ExampleMethod` posiadającą jeden parametr typu `Integer`. Metoda rozszerzenia `ExampleMethod` rozszerza `ExampleClass`, i ma jeden parametr typu `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]  
  
 Pierwsze wywołanie `ExampleMethod` w poniższym kodzie wywołuje metodę rozszerzenia, ponieważ `arg1` jest `Long` i jest zgodny tylko z `Long` parametru w metodzie rozszerzenia. Drugie wywołanie `ExampleMethod` ma `Integer` argument `arg2`, i wywołuje metodę wystąpienia.  
  
 [!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]  
  
 Teraz Odwróć typy danych parametrów w dwóch metod:  
  
 [!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]  
  
 Tym razem z kodem w `Main` wywołuje metodę wystąpienia w obu przypadkach. Jest to spowodowane zarówno `arg1` i `arg2` umożliwiać konwersję rozszerzającą do `Long`, i metoda wystąpienia ma pierwszeństwo przez metoda rozszerzenia w obu przypadkach.  
  
 [!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]  
  
 W związku z tym metody rozszerzenia nie może zastąpić istniejącej metody wystąpienia. Jednakże gdy metoda rozszerzająca ma taką samą nazwę jak metoda wystąpienia, ale podpisy nie będą w konflikcie, obie metody są dostępne. Na przykład jeśli klasa `ExampleClass` zawiera metodę o nazwie `ExampleMethod` która nie przyjmuje argumentów, metody rozszerzające o tej samej nazwie, ale różnych dopuszczalne są, jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]  
  
 Dane wyjściowe z tego kodu jest następująca:  
  
 `Extension method`  
  
 `Instance method`  
  
 Ta sytuacja jest prostsza w przypadku właściwości: Jeżeli metoda rozszerzająca ma taką samą nazwę jak właściwość klasy którą rozszerza, metoda rozszerzenia nie jest widoczna i nie są dostępne.  
  
## <a name="extension-method-precedence"></a>Pierwszeństwo metody rozszerzającej  
 Gdy dwie metody rozszerzające, posiadające identyczne oznaczenie są z zakresie oraz są dostępne, co o wyższym priorytecie zostanie wywołany. Pierwszeństwo metody rozszerzenia opiera się na mechanizmie zastosowanym w celu dostosowania metody do zakresu. Na poniższej liście przedstawiono hierarchię pierwszeństwa, od najwyższego do najniższego.  
  
1. Metody rozszerzające zdefiniowane wewnątrz bieżącego modułu.  
  
2. Metody rozszerzające zdefiniowane wewnątrz typów danych w bieżącej przestrzeni nazw lub jednego z elementów nadrzędnych za pomocą podrzędne przestrzenie nazw mającą wyższy priorytet niż nadrzędna przestrzeń nazw.  
  
3. Metody rozszerzające zdefiniowane wewnątrz dowolnego typu importu w bieżącym pliku.  
  
4. Metody rozszerzające zdefiniowane wewnątrz dowolnej importowanej przestrzeni nazw w bieżącym pliku.  
  
5. Metody rozszerzające zdefiniowane wewnątrz dowolnej importowanej typu na poziomie projektu.  
  
6. Metody rozszerzające zdefiniowane wewnątrz dowolnej importowanej przestrzeni nazw na poziomie projektu.  
  
 Jeśli pierwszeństwo nie rozwiązuje niejasności, można użyć w pełni kwalifikowana nazwa, aby określić metodę, którą wywołujesz. Jeśli `Print` metoda we wcześniejszym przykładzie jest zdefiniowana w module o nazwie `StringExtensions`, w pełni kwalifikowana nazwa to `StringExtensions.Print(example)` zamiast `example.Print()`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Metody rozszerzeń](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Instrukcja Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Tablice parametrów](./parameter-arrays.md)
- [Omówienie atrybuty](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
