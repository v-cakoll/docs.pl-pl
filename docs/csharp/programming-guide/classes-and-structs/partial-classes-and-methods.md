---
title: Klasy częściowe i metody - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 222a47989537f09fd78c4a3b17fa8c1a5478d73f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243468"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Klasy częściowe i metody (Przewodnik programowania w języku C#)
Umożliwia dzielenie definicji [klasy](../../../csharp/language-reference/keywords/class.md), [struktury](../../../csharp/language-reference/keywords/struct.md), [interfejsu](../../../csharp/language-reference/keywords/interface.md) lub metody za pośrednictwem dwóch lub więcej plików źródłowych. Każdy plik źródłowy zawiera sekcję definicji typu lub metody, a wszystkie elementy są łączone, podczas kompilowania aplikacji.  
  
## <a name="partial-classes"></a>Klasy częściowe  
 Istnieje kilka sytuacji, gdy wskazane jest dzielenie definicji klasy:  
  
-   Podczas pracy z dużymi projektami, rozmieszczanie klasę za pośrednictwem osobnych plikach umożliwia wielu programistów pracować nad nim, w tym samym czasie.  
  
-   Podczas pracy z automatycznie wygenerowanego źródła, można dodać kodu do klasy bez konieczności ponownego tworzenia pliku źródłowego. Visual Studio używa tego podejścia, podczas tworzenia formularzy Windows, kodu otoki usługi sieci Web i tak dalej. Możesz utworzyć kod, który używa tych klas bez konieczności modyfikowania pliku tworzone przez program Visual Studio.  
  
-   Aby podzielić definicji klasy, należy użyć [częściowe](../../../csharp/language-reference/keywords/partial-type.md) modyfikator — słowo kluczowe, jak pokazano poniżej:  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 `partial` Słowo kluczowe wskazuje, że inne części klasy, struktury, lub interfejsu może być zdefiniowany w przestrzeni nazw. Wszystkie części muszą używać `partial` — słowo kluczowe. Wszystkie części muszą być dostępne w kompilacji do końcowego typu formularza. Wszystkie części muszą mieć identyczną dostępność, takich jak `public`, `private`i tak dalej.  
  
 Jeśli jakakolwiek część został zadeklarowany jako abstrakcyjny, cały typ będzie traktowany abstrakcyjne. Jeśli jakakolwiek część zadeklarowano sealed, a następnie cały typ jest traktowany jako zapieczętowany. Jeśli jakakolwiek część deklaruje typu podstawowego, cały typ dziedziczy tej klasy.  
  
 Musisz zaakceptować wszystkie elementy, które określają klasy bazowej, ale części, które pominięto klasę bazową nadal dziedziczą typu podstawowego. Części można określić różne interfejsy podstawowe, a końcowe typ implementuje wszystkie interfejsy, które są wyświetlane według częściowe deklaracje. Wszystkie klasy, struktury lub interfejsu elementów członkowskich zadeklarowanych w definicji częściowej są dostępne dla wszystkich innych części. Typ końcowego jest kombinacją wszystkie elementy w czasie kompilacji.  
  
> [!NOTE]
>  `partial` Modyfikator nie jest dostępny na delegata lub wyliczenie deklaracji.  
  
 Poniższy przykład pokazuje, że zagnieżdżone typy mogą być częściowe, nawet jeśli są one zagnieżdżone w obrębie typu nie jest częściowe sam.  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 W czasie kompilacji atrybuty z definicji typu częściowego są scalane. Na przykład należy wziąć pod uwagę następujące deklaracje:  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 Są one równoważnymi następujące deklaracje:  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 Poniżej są scalane z definicji typu częściowego:  
  
-   komentarze XML  
  
-   interfejsy  
  
-   atrybuty parametru typu ogólnego  
  
-   class — Atrybuty  
  
-   elementy członkowskie  
  
 Na przykład należy wziąć pod uwagę następujące deklaracje:  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 Są one równoważnymi następujące deklaracje:  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a>Ograniczenia  
 Istnieje kilka reguł, które należy wykonać podczas pracy z częściowych definicji klasy:  
  
-   Wszystkie definicje typu częściowego, należy traktować jako części tego samego typu, muszą zostać zmodyfikowane za pomocą `partial`. Na przykład następujące deklaracje klas wygenerowanie błędu:  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   `partial` Modyfikator może się pojawić tylko bezpośrednio przed słowa kluczowe `class`, `struct`, lub `interface`.  
  
-   Zagnieżdżone typy częściowe są dozwolone w definicji typu częściowego, jak pokazano w poniższym przykładzie:  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   Wszystkie definicje typu częściowego, należy traktować jako części tego samego typu musi być zdefiniowany w tym samym zestawie i tego samego modułu (plik .exe lub .dll). Definicje częściowe nie mogą obejmować wiele modułów.  
  
-   Nazwa klasy i parametry typu ogólnego muszą być zgodne na wszystkich definicji typu częściowego. Typy rodzajowe mogą być częściowe. Każdy częściowa deklaracja należy użyć tej samej nazwy parametrów w tej samej kolejności.  
  
-   Następujące słowa kluczowe w definicji typu częściowego są opcjonalne, ale jeśli jest obecny na jedną definicję typu częściowego, nie może powodować konfliktu ze słowami kluczowymi, określone w innej definicji częściowej dla tego samego typu:  
  
    -   [public](../../../csharp/language-reference/keywords/public.md)  
  
    -   [private](../../../csharp/language-reference/keywords/private.md)  
  
    -   [protected](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [internal](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   klasa bazowa  
  
    -   [nowe](../../../csharp/language-reference/keywords/new.md) modyfikator (zagnieżdżonych części)  
  
    -   ograniczenia ogólne  
  
         Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="example-1"></a>Przykład 1  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie, pola i Konstruktor klasy `CoOrds`, są deklarowane w jedną definicję klasy częściowe i elementu członkowskiego, `PrintCoOrds`, jest zadeklarowany w innej definicji częściowej klasy.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a>Przykład 2  
  
### <a name="description"></a>Opis  
 Poniższy przykład pokazuje, że możesz również tworzyć częściowej struktury i interfejsy.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a>Metody częściowe  
 Częściowe klasy lub struktury może zawierać metody częściowej. Jedną część klasy zawiera podpis metody. Opcjonalne wdrożenia może być zdefiniowana w części tej samej lub innej części. Jeśli wdrożenia nie jest podany, następnie metoda i wszystkie wywołania do metody są usuwane w czasie kompilacji.  
  
 Metody częściowe umożliwiają implementujący jednej części klasy zdefiniować metodę, podobne do zdarzenia. Implementujący części klasy zdecydować, czy wdrożyć metodę, czy nie. Jeśli metoda nie jest zaimplementowana, a następnie kompilator usuwa metodę podpisu i wszystkie wywołania metody. Wywołania do metody, w tym żadnych wyników, które wystąpiłyby oceny argumenty w wywołaniach, nie mają wpływu w czasie wykonywania. W związku z tym, każdy kod w klasie częściowej bez ograniczeń wykorzystywać metody częściowej, nawet jeśli nie podano wdrożenia. Jeśli metoda jest wywoływana, ale nie zaimplementowana spowoduje, że żadne błędy kompilacji lub czasu wykonywania.  
  
 Metody częściowe są szczególnie przydatne, jako sposób dostosować wygenerowanego kodu. Pozwalają one na nazwę metody i podpisu do zarezerwowania, tak aby wygenerowanego kodu można wywołać metodę, ale deweloper może zdecydować, czy do implementacji metody. Znacznie takich jak klasy częściowe metod częściowych Włącz kod utworzony przez generator kodu i kod utworzony przez ludzi dla deweloperów do współpracują ze sobą bez kosztów środowiska wykonawczego.  
  
 Deklaracji metody częściowej składa się z dwóch części: definicję i implementację. Może to być w osobnych części klasy częściowej lub w tej samej części. Jeśli istnieje żadna deklaracja wdrożenia, a następnie kompilator optymalizuje natychmiast zarówno Definiowanie deklaracji i wszystkie wywołania metody.  
  
```csharp  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   Deklaracje metody częściowej musi zaczynać się od kontekstowego słowa kluczowego [częściowe](../../../csharp/language-reference/keywords/partial-type.md) i metoda musi zwracać [void](../../../csharp/language-reference/keywords/void.md).  
  
-   Metody częściowe mogą mieć [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) lub [ref](../../../csharp/language-reference/keywords/ref.md) , ale nie [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów.  
  
-   Metody częściowe są niejawną kolekcją [prywatnej](../../../csharp/language-reference/keywords/private.md), i dlatego nie może być [wirtualnego](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Metody częściowe nie może być [extern](../../../csharp/language-reference/keywords/extern.md), ponieważ obecność treści Określa, czy są one Definiowanie lub wdrażania.  
  
-   Metody częściowe mogą mieć [statyczne](../../../csharp/language-reference/keywords/static.md) i [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) modyfikatorów.  
  
-   Metody częściowe mogą być ogólne. Ograniczenia są nakładane na definiowanie deklaracji metody częściowej i opcjonalnie może być powtarzany na architekturze implementującej. Parametr i typ nazwy parametru nie muszą być takie same, w deklaracji implementującej jak definiowanie jeden.  
  
-   Możesz wprowadzić [delegować](../../../csharp/language-reference/keywords/delegate.md) do metody częściowej, które zostały zdefiniowane i zaimplementowane, ale nie do metody częściowej, który tylko został zdefiniowany.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [typów częściowych](~/_csharplang/spec/classes.md#partial-types) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
- [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
- [partial (typ)](../../../csharp/language-reference/keywords/partial-type.md)
