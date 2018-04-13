---
title: "Klasy częściowe i metody (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 396914e487bee0924c36bb1d7a0f28976f4ad354
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Klasy częściowe i metody (Przewodnik programowania w języku C#)
Umożliwia dzielenie definicji [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md), [interfejsu](../../../csharp/language-reference/keywords/interface.md) lub metody za pośrednictwem dwóch lub więcej plików źródłowych. Każdy plik źródłowy zawiera sekcja definicji typu lub metody, a wszystkie elementy są łączone podczas kompilowania aplikacji.  
  
## <a name="partial-classes"></a>Klasy częściowe  
 Istnieje kilka sytuacji, gdy pożądane jest podział definicję klasy:  
  
-   Podczas pracy w przypadku dużych projektów, rozpowszechniania się klasę oddzielnych plików umożliwia wielu programistom na nim pracować, w tym samym czasie.  
  
-   Podczas pracy ze źródłem wygenerowanej automatycznie, można dodać kod do klasy bez konieczności ponownego tworzenia pliku źródłowego. Visual Studio korzysta z tej metody podczas tworzenia formularzy systemu Windows, kodu otoki usługi sieci Web i tak dalej. Można utworzyć kod, który używa tych klas bez konieczności modyfikowania pliku utworzonego przez program Visual Studio.  
  
-   Aby podzielić definicję klasy, należy użyć [częściowe](../../../csharp/language-reference/keywords/partial-type.md) modyfikator — słowo kluczowe, jak pokazano poniżej:  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 `partial` — Słowo kluczowe wskazuje, że inne części klasy, struktury, lub interfejs można zdefiniować w przestrzeni nazw. Wszystkie części muszą używać `partial` — słowo kluczowe. Wszystkie części muszą być dostępne w kompilacji do końcowego typu formularza. Wszystkie części muszą mieć tą samą dostępnością, takie jak `public`, `private`i tak dalej.  
  
 Jeśli żadnej części jest zadeklarowany jako abstrakcyjny, następnie całego typu jest określana jako abstrakcyjny. Części zadeklarowana zapieczętowanym, następnie całego typ jest traktowany jako zapieczętowany. Jeśli któraś deklaruje typ podstawowy, całe typ dziedziczy tej klasy.  
  
 Zaakceptować wszystkie części, które Określ klasę podstawową, ale elementy, które Pomiń klasę podstawową nadal dziedziczą typu podstawowego. Części można określić różnych interfejsach podstawowych i końcowe typ implementuje wszystkich interfejsów, które są wyświetlane według częściowe deklaracje. Wszystkie klasy, struktury lub elementy członkowskie interfejsu zadeklarowany w definicji częściowej są dostępne dla wszystkich innych części. Końcowy Typ jest kombinacją wszystkie części w czasie kompilacji.  
  
> [!NOTE]
>  `partial` Modyfikator nie jest dostępna w deklaracjach delegata lub wyliczenia.  
  
 W poniższym przykładzie pokazano, że zagnieżdżone typy mogą być częściowe, nawet jeśli są one zagnieżdżone w obrębie typu nie jest częściowe sam.  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 W czasie kompilacji atrybutów typu częściowego definicje zostały scalone. Na przykład wziąć pod uwagę następujące deklaracje:  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 Są one odpowiednikiem następujące deklaracje:  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 Poniżej są łączone ze wszystkich definicji typu częściowego:  
  
-   komentarze XML  
  
-   interfejsy  
  
-   atrybuty parametru typu ogólnego  
  
-   class — Atrybuty  
  
-   elementy członkowskie  
  
 Na przykład wziąć pod uwagę następujące deklaracje:  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 Są one odpowiednikiem następujące deklaracje:  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a>Ograniczenia  
 Istnieje kilka reguł, które należy wykonać podczas pracy z definicjami częściowej klasy:  
  
-   Wszystkie definicje typu częściowego przeznaczone do części tego samego typu muszą zostać zmodyfikowane z `partial`. Na przykład następujące deklaracje klas generuje błąd:  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   `partial` Modyfikator może występować tylko bezpośrednio przed słowa kluczowe `class`, `struct`, lub `interface`.  
  
-   Zagnieżdżone typy częściowe są dozwolone w definicji typu częściowego, jak pokazano w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   Wszystkie definicje typu częściowego przeznaczone do części tego samego typu muszą być zdefiniowane w tym samym zestawie i tym samym module (plik .exe lub .dll). Definicje z częściowa nie może obejmować wiele modułów.  
  
-   Nazwa klasy i parametry typu ogólnego muszą odpowiadać na wszystkie definicje typu częściowego. Typy ogólne mogą być częściowe. Każdy z częściowa deklaracja musi używać takie same nazwy parametrów w tej samej kolejności.  
  
-   Poniższe słowa kluczowe w definicji typu częściowego są opcjonalne, ale jeśli jest obecny w jednej definicji typu częściowego, nie powodują konflikt z słów kluczowych określonych w innej definicji częściowej dla tego samego typu:  
  
    -   [public](../../../csharp/language-reference/keywords/public.md)  
  
    -   [private](../../../csharp/language-reference/keywords/private.md)  
  
    -   [protected](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [internal](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   klasa bazowa  
  
    -   [nowe](../../../csharp/language-reference/keywords/new.md) modyfikator (części zagnieżdżonych)  
  
    -   ograniczenia ogólne  
  
         Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="example-1"></a>Przykład 1  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie, pola, konstruktora klasy `CoOrds`, są zadeklarowane w jednej definicji klasy częściowe i element członkowski, `PrintCoOrds`, jest zadeklarowany w innej definicji częściowej klasy.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a>Przykład 2  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie pokazano, że można również zaprojektować częściowej struktury i interfejsy.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a>Metody częściowe  
 Częściowej klasy lub struktury może zawierać metody częściowej. Jedną część klasy zawiera podpis metody. Opcjonalne wdrożenia może być zdefiniowana w tej samej części lub innej części. Jeśli nie podano implementacji, następnie metoda i wszystkie wywołania metody są usuwane w czasie kompilacji.  
  
 Metody częściowe Włącz implementujący jednej części klasy w celu zdefiniowania metody, podobnie jak zdarzenia. Realizator z drugiej strony klasy można zdecydować, czy do implementacji metody, czy nie. Jeśli metoda nie jest zaimplementowana, a następnie usuwa kompilator metodę podpisu i wszystkie wywołania metody. Wywołania do metody, w tym jakiekolwiek wyniki, które wystąpiłyby ewaluacyjną argumentów wywołań, nie obowiązują w czasie wykonywania. W związku z tym dowolny kod w klasie częściowej za darmo można użyć metody częściowej, nawet, jeśli nie podano implementacji. Jeśli metoda jest wywoływana, ale nie zaimplementowano spowoduje, że żadne błędy kompilacji lub w czasie wykonywania.  
  
 Metody częściowe są szczególnie użyteczne jako sposobem dostosowania wygenerowanego kodu. Pozwalają one na nazwę metody i podpis do zarezerwowania, dzięki czemu kod wygenerowany przez można wywołać metody, ale deweloper może zdecydować, czy do implementacji metody. Znacznie takich jak klasy częściowe metody częściowe umożliwiają kod tworzony przez generator kodu i kod utworzony przez człowieka dewelopera współdziałają ze sobą bez kosztów czasu wykonywania.  
  
 Deklaracji metody częściowej składa się z dwóch części: definicja i wdrożenia. Mogą one w oddzielnych części częściowej klasy lub w tej samej części. Jeśli istnieje nie deklaracji w implementacji, a następnie kompilator optymalizuje optymalizacji zarówno Definiowanie deklaracji i wszystkie wywołania metody.  
  
```  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   Deklaracje metody częściowej musi rozpoczynać się od kontekstowe słowo kluczowe [częściowe](../../../csharp/language-reference/keywords/partial-type.md) i metoda musi zwracać [void](../../../csharp/language-reference/keywords/void.md).  
  
-   Metody częściowe mogą mieć [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) lub [ref](../../../csharp/language-reference/keywords/ref.md) , ale nie [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów.  
  
-   Metody częściowe są niejawnie [prywatnej](../../../csharp/language-reference/keywords/private.md), i dlatego nie może być [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Metody częściowe nie może być [extern](../../../csharp/language-reference/keywords/extern.md), ponieważ obecności treści Określa, czy są one Definiowanie lub wykonania.  
  
-   Metody częściowe mogą mieć [statycznych](../../../csharp/language-reference/keywords/static.md) i [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) modyfikatorów.  
  
-   Metody częściowe mogą być ogólne. Ograniczenia są umieszczone w deklaracji metody częściowej definiującej i opcjonalnie może zostać powtórzony na jeden implementującej. Parametr i typ nazwy parametru muszą być takie same, w deklaracji implementującej jak definiująca jeden.  
  
-   Możesz wprowadzić [delegować](../../../csharp/language-reference/keywords/delegate.md) metody częściowej, który został zdefiniowany i wdrożone, ale nie tylko zdefiniowanego metodą częściową.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
 [partial (typ)](../../../csharp/language-reference/keywords/partial-type.md)
