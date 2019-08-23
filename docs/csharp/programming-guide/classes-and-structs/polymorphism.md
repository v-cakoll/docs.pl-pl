---
title: Polimorfizm — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: e98399ac49e70f9139281ab75947c4acaf2dee7c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922083"
---
# <a name="polymorphism-c-programming-guide"></a>Polimorfizm (Przewodnik programowania w języku C#)
Polimorfizm jest często określany jako trzeci filar programowania zorientowanego obiektowo po hermetyzacji i dziedziczeniu. Polimorfizm jest wyrazem greckim, który oznacza "wiele-kształt" i ma dwa odrębne aspekty:  
  
- W czasie wykonywania obiekty klasy pochodnej mogą być traktowane jako obiekty klasy bazowej w miejscach takich jak parametry metody i kolekcje lub tablice. W takim przypadku zadeklarowany typ obiektu nie jest już identyczny z typem jego czasu wykonywania.  
  
- Klasy bazowe mogą definiować i implementować *metody* [wirtualne](../../language-reference/keywords/virtual.md) , a klasy pochodne mogą je przesłonić, co oznacza, że zapewniają własne definicje i implementacje. [](../../language-reference/keywords/override.md) W czasie wykonywania, gdy kod klienta wywołuje metodę, środowisko CLR wyszukuje typ obiektu w czasie wykonywania i wywołuje przesłonięcie metody wirtualnej. W tym celu w kodzie źródłowym można wywołać metodę w klasie bazowej i spowodować, że ma zostać wykonana wersja klasy pochodnej.  
  
 Metody wirtualne umożliwiają współpracę z grupami powiązanych obiektów w jednolity sposób. Załóżmy na przykład, że masz aplikację do rysowania, która umożliwia użytkownikowi tworzenie różnych rodzajów kształtów na powierzchni rysunku. W czasie kompilacji, które są tworzone dla poszczególnych typów kształtów, użytkownik nie wie. Jednak aplikacja musi śledzić wszystkie różne typy tworzonych kształtów i musi je zaktualizować w odpowiedzi na akcje myszy wykonywane przez użytkownika. Można użyć polimorfizmu, aby rozwiązać ten problem w dwóch podstawowych krokach:  
  
1. Utwórz hierarchię klas, w której każda klasa określonego kształtu pochodzi ze wspólnej klasy bazowej.  
  
2. Użyj metody wirtualnej do wywołania odpowiedniej metody dla dowolnej klasy pochodnej za pomocą pojedynczego wywołania metody klasy bazowej.  
  
 Najpierw Utwórz klasę bazową o nazwie `Shape`i klasy pochodne, takie jak `Rectangle`, `Circle`, i `Triangle`. Nadaj klasie metodę wirtualną o nazwie `Draw`i Przesłoń ją w każdej klasie pochodnej, aby narysować określony kształt, który reprezentuje Klasa. `Shape` `List<Shape>` Utwórz obiekt i Dodaj okrąg, Trójkąt i prostokąt do niego. Aby zaktualizować powierzchnię rysowania, użyj pętli [foreach](../../language-reference/keywords/foreach-in.md) , aby wykonać iterację listy i wywołać `Draw` metodę dla każdego `Shape` obiektu na liście. Mimo że każdy obiekt na liście ma zadeklarowany typ `Shape`, jest typem czasu wykonywania (zastąpioną wersją metody w każdej klasie pochodnej), która zostanie wywołana.  
  
 [!code-csharp[csProgGuideInheritance#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#50)]  
  
 W C#programie każdy typ jest polimorficzny, ponieważ wszystkie typy, włącznie z typami zdefiniowanymi przez <xref:System.Object>użytkownika, dziedziczą z.  
  
## <a name="polymorphism-overview"></a>Omówienie polimorfizmu  
  
### <a name="virtual-members"></a>Wirtualne składowe  
 Gdy Klasa pochodna dziedziczy z klasy bazowej, uzyskuje wszystkie metody, pola, właściwości i zdarzenia klasy bazowej. Projektant klasy pochodnej może wybrać, czy należy  
  
- Przesłoń wirtualne elementy członkowskie w klasie bazowej,  
  
- Dziedzicz najbliższą metodę klasy bazowej bez jej przesłaniania  
  
- Zdefiniuj nową niewirtualną implementację tych elementów członkowskich, które ukrywają implementacje klas podstawowych  
  
 Klasa pochodna może przesłonić składową klasy bazowej tylko wtedy, gdy element członkowski klasy bazowej jest zadeklarowany jako [wirtualny](../../language-reference/keywords/virtual.md) lub [abstrakcyjny](../../language-reference/keywords/abstract.md). Pochodny element członkowski musi użyć słowa kluczowego [override](../../language-reference/keywords/override.md) , aby jawnie wskazać, że metoda ma uczestniczyć w wywołaniu wirtualnym. Poniższy kod zawiera przykład:  
  
 [!code-csharp[csProgGuideInheritance#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#20)]  
  
 Pola nie mogą być wirtualne; tylko metody, właściwości, zdarzenia i indeksatory mogą być wirtualne. Gdy Klasa pochodna przesłania wirtualną składową, ten element członkowski jest wywoływany nawet wtedy, gdy do wystąpienia tej klasy jest uzyskiwany dostęp jako wystąpienie klasy bazowej. Poniższy kod zawiera przykład:  
  
 [!code-csharp[csProgGuideInheritance#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#21)]  
  
 Metody wirtualne i właściwości umożliwiają klasom pochodnym poszerzanie klasy bazowej bez konieczności używania implementacji klasy bazowej metody. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji ze słowami kluczowymi override i New](./versioning-with-the-override-and-new-keywords.md). Interfejs zapewnia inny sposób definiowania metody lub zestawu metod, których implementacja pozostała do klas pochodnych. Więcej informacji znajdziesz w artykule [Interfejsy](../interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Ukrywanie członków klasy bazowej przy użyciu nowych członków  
 Jeśli element członkowski pochodna ma mieć taką samą nazwę jak element członkowski w klasie bazowej, ale nie chcesz, aby uczestniczył w wywołaniu wirtualnym, możesz użyć słowa kluczowego [New](../../language-reference/keywords/new-modifier.md) . `new` Słowo kluczowe jest umieszczane przed typem zwracanym elementu członkowskiego klasy, który jest zastępowany. Poniższy kod zawiera przykład:  
  
 [!code-csharp[csProgGuideInheritance#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#18)]  
  
 Do elementów członkowskich ukrytych klas podstawowych nadal można uzyskać dostęp z kodu klienta, Rzutowanie wystąpienia klasy pochodnej na wystąpienie klasy bazowej. Przykład:  
  
 [!code-csharp[csProgGuideInheritance#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#19)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Uniemożliwianie klas pochodnych przed zastępowaniem wirtualnych elementów członkowskich  
 Wirtualne elementy członkowskie pozostają na czas nieokreślony, niezależnie od tego, jak wiele klas zostało zadeklarowanych między wirtualną składową i klasą, która pierwotnie została zadeklarowana. Jeśli klasa A deklaruje wirtualną składową, a Klasa B pochodzi z, a Klasa C pochodzi od B, Klasa C dziedziczy do wirtualnego elementu członkowskiego i ma możliwość jego zastąpienia, niezależnie od tego, czy Klasa B deklaruje przesłonięcie dla tego elementu członkowskiego. Poniższy kod zawiera przykład:  
  
 [!code-csharp[csProgGuideInheritance#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#22)]  
  
 Klasa pochodna może zatrzymać Dziedziczenie wirtualne, deklarując przesłonięcie jako [Sealed](../../language-reference/keywords/sealed.md). Wymaga to umieszczenia `sealed` słowa kluczowego `override` przed słowem kluczowym w deklaracji składowej klasy. Poniższy kod zawiera przykład:  
  
 [!code-csharp[csProgGuideInheritance#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#24)]  
  
 W poprzednim przykładzie metoda `DoWork` nie jest już wirtualna dla żadnej klasy pochodnej języka C. Nadal jest ona wirtualna dla wystąpień C, nawet jeśli są one rzutowane do typu B lub typu A. zapieczętowane metody mogą zostać zastąpione przez klasy pochodne za pomocą `new` słowa kluczowego, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideInheritance#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#25)]  
  
 W tym przypadku, jeśli `DoWork` jest wywoływana w D przy użyciu zmiennej typu d, Nowa `DoWork` jest wywoływana. Jeśli zmienna typu C, B lub a jest używana w celu uzyskania dostępu do wystąpienia D, wywołanie `DoWork` zostanie zgodne z regułami dziedziczenia wirtualnego, a następnie rozsyła te wywołania do `DoWork` implementacji klasy C.  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Uzyskiwanie dostępu do wirtualnych elementów członkowskich klasy podstawowej z klas pochodnych  
 Klasa pochodna, która zastąpiła lub przesłonięta metodę lub właściwość, może nadal uzyskiwać dostęp do metody lub właściwości w `base` klasie podstawowej przy użyciu słowa kluczowego. Poniższy kod zawiera przykład:  
  
 [!code-csharp[csProgGuideInheritance#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#26)]  
  
 Aby uzyskać więcej informacji, zobacz temat [Base](../../language-reference/keywords/base.md).  
  
> [!NOTE]
> Zaleca się, aby wirtualne składowe `base` używały do wywoływania implementacji klasy bazowej tego elementu członkowskiego we własnej implementacji. Zezwolenie na zachowanie klasy bazowej umożliwia skoncentrowanie się na implementowaniu przez klasę pochodną zachowania związanego z klasą pochodną. Jeśli implementacja klasy bazowej nie jest wywoływana, jest do klasy pochodnej, aby ich zachowanie było zgodne z zachowaniem klasy bazowej.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
- [Przechowywanie wersji przesłonięć i nowych słów kluczowych](./versioning-with-the-override-and-new-keywords.md)  
  
- [Użycie przesłonięć i nowych słów kluczowych](./knowing-when-to-use-override-and-new-keywords.md)  
  
- [Instrukcje: Zastąp metodę ToString](./how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Dziedziczenie](./inheritance.md)
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](./abstract-and-sealed-classes-and-class-members.md)
- [Metody](./methods.md)
- [Zdarzenia](../events/index.md)
- [Właściwości](./properties.md)
- [Indeksatory](../indexers/index.md)
- [Typy](../types/index.md)
