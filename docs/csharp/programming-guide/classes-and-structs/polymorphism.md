---
title: Polimorfizm (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 8bbf93d14a16b06441ba48b9d4e19cfd249e9146
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328448"
---
# <a name="polymorphism-c-programming-guide"></a>Polimorfizm (Przewodnik programowania w języku C#)
Polimorfizm jest często określany jako trzeci słupka o programowanie zorientowane obiektowo, po hermetyzacji i dziedziczenia. Polimorfizm jest słowem grecki, która oznacza "wiele kształcie" i ma dwa różne aspekty:  
  
-   W czasie wykonywania obiekty pochodne klasy może być traktowana jako obiekty klasy podstawowej w miejscach, takie jak parametry metody i kolekcje lub tablic. W takim przypadku deklarowany typ obiektu nie jest już takie same jak jego typu run-time.  
  
-   Klasy podstawowe mogą definiować i wdrażać [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) *metody*, i klasy pochodne mogą [zastąpienia](../../../csharp/language-reference/keywords/override.md) je, co oznacza zapewniają własne definicji i implementacji. W czasie wykonywania gdy kod klienta wywołuje metodę, środowiska CLR odwołuje się do typu czasu wykonywania obiektu i wywołuje tego zastąpienie metody wirtualnej. W związku z tym w kodzie źródłowym wywołania metody w klasie podstawowej i spowodować, że wersja klasy pochodnej metody do wykonania.  
  
 Metody wirtualne umożliwiają pracę z grupami powiązanych obiektów w jednolity sposób. Na przykład załóżmy, że masz rysowania aplikacji, która umożliwia użytkownikowi tworzenie różnego rodzaju kształtów na powierzchni do rysowania. Nie wiadomo, w czasie kompilacji które określonych typów kształtów spowoduje utworzenie użytkownika. Jednak aplikacja ma do śledzenia różne typy kształtów, które są tworzone i należy zaktualizować je w odpowiedzi na akcje myszy użytkownika. Polimorfizm można użyć, aby rozwiązać ten problem w dwa podstawowe kroki:  
  
1.  Tworzenie hierarchii klas, w którym każda klasa kształt pochodną wspólną klasę podstawową.  
  
2.  Użyj metody wirtualnej można wywołać metody odpowiedniej dla dowolnej klasy pochodnej za pomocą jednego wywołania metody klasy podstawowej.  
  
 Najpierw Utwórz klasę podstawową o nazwie `Shape`i klasach pochodnych, takich jak `Rectangle`, `Circle`, i `Triangle`. Nadaj `Shape` klasy metodą wirtualną o nazwie `Draw`, i reprezentuje zastąpienie go w każdej klasy pochodnej w celu rysowania określonego kształtu, który klasy. Utwórz `List<Shape>` obiektu i Dodaj do niej koło, trójkąt i prostokąta. Aby zaktualizować na powierzchni do rysowania, użyj [foreach](../../../csharp/language-reference/keywords/foreach-in.md) pętli iterację na liście i wywołanie `Draw` metody na każdym `Shape` obiektu na liście. Mimo że każdy obiekt na liście ma zadeklarowany typ `Shape`, jest typu run-time (wersja przesłoniętej metody w każdej klasy pochodnej), która będzie wywołana.  
  
 [!code-csharp[csProgGuideInheritance#50](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_1.cs)]  
  
 W języku C#, co typ jest polimorficzny ponieważ dziedziczy wszystkich typów, w tym typy danych zdefiniowane przez użytkownika, <xref:System.Object>.  
  
## <a name="polymorphism-overview"></a>Polimorfizm — omówienie  
  
### <a name="virtual-members"></a>Wirtualne elementy członkowskie  
 Klasa pochodna dziedziczy z klasy podstawowej, uzyskuje się wszystkie metody, pola, właściwości i zdarzeń klasy podstawowej. Projektant klasy pochodnej można wybrać opcję  
  
-   zastąpienie wirtualnych elementów członkowskich w klasie podstawowej  
  
-   Dziedzicz bez przesłanianie go najbliższego metody klasy podstawowej  
  
-   Zdefiniuj nowy-virtual stosowania tych elementów członkowskich, które Ukryj implementacji klasy podstawowej  
  
 Klasy pochodne mogą zastąpić element członkowski klasy podstawowej, tylko wtedy, gdy element członkowski klasy podstawowej jest zadeklarowany jako [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) lub [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md). Element członkowski pochodnej należy użyć [zastąpienia](../../../csharp/language-reference/keywords/override.md) — słowo kluczowe, aby jawnie wskazać, że metoda jest przeznaczony do udziału w wywołaniu wirtualnego. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_2.cs)]  
  
 Pola nie może być wirtualny; tylko metody, właściwości, zdarzeń i indeksatory mogą być wirtualne. Ten element członkowski w klasie pochodnej przesłania wirtualny element członkowski, nosi nawet wtedy, gdy wystąpienie tej klasy jest dostępny jako wystąpienie klasy podstawowej. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_3.cs)]  
  
 Właściwości i metody wirtualne włączyć klasy pochodne rozszerzyć klasę podstawową bez konieczności korzystania z klasy podstawowej implementacji metody. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md). Interfejs zawiera inny sposób, aby zdefiniować metody lub zestaw metod, którego implementacja pozostało do klas pochodnych. Aby uzyskać więcej informacji, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Ukrywanie elementów członkowskich klasy podstawowej dla nowych członków  
 Jeśli chcesz pochodnej elementów członkowskich mają taką samą nazwę jak element członkowski w klasie podstawowej, ale nie chcesz brać udziału w wywołaniu wirtualnych, możesz użyć [nowe](../../../csharp/language-reference/keywords/new.md) — słowo kluczowe. `new` — Słowo kluczowe jest umieszczany przed zwracanym typem elementu członkowskiego klasy, który jest zastępowany. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_4.cs)]  
  
 Elementów członkowskich klasy podstawowej ukryte nadal będą dostępne z kodu klienta przez rzutowanie wystąpienie klasy pochodnej z wystąpieniem klasy podstawowej. Na przykład:  
  
 [!code-csharp[csProgGuideInheritance#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_5.cs)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Uniemożliwia zastępowanie wirtualne elementy członkowskie klasy pochodne  
 Wirtualne elementy członkowskie pozostają wirtualnych przez czas nieokreślony, niezależnie od tego, jak wiele klas zostały zgłoszone od wirtualny element członkowski i klasy, która pierwotnie zadeklarowana jako. Jeśli klasy A deklaruje elementu członkowskiego wirtualnego i klasy B pochodną A, a klasa C pochodzi z B, klasa C dziedziczy członka wirtualnego i włączono opcję, aby ją zastąpić, bez względu na to czy klasy B podana zastąpienia dla tego elementu członkowskiego. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_6.cs)]  
  
 Klasa pochodna można zatrzymać wirtualnego dziedziczenia przez zadeklarowanie zastąpienia jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md). Wymaga to wprowadzenia `sealed` przed `override` — słowo kluczowe w deklaracji elementu członkowskiego klasy. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_7.cs)]  
  
 W poprzednim przykładzie metoda `DoWork` nie jest już wirtualnych do dowolnej klasy pochodnej z C. Jest nadal wirtualnych dla wystąpień C, nawet jeśli są one rzutowane na typ B lub typu metody zapieczętowane A. może być zastąpiony klas pochodnych przy użyciu `new` — słowo kluczowe, jak przedstawiono na poniższym przykładzie:  
  
 [!code-csharp[csProgGuideInheritance#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_8.cs)]  
  
 W tym przypadku jeśli `DoWork` jest wywoływana na D przy użyciu zmiennej typu D, nowe `DoWork` jest wywoływana. Jeśli zmienna typu C B i A uzyskano dostęp wystąpienia D, wywołanie `DoWork` będzie zgodna z zasadami wirtualnego dziedziczenia routingu wywołań do implementacji `DoWork` klasy C.  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Uzyskiwanie dostępu do klasy podstawowej wirtualne elementy członkowskie z klasy pochodne  
 Klasy pochodnej, która została zastąpiona bądź przesłonięcia metody lub właściwości nadal mają dostęp do metody lub właściwości w klasie podstawowej za pomocą słowa kluczowego podstawowej. Poniższy kod stanowi przykład:  
  
 [!code-csharp[csProgGuideInheritance#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_9.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [podstawowej](../../../csharp/language-reference/keywords/base.md).  
  
> [!NOTE]
>  Zaleca się, że wirtualne elementy członkowskie używać `base` wywołać Implementacja klasy podstawowej ten element członkowski w realizacji. Umożliwienie wystąpić umożliwia klasy pochodnej w celu skoncentrować się na zachowanie klasa podstawowa implementacja zachowanie specyficzne dla klasy pochodnej. Jeśli Implementacja klasy podstawowej nie jest wywoływany, jest klasy pochodnej, aby zapewnić ich zachowania zgodność z zachowaniem klasy podstawowej.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
-   [Użycie przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
-   [Instrukcje: przesłonięcie metody ToString](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dziedziczenie](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)
