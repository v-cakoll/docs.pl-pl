---
title: Polimorfizm - Przewodnik programowania C#
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 58980bd0d70d8a778cdb208f56d31ee8465871a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170172"
---
# <a name="polymorphism-c-programming-guide"></a>Polimorfizm (Przewodnik programowania w języku C#)

Polimorfizm jest często określany jako trzeci filar programowania obiektowego, po hermetyzacji i dziedziczeniu. Polimorfizm jest greckie słowo, które oznacza "wielu kształtach" i ma dwa różne aspekty:
  
- W czasie wykonywania obiekty klasy pochodnej mogą być traktowane jako obiekty klasy podstawowej w miejscach, takich jak parametry metody i kolekcje lub tablice. Po wystąpieniu tego polimorfizmu zadeklarowany typ obiektu nie jest już identyczny z jego typem czasu wykonywania.
- Klasy podstawowe mogą definiować i implementować *metody* [wirtualne,](../../language-reference/keywords/virtual.md) a klasy pochodne mogą je [zastąpić,](../../language-reference/keywords/override.md) co oznacza, że zapewniają własną definicję i implementację. W czasie wykonywania, gdy kod klienta wywołuje metodę, środowisko CLR wyszukuje typ czasu wykonywania obiektu i wywołuje, że zastąpienie metody wirtualnej. W kodzie źródłowym można wywołać metodę w klasie podstawowej i spowodować, że wersja metody klasy pochodnej ma być wykonywana.

Metody wirtualne umożliwiają jednolitą pracę z grupami powiązanych obiektów. Załóżmy na przykład, że masz aplikację do rysowania, która umożliwia użytkownikowi tworzenie różnego rodzaju kształtów na powierzchni rysunku. Nie wiadomo w czasie kompilacji, które konkretne typy kształtów użytkownik utworzy. Jednak aplikacja musi śledzić wszystkie różne typy kształtów, które są tworzone i musi je zaktualizować w odpowiedzi na akcje myszy użytkownika. Możesz użyć polimorfizmu, aby rozwiązać ten problem w dwóch podstawowych krokach:

1. Utwórz hierarchię klas, w której każda klasa określonego kształtu pochodzi od wspólnej klasy podstawowej.
1. Użyj metody wirtualnej, aby wywołać odpowiednią metodę dla dowolnej klasy pochodnej za pośrednictwem pojedynczego wywołania metody klasy podstawowej.

Najpierw utwórz klasę `Shape`podstawową o nazwie `Rectangle`, `Circle`i `Triangle`klasy pochodne, takie jak , , i . Nadaj `Shape` klasie metodę `Draw`wirtualną o nazwie i zastąp ją w każdej klasie pochodnej, aby narysować określony kształt, który reprezentuje klasa. Utwórz `List<Shape>` obiekt i `Circle` `Triangle`dodaj `Rectangle` , i do niego.

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

Aby zaktualizować powierzchnię rysunku, użyj pętli [foreach](../../language-reference/keywords/foreach-in.md) do iteratezania listy i wywołania `Draw` metody na każdym `Shape` obiekcie na liście. Mimo że każdy obiekt na liście `Shape`ma zadeklarowany typ , jest to typ czasu wykonywania (zastąpiona wersja metody w każdej klasie pochodnej), który zostanie wywołany.

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

W języku C#, każdy typ jest polimorficzny, ponieważ <xref:System.Object>wszystkie typy, w tym typy zdefiniowane przez użytkownika, dziedziczą z .  

## <a name="polymorphism-overview"></a>Przegląd polimorfizmu

### <a name="virtual-members"></a>Członkowie wirtualni

Gdy klasa pochodna dziedziczy z klasy podstawowej, zyskuje wszystkie metody, pola, właściwości i zdarzenia klasy podstawowej. Projektant klasy pochodnej może różnych wyborów dla zachowania metod wirtualnych:

- Klasa pochodna może zastąpić członków wirtualnych w klasie podstawowej, definiując nowe zachowanie.
- Klasa pochodna dziedziczyć najbliższą metodę klasy podstawowej bez zastępowania go, zachowując istniejące zachowanie, ale umożliwiając dalsze pochodne klasy zastąpić metodę.
- Klasa pochodna może zdefiniować nową implementację niewirtualną tych elementów członkowskich, które ukrywają implementacje klasy podstawowej.

Klasa pochodna może zastąpić element członkowski klasy podstawowej tylko wtedy, gdy element członkowski klasy podstawowej jest zadeklarowany jako [wirtualny](../../language-reference/keywords/virtual.md) lub [abstrakcyjny.](../../language-reference/keywords/abstract.md) Element członkowski pochodne musi używać [override](../../language-reference/keywords/override.md) — słowo kluczowe, aby jawnie wskazać, że metoda jest przeznaczona do udziału w wywołaniu wirtualnym. Poniższy kod zawiera przykład:

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Pola nie mogą być wirtualne; tylko metody, właściwości, zdarzenia i indeksatory mogą być wirtualne. Gdy klasa pochodna zastępuje element członkowski virtual, ten element członkowski jest wywoływany nawet wtedy, gdy wystąpienie tej klasy jest dostępne jako wystąpienie klasy podstawowej. Poniższy kod zawiera przykład:

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Metody i właściwości wirtualne umożliwiają klasy pochodne, aby rozszerzyć klasę podstawową bez konieczności używania implementacji klasy podstawowej metody. Aby uzyskać więcej informacji, zobacz [Przechowywanie wersji przy pomocą słów kluczowych Zastępowania i Nowych](./versioning-with-the-override-and-new-keywords.md). Interfejs zapewnia inny sposób definiowania metody lub zestawu metod, których implementacja jest pozostawiona klasom pochodnym. Aby uzyskać więcej informacji, zobacz [Interfejsy](../interfaces/index.md).

### <a name="hide-base-class-members-with-new-members"></a>Ukrywanie członków klasy podstawowej z nowymi członkami

Jeśli chcesz, aby klasa pochodna miała element członkowski o tej samej nazwie co element członkowski w klasie podstawowej, możesz użyć [nowego](../../language-reference/keywords/new-modifier.md) słowa kluczowego, aby ukryć element członkowski klasy podstawowej. Słowo `new` kluczowe jest umieszczane przed zwracanym typem elementu członkowskiego klasy, który jest zastępowany. Poniższy kod zawiera przykład:

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

Ukryte elementy członkowskie klasy podstawowej mogą być dostępne z kodu klienta przez rzutowanie wystąpienia klasy pochodnej do wystąpienia klasy podstawowej. Przykład:

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a>Zapobiegaj zastępowaniu wirtualnych elementów członkowskich klas pochodnych  

Elementy członkowskie wirtualne pozostają wirtualne, niezależnie od tego, ile klas zostały zadeklarowane między elementem członkowskim wirtualnym i klasy, która pierwotnie zadeklarowała go. Jeśli `A` klasa deklaruje wirtualny element `B` członkowski, a `C` klasa `B`pochodzi `C` od `B` `A`, a klasa pochodzi od , klasa dziedziczy element członkowski wirtualny i może go zastąpić, niezależnie od tego, czy klasa zadeklarowała zastąpienie tego elementu członkowskiego. Poniższy kod zawiera przykład:

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

Klasa pochodna może zatrzymać dziedziczenie wirtualne, deklarując zastąpienie jako [zapieczętowane](../../language-reference/keywords/sealed.md). Zatrzymywanie dziedziczenia wymaga `override` umieszczenia słowa kluczowego `sealed` przed słowem kluczowym w deklaracji elementu członkowskiego klasy. Poniższy kod zawiera przykład:

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

W poprzednim przykładzie metoda `DoWork` nie jest już wirtualny do `C`żadnej klasy pochodzącej z . Jest to nadal wirtualne dla `C`wystąpień , nawet jeśli `B` są `A`one oddanych do typu lub typu . Metody zapieczętowane można zastąpić klasami pochodnymi za pomocą słowa kluczowego, `new` jak pokazano w poniższym przykładzie:

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

W takim przypadku, `DoWork` jeśli `D` jest wywoływana `D`przy `DoWork` użyciu zmiennej typu , nowy jest wywoływana. Jeśli zmienna `C`typu `B`, `A` lub jest używany `D`do uzyskania `DoWork` dostępu do wystąpienia , wywołanie będzie zgodne `DoWork` z `C`regułami dziedziczenia wirtualnego, routing tych wywołań do implementacji na klasy .

### <a name="access-base-class-virtual-members-from-derived-classes"></a>Dostęp do wirtualnych elementów członkowskich klasy podstawowej z klas pochodnych

Klasa pochodna, która zastąpiła lub zastąpiona metoda lub właściwość nadal może `base` uzyskać dostęp do metody lub właściwości w klasie podstawowej przy użyciu słowa kluczowego. Poniższy kod zawiera przykład:

```csharp
public class Base
{
    public virtual void DoWork() {/*...*/ }
}
public class Derived : Base
{
    public override void DoWork()
    {
        //Perform Derived's work here
        //...
        // Call DoWork on base class
        base.DoWork();
    }
}
```

Aby uzyskać więcej informacji, zobacz [podstawa](../../language-reference/keywords/base.md).

> [!NOTE]
> Zaleca się, że elementy `base` członkowskie wirtualne użyć do wywołania implementacji klasy podstawowej tego elementu członkowskiego w ich implementacji własnej. Pozwalając zachowanie klasy podstawowej występuje umożliwia klasy pochodnej skoncentrować się na implementowanie zachowanie specyficzne dla klasy pochodnej. Jeśli implementacja klasy podstawowej nie jest wywoływana, to do klasy pochodnej, aby ich zachowanie zgodne z zachowaniem klasy podstawowej.

## <a name="in-this-section"></a>W tej sekcji

- [Przechowywanie wersji przesłonięć i nowych słów kluczowych](./versioning-with-the-override-and-new-keywords.md)
- [Użycie zastępowania i nowych słów kluczowych](./knowing-when-to-use-override-and-new-keywords.md)
- [Jak zastąpić ToString metody](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Dziedziczenie](./inheritance.md)
- [Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](./abstract-and-sealed-classes-and-class-members.md)
- [Metody](./methods.md)
- [Zdarzenia](../events/index.md)
- [Właściwości](./properties.md)
- [Indexers](../indexers/index.md) (Indeksatory)
- [Typy](../types/index.md)
