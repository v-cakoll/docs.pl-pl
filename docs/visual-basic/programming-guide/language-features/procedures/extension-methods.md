---
title: "Metody rozszerzeń (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d3db3bc2b213b78ef2dceebcf56c9d5fbfa3016e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="extension-methods-visual-basic"></a>Metody rozszerzeń (Visual Basic)
Metody rozszerzenia umożliwiają deweloperom dodania funkcji niestandardowych do typów danych, które zostały już zdefiniowane bez tworzenia nowego typu pochodnego. Metody rozszerzenia umożliwiają napisanie metody, która może być wywołana tak, jakby była metodą wystąpienia istniejącego typu.  
  
## <a name="remarks"></a>Uwagi  
 Metody rozszerzenia mogą być tylko `Sub` procedury lub `Function` procedury. Nie można zdefiniować właściwości rozszerzenia, pole lub zdarzeń. Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw.  
  
 Pierwszy parametr w definicji — metoda rozszerzenia Określa typ danych metoda jest rozszerzeniem. Po uruchomieniu metoda pierwszy parametr jest powiązany z wystąpieniem typu danych, która wywołuje metodę.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie zdefiniowano `Print` rozszerzenie <xref:System.String> — typ danych. W metodzie `Console.WriteLine` do wyświetlenia ciąg. Parametr `Print` metody `aString`, określa, że metoda jest rozszerzeniem <xref:System.String> klasy.  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 Zwróć uwagę, że definicji — metoda rozszerzenia jest oznaczony atrybutem rozszerzenia `<Extension()>`. Oznaczenie modułu, w którym zdefiniowana jest metoda jest opcjonalne, ale każda metoda rozszerzenia musi być oznaczona. <xref:System.Runtime.CompilerServices>należy zaimportować tak, aby uzyskać dostęp do atrybutu rozszerzenia.  
  
 Metody rozszerzenia mogą być deklarowane tylko w modułach. Zazwyczaj modułu, w którym jest zdefiniowany — metoda rozszerzenia nie jest tym samym module, w którym jest wywoływana. Zamiast tego należy moduł, który zawiera metody rozszerzenia są importowane, jeśli wymagane jest, aby przełączyć go do zakresu. Po moduł, który zawiera `Print` jest w zakresie, można wywołać metody, tak jakby był on metodę zwykłej wystąpienia, który nie przyjmuje żadnych argumentów, takich jak `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 Kolejnym przykładzie `PrintAndPunctuate`, także jest rozszerzeniem <xref:System.String>, teraz zdefiniowany dwa parametry. Pierwszy parametr `aString`, określa, że metodę rozszerzenie rozszerza <xref:System.String>. Drugi parametr `punc`, jest przeznaczona do postaci ciągu znaków interpunkcyjnych, który jest przekazywany jako argument podczas wywoływania metody. Metoda wyświetla ciąg następuje znaków interpunkcyjnych.  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 Metoda jest wywoływana przez wysyłanie argument ciągu `punc`:`example.PrintAndPunctuate(".")`  
  
 W poniższym przykładzie przedstawiono `Print` i `PrintAndPunctuate` zdefiniowany i wywołać. <xref:System.Runtime.CompilerServices>zostaną zaimportowane w module definicji w celu umożliwienia dostępu do atrybutu rozszerzenia.  
  
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
  
 Metody rozszerzenia są następnie wejścia zakres i o nazwie.  
  
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
 Wymaganiem, aby można było uruchomić te lub podobne metody rozszerzenia jest, aby być w zakresie. Jeśli moduł, który zawiera metody rozszerzenia znajduje się w zakresie, jest widoczny w IntelliSense i można wywołać, tak jakby był on metodę wystąpienia zwykłej.  
  
 Zwróć uwagę, że gdy metody są wywoływane, Brak argumentu nie są przesyłane pierwszego parametru. Parametr `aString` w metodzie poprzedniej definicje jest powiązany z `example`, wystąpienie `String` , który odwołuje się je. Kompilator użyje `example` jako argument wysyłane do pierwszego parametru.  
  
 Jeśli metoda rozszerzenia jest wywoływana dla obiekt, który ma ustawioną wartość `Nothing`, wykonuje metodę rozszerzenie. Dotyczy to zwykłych wystąpienia metody. Można jawnie sprawdzaj `Nothing` w metodzie rozszerzenia.  
  
## <a name="types-that-can-be-extended"></a>Typy, które mogą zostać rozszerzone  
 Można zdefiniować metody rozszerzenia większość typów, które może być reprezentowany w liście parametrów języka Visual Basic, takie jak następujące:  
  
-   Klasy (typy referencyjne)  
  
-   Struktury (typy wartości)  
  
-   Interfejsy  
  
-   Delegaty  
  
-   Argumenty ByRef i ByVal  
  
-   Parametry ogólne — metoda  
  
-   Tablice  
  
 Ponieważ pierwszy parametr określa typ danych, rozszerzający metody rozszerzenia, jest wymagana i nie może być opcjonalny. Z tego powodu `Optional` parametrów i `ParamArray` parametrów nie może być pierwszym parametrem na liście parametrów.  
  
 Metody rozszerzenia nie są wliczane późne wiązanie. W poniższym przykładzie instrukcja `anObject.PrintMe()` zgłasza <xref:System.MissingMemberException> wyjątek, ten sam wyjątek, zobaczysz, jeśli drugi `PrintMe` definicji — metoda rozszerzenia zostały usunięte.  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Metody rozszerzenia udostępniają wygodnym i zaawansowanym sposób rozszerzenia istniejącego typu. W celu użycia pomyślnie istnieją pewne kwestie do rozważenia. Te kwestie głównie autorów bibliotek klas, ale mogą wpłynąć na dowolnej aplikacji, która używa metody rozszerzenia.  
  
 Metody rozszerzenia, które dodajesz do typów, które nie ma są zazwyczaj, bardziej narażony, niż metody rozszerzenia dodane do typów, które kontrolujesz. Liczba elementów może wystąpić w klasach nie użytkownika, które może zakłócać metody rozszerzenia.  
  
-   Jeśli żadnego członka dostępne wystąpienia istnieje, która ma podpisu zgodnego z argumentów w instrukcji wywoływania z konwersji zawężającej wymagane od argumentu do parametru, zostanie użyta metoda wystąpienia preferowanego w stosunku do dowolnej metody rozszerzenia. W związku z tym jeśli metoda odpowiednie wystąpienie jest dodawana do klasy, w pewnym momencie, istniejącym elementem członkowskim rozszerzenia, które korzystają z mogą stać się niedostępne.  
  
-   Autor metody rozszerzenia nie może uniemożliwić zapisywanie metod rozszerzeń powodujące konflikt, które mogą mieć pierwszeństwo nad oryginalne rozszerzenie innych programistów.  
  
-   Można zwiększyć niezawodność umieszczenie metody rozszerzenia w ich własnej przestrzeni nazw. Konsumenci biblioteki dołączyć przestrzeni nazw lub go wykluczyć lub wybierz jeden z przestrzeni nazw, niezależnie od pozostałej części biblioteki.  
  
-   Może być bezpieczniejsze rozszerzenie interfejsów, niż jest rozszerzenie klasy, zwłaszcza, jeśli nie ma interfejsu lub klasy. Zmiana w interfejsie wpływa na każdej klasy, która implementuje go. W związku z tym Autor może być mniej prawdopodobne dodać lub zmienić metody w interfejsie. Jednak jeśli klasa implementuje dwa interfejsy, które mają metody rozszerzenia o tej samej sygnaturze, żadna z tych metod rozszerzenia jest widoczny.  
  
-   Rozszerzanie najbardziej określonego typu, które można wykonywać następujące czynności. W hierarchii typów Jeśli należy wybrać typ, od których pochodzą wiele innych typów, istnieją warstwy możliwości wprowadzania wystąpienia metody lub innych metod rozszerzenia, które może zakłócać należy do Ciebie.  
  
## <a name="extension-methods-instance-methods-and-properties"></a>Metody rozszerzenia, wystąpienie metody i właściwości  
 Metody wystąpienia w zakresie po podpisie, który jest zgodny z argumentami instrukcji wywoływania metody wystąpienia jest wybierany preferowanego w stosunku do dowolnej metody rozszerzenia. Metoda wystąpienia ma pierwszeństwo, nawet jeśli — metoda rozszerzenia jest lepszym dopasowaniem. W poniższym przykładzie `ExampleClass` zawiera metodę wystąpienia o nazwie `ExampleMethod` który ma jeden parametr typu `Integer`. Metody rozszerzenia `ExampleMethod` rozszerza `ExampleClass`, i ma jeden parametr typu `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 W pierwszym wywołaniu `ExampleMethod` poniższy kod wywołuje metodę rozszerzenia, ponieważ `arg1` jest `Long` i jest zgodna tylko z `Long` parametru w metodzie rozszerzenia. Drugie wywołanie `ExampleMethod` ma `Integer` argumentu, `arg2`, i wywołuje metodę wystąpienia.  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 Teraz wycofywania typów danych parametrów w dwóch metod:  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 Tym razem kod w `Main` wywołuje metodę wystąpienia razem. Jest to spowodowane zarówno `arg1` i `arg2` umożliwiać konwersję rozszerzającą do `Long`, oraz metody wystąpienia mają pierwszeństwo przed — metoda rozszerzenia w obu przypadkach.  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 W związku z tym metody rozszerzenia nie może zastąpić istniejącą metodę wystąpienia. Jednak gdy metody rozszerzenia ma taką samą nazwę jako metodę wystąpienia, ale nie powodują konfliktu podpisy, obie metody są dostępne. Na przykład jeśli klasa `ExampleClass` zawiera metodę o nazwie `ExampleMethod` pobierającej nie argumentów, metody rozszerzenia o tej samej nazwie, ale różnych podpisów są dozwolone, jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 Dane wyjściowe z tego kodu jest następujący:  
  
 `Extension method`  
  
 `Instance method`  
  
 Sytuacja jest prostsze właściwości: Jeśli metody rozszerzenia ma taką samą nazwę jak właściwość rozszerza klasy, metody rozszerzenia nie jest widoczny i nie są dostępne.  
  
## <a name="extension-method-precedence"></a>Pierwszeństwo — metoda rozszerzenia  
 Gdy dwie metody rozszerzenia, które mają identyczne podpisy są w zakresie i jest dostępny, zostanie wywołany z wyższy priorytet. Metody rozszerzenia pierwszeństwo jest oparta na mechanizm służący do wprowadzenia metody w zakresie. Na poniższej liście przedstawiono hierarchią pierwszeństwo w kolejności malejącej.  
  
1.  Metody rozszerzenia, zdefiniowane wewnątrz bieżącego modułu.  
  
2.  Metody rozszerzenia zdefiniowane wewnątrz danych typów w bieżącej przestrzeni nazw lub jednego z jego elementów nadrzędnych z podrzędne przestrzenie nazw mające wyższy priorytet niż nadrzędny przestrzeni nazw.  
  
3.  Metody rozszerzenia, zdefiniowane wewnątrz wszystkie Importy typu w bieżącym pliku.  
  
4.  Metody rozszerzenia, zdefiniowane wewnątrz żadnych importów przestrzeni nazw w bieżącym pliku.  
  
5.  Metody rozszerzenia, zdefiniowane wewnątrz importów dowolnego typu na poziomie projektu.  
  
6.  Metody rozszerzenia zdefiniowany w dowolnym importowane elementy obszaru nazw poziom projektu.  
  
 Jeśli pierwszeństwo rozwiązania niejednoznaczności, można w pełni kwalifikowana nazwa Określ metodę, która jest wywoływana. Jeśli `Print` poprzedniego przykładu metoda jest zdefiniowany w module o nazwie `StringExtensions`, jest w pełni kwalifikowana nazwa `StringExtensions.Print(example)` zamiast `example.Print()`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [Metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [Module — instrukcja](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Parametry opcjonalne](./optional-parameters.md)  
 [Tablice parametrów](./parameter-arrays.md)  
 [Atrybuty — omówienie](../../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
