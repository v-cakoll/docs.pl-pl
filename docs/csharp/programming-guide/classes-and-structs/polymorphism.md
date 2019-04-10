---
title: Polimorfizm - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 9bb87115f4649a890d1fb2aab1595c3b6848bc74
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322085"
---
# <a name="polymorphism-c-programming-guide"></a>Polimorfizm (Przewodnik programowania w języku C#)
Polimorfizm często nazywa się trzeci filar programowanie zorientowane obiektowo, po hermetyzacji i dziedziczenia. Polimorfizm jest wyrazem greckim, co oznacza "wiele kształcie" i ma dwa różne aspekty:  
  
-   W czasie wykonywania obiektów klasy pochodne mogą być traktowane jako obiekty klasy bazowej, w miejscach takich jak parametry metody i kolekcje lub tablic. W takiej sytuacji deklarowany typ obiektu nie jest już taka sama jak jego typu run-time.  
  
-   Klasy bazowe mogą definiować ani implementować [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) *metody*, oraz klasy pochodne mogą [zastąpienia](../../../csharp/language-reference/keywords/override.md) je, co oznacza, że zapewniają one własne definicję i implementację. W czasie wykonywania gdy kod klienta wywołuje metodę, środowisko CLR odwołuje się do typu run-time obiektu, a wywołuje zastąpienie metod wirtualnych. Ten sposób w kodzie źródłowym wywołania metody w klasie bazowej i spowodować, że wersja klasy pochodnej metody do wykonania.  
  
 Metody wirtualne umożliwiają pracować z grupami powiązanych obiektów w jednolity sposób. Na przykład załóżmy, że masz rysunku aplikacji, która umożliwia użytkownikowi tworzenie różne rodzaje kształtów na powierzchnię rysunku. Nie wiesz, w czasie kompilacji które określonych rodzajów kształtów spowoduje utworzenie użytkownika. Jednak aplikacja ma do śledzenia różnych typów kształty, które są tworzone i ma je zaktualizować w odpowiedzi na akcje myszy użytkownika. Polimorfizm można użyć, aby rozwiązać ten problem w dwa podstawowe kroki:  
  
1. Tworzenie hierarchii klas, w którym każda klasa kształt pochodzi od klasy wspólną klasę bazową.  
  
2. Użyj metody wirtualnej można wywołać metody odpowiedniej dla dowolnej klasy pochodnej za pomocą jednego wywołania metody klasy bazowej.  
  
 Najpierw należy utworzyć klasę bazową, która wywołuje `Shape`i klas pochodnych, takich jak `Rectangle`, `Circle`, i `Triangle`. Nadaj `Shape` wywołuje metodę wirtualną klasy `Draw`, i zastąpienie go w każdej klasie pochodnej, aby narysować określonych kształtów, klasa reprezentuje. Utwórz `List<Shape>` obiektu i dodać do niego koła, trójkąt i prostokąt. Aby zaktualizować powierzchni do rysowania, użyj [foreach](../../../csharp/language-reference/keywords/foreach-in.md) pętli do iteracji przez listę i wywołania `Draw` metody na każdym `Shape` obiektu na liście. Mimo że każdy obiekt na liście ma zadeklarowany typ `Shape`, jest typu run-time (wersja przesłonięte metody w każdej klasie pochodnej), który zostanie wywołany.  
  
 [!code-csharp[csProgGuideInheritance#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#50)]  
  
 W języku C# polimorficznych jest każdego typu, ponieważ dziedziczy wszystkie typy, w tym typy zdefiniowane przez użytkownika <xref:System.Object>.  
  
## <a name="polymorphism-overview"></a>Polimorfizm — omówienie  
  
### <a name="virtual-members"></a>Wirtualne składowe  
 Klasa pochodna dziedziczy z klasy bazowej, uzyskuje się wszystkie metody, pola, właściwości i zdarzeń klasy podstawowej. Projektant klasy pochodne mogą wybrać opcję  
  
-   Przesłoń składowe wirtualnego w klasie bazowej  
  
-   dziedziczenie najbliższego metody klasy bazowej nie przesłanianie go  
  
-   Zdefiniuj nową metodę niewirtualną implementacji tych członków, którzy Ukryj implementacji klasy podstawowej  
  
 Klasa pochodna można zastąpić składowej klasy bazowej, tylko wtedy, gdy składowej klasy bazowej jest zadeklarowany jako [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) lub [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md). Należy użyć pochodnej elementu członkowskiego [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe, aby jawnie wskazać, że metoda jest przeznaczona do wzięcia udziału w wywołaniu wirtualnego. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#20)]  
  
 Pola nie mogą być wirtualne; tylko metody, właściwości, zdarzeń i indeksatory mogą być wirtualne. Ten element członkowski w klasie pochodnej przeciążono wirtualna elementu członkowskiego, nosi nawet wtedy, gdy wystąpienie tej klasy jest uzyskiwany jako wystąpienia klasy bazowej. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#21)]  
  
 Włącz klasy pochodne, aby rozszerzyć klasę bazową, bez konieczności korzystania z implementacji klasy podstawowej metody, właściwości i metod wirtualnych. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md). Interfejs zapewnia innym sposobem zdefiniowania metody lub zestaw metod, których implementacja pozostanie w klasach pochodnych. Więcej informacji znajdziesz w artykule [Interfejsy](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Ukrywanie składowych klasy bazowej dla nowych członków  
 Jeśli chcesz pochodnej elementów członkowskich mają taką samą nazwę jak element członkowski w klasie bazowej, ale chcesz, aby wziąć udział w wirtualnych wywołania on, możesz użyć [nowe](../../../csharp/language-reference/keywords/new.md) — słowo kluczowe. `new` — Słowo kluczowe jest umieszczany przed zwracanym typem składowej klasy, która jest zastępowany. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#18)]  
  
 Nadal jest możliwy członków ukrytej klasy bazowej z poziomu kodu klienta przez rzutowanie wystąpienie klasy pochodnej do wystąpienia klasy bazowej. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#19)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Uniemożliwia zastępowanie wirtualnych elementów członkowskich klas pochodnych  
 Wirtualne elementy członkowskie nadal wirtualnego przez czas nieokreślony, niezależnie od tego, jak wiele klas zostały zadeklarowane między wirtualna elementu członkowskiego i klasy, która pierwotnie zadeklarowała go. Jeśli klasy A deklaruje wirtualna elementu członkowskiego i klasy B pochodzi od A, a klasa C pochodzi od B, klasa C dziedziczy wirtualna elementu członkowskiego i włączono opcję, aby go zastąpić, niezależnie od tego, czy klasy B podana zastąpienia dla tego elementu członkowskiego. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#22)]  
  
 Klasy pochodnej można zatrzymać dziedziczenie wirtualne od zadeklarowania zastąpienia jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md). Wymaga to umieszczenie `sealed` — słowo kluczowe przed `override` — słowo kluczowe w deklaracji członka klasy. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#24)]  
  
 W poprzednim przykładzie, Metoda `DoWork` nie jest już wirtualnych do dowolnej klasie pochodnej C. Nadal jest wirtualna dla wystąpienia elementu C, nawet wtedy, gdy są one rzutowane na typ B lub typ metody zapieczętowane A. może być zastąpiony przez klasy pochodne przy użyciu `new` — słowo kluczowe, co ilustruje poniższy przykład:  
  
 [!code-csharp[csProgGuideInheritance#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#25)]  
  
 W tym przypadku jeśli `DoWork` jest wywoływana w D przy użyciu zmiennej typu D, nowe `DoWork` jest wywoływana. Jeśli zmienna typu C, B i A umożliwia dostęp do wystąpienia D, wywołanie `DoWork` będzie zgodna z zasadami dziedziczenie wirtualne routingu wywołań do implementacji `DoWork` klasy C.  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Uzyskiwanie dostępu do wirtualnych elementów członkowskich klasy podstawowej w klasach pochodnych  
 Klasa pochodna, która została zastąpiona bądź przesłonięcia metody lub właściwości mogą nadal uzyskiwać dostęp do metody lub właściwości w klasie bazowej, przy użyciu `base` — słowo kluczowe. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#26)]  
  
 Aby uzyskać więcej informacji, zobacz [podstawowy](../../../csharp/language-reference/keywords/base.md).  
  
> [!NOTE]
>  Zalecane jest, że wirtualne elementy członkowskie używać `base` wywoływały implementację klasy bazowej tego członka w ich własnych implementacji. Umożliwienie zachowanie klasy bazowej, występują umożliwia klasy pochodnej skoncentrować się na implementowanie zachowania specyficzne dla klasy pochodnej. Jeśli Implementacja klasy bazowej nie jest wywoływana, to do klasy pochodnej, aby ich zachowanie zgodne z zachowaniem klasy bazowej.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
-   [Użycie przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
-   [Instrukcje: Przesłonięcie metody ToString](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
- [Klasy abstrakcyjne i zapieczętowane oraz składowe klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
- [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Indeksatory](../../../csharp/programming-guide/indexers/index.md)
- [Types](../../../csharp/programming-guide/types/index.md)
