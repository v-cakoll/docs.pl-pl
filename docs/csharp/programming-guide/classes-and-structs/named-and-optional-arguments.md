---
title: Argumenty nazwane i opcjonalne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c3c2c2ec0c982582032c1ae586d23226028ad899
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Argumenty nazwane i opcjonalne (Przewodnik programowania w języku C#)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] wprowadza argumenty nazwane i opcjonalne. *Argumenty nazwane o* można określić argumentu dla parametru określonego przez skojarzenie argument o nazwie parametru, a nie parametru pozycji na liście parametrów. *Argumenty opcjonalne* można pominąć argumenty dla niektórych parametrów. Obie techniki można używać z metod, indeksatorów konstruktory i delegatów.  
  
 Użycie argumentów nazwanych i opcjonalnych argumentach są oceniane w kolejności, w którym są wyświetlane na liście argumentów nie listy parametrów.  
  
 Parametry nazwane i opcjonalne, gdy jest używany razem umożliwiają podać argumenty tylko kilka parametrów z listy parametrów opcjonalnych. Ta funkcja znacznie ułatwia wywołania do interfejsów modelu COM, takie jak interfejsy API Microsoft Office automatyzacji.  
  
## <a name="named-arguments"></a>Argumenty nazwane  
 Argumenty nazwane pozbawione potrzebę do zapamiętania lub wyszukania kolejność parametrów na listach parametrem wywoływane metody. Parametr dla każdego argumentu można określić nazwę parametru. Na przykład funkcja, która wyświetla szczegóły zamówienia (takich jak nazwy sprzedawcy, kolejność numer & produktu nazwy), wysyłając argumentów według pozycji w kolejności, zdefiniowany przez funkcję można wywołać w sposób standardowy.
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 Jeśli nie pamięta kolejność parametrów, ale znasz ich nazw, możesz wysłać argumenty w dowolnej kolejności.  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 Argumenty nazwane również poprawić czytelność kodu, określając reprezentuje każdy argument. W metodzie przykładzie poniżej `sellerName` nie może mieć wartości null ani biały znak. Jednocześnie jako `sellerName` i `productName` są typu ciąg, zamiast wysyłać argumentów według pozycji, warto użyć nazwane argumenty do odróżniania dwóch i uniknąć pomyłek dla każdego odczytywania kod.
  
 Nazwane argumenty, gdy jest używany z argumenty pozycyjne, są prawidłowe tak długo, jak 

- nie są one następuje argumenty pozycyjne lub

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _począwszy od C# 7.2_, są używane w poprawnej pozycji. W przykładzie poniżej parametr `orderNum` jest w prawidłowym miejscu, ale nie jest jawnie nazwane.

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 Jednak poza kolejnością nazwane argumenty są nieprawidłowe, jeśli jest następuje argumenty pozycyjne.

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>Przykład  
 Poniższy kod implementuje przykłady w tej sekcji oraz dodatkowe niektóre z nich.  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a>Argumenty opcjonalne  
 Definicja metody, konstruktora, indeksatora lub delegata można określić, czy wymagane są jego parametrów lub że są opcjonalne. Każde wywołanie podać argumenty dla wszystkich wymaganych parametrów, ale można pominąć argumentów dla parametrów opcjonalnych.  
  
 Każdy opcjonalny parametr ma wartość domyślną w ramach swojej definicji. Jeśli argument nie jest wysyłany dla tego parametru, zostanie użyta domyślna wartość. Wartość domyślna musi mieć jedną z następujących typów wyrażeń:  
  
-   wyrażenie stałe;  
  
-   wyrażenie w postaci `new ValType()`, gdzie `ValType` jest typem wartości, takich jak [wyliczenia](../../../csharp/language-reference/keywords/enum.md) lub [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
-   wyrażenie w postaci [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), gdzie `ValType` jest typem wartości.  
  
 Parametry opcjonalne są definiowane na końcu listy parametrów po wszelkie wymagane parametry. Jeśli element wywołujący zapewnia argumentu dla dowolnego kolejne parametry opcjonalne, podaj argumenty dla wszystkich powyższych parametrów opcjonalnych. Rozdzielana przecinkami luk w liście argumentów nie są obsługiwane. Na przykład w poniższym kodzie metody wystąpienia `ExampleMethod` jest zdefiniowana z jednym wymagane i dwa parametry opcjonalne.  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 Następujące wywołanie do `ExampleMethod` powoduje błąd kompilatora, ponieważ argument podano trzeci parametr, ale nie dla drugiego.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 Jednak jeśli znasz nazwę trzeci parametr służy nazwany argument do wykonania zadania.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense używa nawiasów w celu wskazania następujące parametry opcjonalne, jak pokazano na poniższej ilustracji.  
  
 ![Szybkie informacje funkcji IntelliSense dla metody ExampleMethod. ] (../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")  
Parametry opcjonalne w ExampleMethod  
  
> [!NOTE]
>  Parametry opcjonalne może deklarować także przy użyciu programu .NET <xref:System.Runtime.InteropServices.OptionalAttribute> klasy. `OptionalAttribute` Parametry nie wymagają wartości domyślnej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie, Konstruktor `ExampleClass` ma jeden parametr, który jest opcjonalne. Metoda wystąpienia `ExampleMethod` ma jeden wymagany parametr `required`i dwa parametry opcjonalne, `optionalstr` i `optionalint`. Kod w `Main` przedstawiono różne sposoby, w którym można wywołać konstruktora i metody.  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a>Interfejsy modelu COM  
 Argumenty nazwane i opcjonalne mechanizmy obiekty dynamiczne i inne rozszerzenia znacznie zwiększyć współdziałanie z interfejsów API modelu COM, takie jak interfejsów API automatyzacji pakietu Office.  
  
 Na przykład [Autoformatowanie](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat(v=office.15).aspx) metody w programie Microsoft Office Excel [zakres](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range(v=office.15).aspx) interfejs ma siedmiu parametrów, które są opcjonalne. Te parametry są wyświetlane na poniższej ilustracji.  
  
 ![Szybkie informacje funkcji IntelliSense dla metody Autoformatowanie. ] (../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")  
Parametry Autoformatowanie  
  
 W języku C# 3.0 i wcześniejszych wersjach, wymagany jest argument dla każdego parametru, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 Jednak może bardzo uprościć wywołanie `AutoFormat` przy użyciu argumentów nazwanych i opcjonalnych wprowadzono w języku C# w wersji 4.0. Nazwę i opcjonalne argumenty umożliwiają Pomiń argumentu dla parametru opcjonalnego, jeśli nie chcesz zmienić wartość domyślna parametru. W poniższym wywołaniu określono wartość tylko dla jednego z parametrów siedem.  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [porady: stosowanie nazwanych i argumentów opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) i [porady: dostępu do obiektów międzyoperacyjności pakietu Office za pomocą Visual C# funkcji](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Rozpoznanie przeciążenia  
 Użycie argumentów nazwanych i opcjonalnych wpływa na rozpoznanie przeciążenia w następujący sposób:  
  
-   Metoda, indeksator lub Konstruktor jest kandydatem do wykonania, jeśli każdego z jego parametrów jest opcjonalny, albo odpowiada według nazwy lub stanie pojedynczy argument w instrukcji wywołującego, oraz że argument można przekonwertować na typ parametru.  
  
-   Jeśli zostanie znaleziony więcej niż jednego kandydata, zasady rozpoznawania przeciążenia preferowanych konwersje są stosowane do argumentów, które zostały jawnie określone. Pominięcia Argumenty opcjonalne parametry są ignorowane.  
  
-   Jeśli dwa kandydatów zostaną ocenione jako jednakowo dobry, preferencji prowadzi do kandydujących, który nie ma następujące parametry opcjonalne dla których argumenty zostały pominięte w wywołaniu. Jest to konsekwencją Ogólne preferencji w wiązaniem dla elementów, które mają mniej parametrów.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [Używanie typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [Używanie konstruktorów](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [Używanie indeksatorów](../../../csharp/programming-guide/indexers/using-indexers.md)
