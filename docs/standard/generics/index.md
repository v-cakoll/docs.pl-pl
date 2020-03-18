---
title: Typy ogólne w .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generic methods, type inference
- generics [.NET Framework], collections
- generic interfaces [.NET Framework]
- constructed generic types
- nested generic types
- generic type definitions
- generic classes [.NET Framework]
- generics [.NET Framework], interfaces
- generics [.NET Framework], about
- generics [.NET Framework]
- generic collections [.NET Framework]
- generic delegates [.NET Framework]
- generic type arguments
- generics [.NET Framework], delegates
- generics [.NET Framework], features
- constraints [.NET Framework]
- generic types
- generic type parameters
ms.assetid: 2994d786-c5c7-4666-ab23-4c83129fe39c
ms.openlocfilehash: 7f20e5108ad8bff602f5b761e65f093d987f2608
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156312"
---
# <a name="generics-in-net"></a>Typy ogólne w .NET

Rodzajowe umożliwiają dostosowanie metody, klasy, struktury lub interfejsu do dokładnego typu danych, na który działa. Na przykład zamiast <xref:System.Collections.Hashtable> używać klasy, która umożliwia klucze i wartości dowolnego <xref:System.Collections.Generic.Dictionary%602> typu, można użyć klasy ogólnej i określić typ dozwolony dla klucza i typ dozwolony dla wartości. Wśród korzyści z leków generycznych są zwiększone ponownego użycia kodu i bezpieczeństwa typu.  

## <a name="defining-and-using-generics"></a>Definiowanie i używanie leków ogólnych
 Rodzajowe są klasy, struktury, interfejsy i metody, które mają symbole zastępcze (parametry typu) dla jednego lub więcej typów, które przechowują lub używają. Klasa kolekcji rodzajowej może używać parametru typu jako symbolu zastępczego dla typu obiektów, które przechowuje; parametry typu są wyświetlane jako typy jego pól i typy parametrów jego metod. Metoda ogólna może używać jego parametr typu jako typ jego wartości zwracanej lub jako typ jednego z jego parametrów formalnych. Poniższy kod ilustruje prostą definicję klasy ogólnej.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Podczas tworzenia wystąpienia klasy ogólnej należy określić rzeczywiste typy, które mają zastąpić parametry typu. Ustanawia nową klasę rodzajową, określaną jako skonstruowana klasa ogólna, z wybranymi typami podstawionymi wszędzie, gdy pojawiają się parametry typu. Wynik jest klasy bezpieczne typu, który jest dostosowany do wyboru typów, jak pokazano w poniższym kodzie.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  

### <a name="generics-terminology"></a>Terminologia rodzajowa  
 Następujące terminy są używane do omawiania leków generycznych w .NET:  
  
- *Definicja typu ogólnego* jest deklaracją klasy, struktury lub interfejsu, która działa jako szablon, z symbolami zastępczymi dla typów, które mogą zawierać lub używać. Na przykład <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> klasa może zawierać dwa typy: klucze i wartości. Ponieważ definicja typu ogólnego jest tylko szablonem, nie można tworzyć wystąpień klasy, struktury lub interfejsu, który jest definicją typu ogólnego.  
  
- *Ogólne parametry typu*lub parametry typu są *symbolami zastępczymi*w definicji typu ogólnego lub metody. Typ <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ogólny ma dwa parametry `TKey` `TValue`typu i , które reprezentują typy jego kluczy i wartości.  
  
- *Skonstruowany typ rodzajowy*lub *typ konstruowany*jest wynikiem określania typów dla parametrów typu ogólnego definicji typu ogólnego.  
  
- Argument *typu ogólnego* jest dowolnym typem, który jest zastępowany parametrem typu ogólnego.  
  
- Termin *ogólny ogólny termin* obejmuje zarówno skonstruowane typy i definicje typów ogólnych.  
  
- *Kowariancja* i *kontrawariancja* parametrów typu ogólnego umożliwiają użycie skonstruowanych typów ogólnych, których argumenty typu są bardziej pochodne (kowariancja) lub mniej pochodne (contravariance) niż typ konstruowany obiekt docelowy. Kowariancja i kontrawariancja są zbiorczo określane jako *wariancja*. Aby uzyskać więcej informacji, zobacz [Kowariancja i wariancja](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
- *Ograniczenia* są limity umieszczone na parametrach typu ogólnego. Na przykład można ograniczyć parametr typu do <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> typów, które implementują interfejs ogólny, aby upewnić się, że można zamówić wystąpienia typu. Można również ograniczyć parametry typu do typów, które mają określoną klasę podstawową, które mają konstruktora bezparametrowego lub które są typami odwołań lub typami wartości. Użytkownicy typu ogólnego nie mogą zastąpić argumentów typu, które nie spełniają ograniczeń.  
  
- *Definicja metody ogólnej* jest metodą z dwiema listami parametrów: listą parametrów typu ogólnego i listą parametrów formalnych. Parametry typu mogą być wyświetlane jako typ zwracany lub jako typy parametrów formalnych, jak pokazano w poniższym kodzie.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Metody ogólne mogą być wyświetlane w typach ogólnych lub nieogólnych. Należy pamiętać, że metoda nie jest ogólny tylko dlatego, że należy do typu ogólnego, a nawet dlatego, że ma parametry formalne, których typy są parametrami ogólnymi typu otaczającego. Metoda jest ogólna tylko wtedy, gdy ma własną listę parametrów typu. W poniższym kodzie `G` tylko metoda jest ogólny.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
## <a name="advantages-and-disadvantages-of-generics"></a>Zalety i wady leków generycznych
 Istnieje wiele zalet korzystania z kolekcji ogólnych i delegatów:  
  
- Bezpieczeństwo typu. Rodzajowe przesunięcie obciążenia bezpieczeństwa typu z ciebie do kompilatora. Nie ma potrzeby pisania kodu do testowania dla prawidłowego typu danych, ponieważ jest wymuszany w czasie kompilacji. Zmniejsza się potrzeba rzutowania typu i możliwość błędów w czasie wykonywania.  
  
- Mniej kodu i kodu jest łatwiej ponownie używane. Nie ma potrzeby dziedziczenia z typu podstawowego i zastępowania elementów członkowskich. Na przykład <xref:System.Collections.Generic.LinkedList%601> jest gotowy do natychmiastowego użycia. Na przykład można utworzyć połączoną listę ciągów z następującą deklaracją zmiennej:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
- Lepsza wydajność. Typy kolekcji ogólnych zazwyczaj działają lepiej do przechowywania i manipulowania typami wartości, ponieważ nie ma potrzeby, aby pole typów wartości.  
  
- Delegaci rodzajowy włączyć wywołania wywołań wywołania oparte na typie bez konieczności tworzenia wielu klas delegata. Na przykład <xref:System.Predicate%601> ogólny delegat umożliwia utworzenie metody, która implementuje własne kryteria wyszukiwania dla określonego typu i <xref:System.Array> używać metody <xref:System.Array.Find%2A> <xref:System.Array.FindLast%2A>z <xref:System.Array.FindAll%2A>metodami typu, takimi jak , i .  
  
- Rodzajowe usprawnić dynamicznie generowany kod. Korzystając z typów ogólnych z dynamicznie generowanym kodem, nie trzeba generować tego typu. Zwiększa to liczbę scenariuszy, w których można użyć lekkich metod dynamicznych zamiast generowania całych zestawów. Aby uzyskać więcej informacji, zobacz [Jak: Definiowanie i wykonywanie metod dynamicznych](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) i <xref:System.Reflection.Emit.DynamicMethod>.  
  
 Oto pewne ograniczenia leków generycznych:  
  
- Typy ogólne mogą pochodzić z większości <xref:System.MarshalByRefObject> klas podstawowych, takich jak (i ograniczenia mogą być używane <xref:System.MarshalByRefObject>do wymagania, że ogólne parametry typu pochodzą z klas podstawowych, takich jak ). Jednak .NET Framework nie obsługuje typów ogólnych związanych z kontekstem. Typ ogólny można wyprowadzić z <xref:System.ContextBoundObject>, ale próba utworzenia <xref:System.TypeLoadException>wystąpienia tego typu powoduje .  
  
- Wyliczenia nie mogą mieć parametrów typu ogólnego. Wyliczenie może być ogólne tylko przypadkowo (na przykład, ponieważ jest zagnieżdżony w typogólny, który jest zdefiniowany przy użyciu języka Visual Basic, C#lub C++). Aby uzyskać więcej informacji, zobacz "Wyliczenia" w [systemie typu wspólnego](../../../docs/standard/base-types/common-type-system.md).  
  
- Lekkie metody dynamiczne nie mogą być ogólne.  
  
- W języku Visual Basic, C#i C++, zagnieżdżony typ, który jest ujęty w typ ogólny, nie może zostać uprzednio użyzczony, chyba że typy zostały przypisane do parametrów typu wszystkich typów otaczających. Innym sposobem na powiedzenie jest to, że w odbiciu, zagnieżdżony typ, który jest zdefiniowany przy użyciu tych języków zawiera parametry typu wszystkich jego typów otaczających. Dzięki temu parametry typu otaczającego typy mają być używane w definicjach elementów członkowskich typu zagnieżdżonego. Aby uzyskać więcej informacji, zobacz <xref:System.Type.MakeGenericType%2A>"Typy zagnieżdżone" w .  
  
    > [!NOTE]
    > Typ zagnieżdżony, który jest zdefiniowany przez emitowanie kodu w zestawie dynamicznym lub przy użyciu [Ilasm.exe (IL Asembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) nie jest wymagane do uwzględnienia parametrów typu jego otaczającego typów; jednak jeśli nie zawiera ich, parametry typu nie są w zakresie w klasie zagnieżdżonej.  
  
     Aby uzyskać więcej informacji, zobacz <xref:System.Type.MakeGenericType%2A>"Typy zagnieżdżone" w .  

## <a name="class-library-and-language-support"></a>Biblioteka klas i obsługa języków  
 .NET udostępnia szereg ogólnych klas kolekcji w następujących przestrzeniach nazw:  
  
- Obszar <xref:System.Collections.Generic> nazw zawiera większość typów kolekcji ogólnych dostarczonych <xref:System.Collections.Generic.List%601> przez <xref:System.Collections.Generic.Dictionary%602> .NET, takich jak i klas ogólnych.  
  
- Obszar <xref:System.Collections.ObjectModel> nazw zawiera dodatkowe typy kolekcji <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> rodzajowych, takich jak klasa ogólna, które są przydatne do ujawniania modeli obiektów dla użytkowników klas.  
  
 Ogólne interfejsy do implementowania porównań sortowania i równości są dostarczane w obszarze <xref:System> nazw, wraz z ogólnymi typami delegatów dla programów obsługi zdarzeń, konwersji i predykatów wyszukiwania.  
  
 Obsługa typów ogólnych została <xref:System.Reflection> dodana do obszaru nazw do badania <xref:System.Reflection.Emit> typów ogólnych i metod ogólnych, do emitowania zestawów dynamicznych, które zawierają typy ogólne i metody, a także do <xref:System.CodeDom> generowania wykresów źródłowych, które zawierają generycznych.  
  
 Czas wykonywania języka wspólnego zawiera nowe opcodes i prefiksy do obsługi <xref:System.Reflection.Emit.OpCodes.Stelem> <xref:System.Reflection.Emit.OpCodes.Ldelem>typów <xref:System.Reflection.Emit.OpCodes.Unbox_Any> <xref:System.Reflection.Emit.OpCodes.Constrained>ogólnych <xref:System.Reflection.Emit.OpCodes.Readonly>w języku pośrednim firmy Microsoft (MSIL), w tym , , , , i .  
  
 Visual C++, C# i Visual Basic zapewniają pełną obsługę definiowania i używania leków ogólnych. Aby uzyskać więcej informacji na temat obsługi języka, zobacz [Typy ogólne w języku Visual Basic](../../visual-basic/programming-guide/language-features/data-types/generic-types.md), Wprowadzenie do leków [ogólnych](../../csharp/programming-guide/generics/index.md)i [Omówienie typów ogólnych w języku Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp).

## <a name="nested-types-and-generics"></a>Typy zagnieżdżone i generyki  
 Typ, który jest zagnieżdżony w typie rodzajowym może zależeć od parametrów typu otaczającego typu ogólnego. Czas wykonywania języka wspólnego uważa zagnieżdżonych typów jest ogólny, nawet jeśli nie mają parametrów typu ogólnego własnych. Podczas tworzenia wystąpienia typu zagnieżdżonego należy określić argumenty typu dla wszystkich otaczających typów ogólnych.  

## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Kolekcje ogólne w .NET](../../../docs/standard/generics/collections.md)|Opisuje ogólne klasy kolekcji i inne typy ogólne w .NET.|  
|[Delegaty ogólne do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|Opisuje ogólnych delegatów dla konwersji, predykatów wyszukiwania i akcje, które mają być podjęte na elementy tablicy lub kolekcji.|  
|[Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)|Opisuje ogólne interfejsy, które zapewniają typowe funkcje dla rodzin typów ogólnych.|  
|[Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)|Opisuje kowariancję i kontrawariancję w parametrach typu ogólnego.|  
|[Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)|Zawiera podsumowanie informacji o właściwościach i scenariuszach użycia typów kolekcji w .NET, w tym typów ogólnych.|  
|[Kiedy należy używać kolekcji ogólnych](../../../docs/standard/collections/when-to-use-generic-collections.md)|Opisuje ogólne reguły określania, kiedy używać typów kolekcji rodzajowych.|  
|[Instrukcje: definiowanie typu ogólnego przy użyciu emisji odbicia](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|W tym artykule wyjaśniono, jak generować zestawy dynamiczne, które zawierają typy ogólne i metody.|  
|[Typy ogólne w języku Visual Basic](../../visual-basic/programming-guide/language-features/data-types/generic-types.md)|W tym artykule opisano funkcję rodzajową dla użytkowników języka Visual Basic, w tym tematy inkanderiów dotyczące używania i definiowania typów ogólnych.|  
|[Wprowadzenie do typów ogólnych](../../csharp/programming-guide/generics/index.md)|Zawiera omówienie definiowania i używania typów ogólnych dla użytkowników języka C#.|  
|[Przegląd typów ogólnych w Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp)|Opisuje funkcję rodzajowy dla użytkowników języka C++, w tym różnice między rodzajowymi i szablonami.|  

## <a name="reference"></a>Dokumentacja  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
