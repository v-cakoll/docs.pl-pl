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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e5aea783640a2aa2c9f4fa7754b9a3a435d1f13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579070"
---
# <a name="generics-in-net"></a>Typy ogólne w .NET

<a name="top"></a> Typy ogólne pozwalają dostosować metody, klasy, struktury lub interfejsu do typu dokładne dane, który działa na. Na przykład zamiast <xref:System.Collections.Hashtable> klasy, dzięki czemu klucze i wartości do być dowolnego typu, możesz użyć <xref:System.Collections.Generic.Dictionary%602> ogólne klasy i określ typu dozwolone dla klucza i dozwolona wartość. Zalety typów ogólnych należą od kodu zwiększenie bezpieczeństwa możliwość ponownego wykorzystania i typu.  
  
 Ten temat zawiera przegląd typów ogólnych w .NET oraz podsumowanie typów ogólnych lub metody. Ten temat zawiera następujące sekcje:  
  
-   [Definiowanie i użycie typów ogólnych](#defining_and_using_generics)  
  
-   [Terminologia ogólne](#generics_terminology)  
  
-   [Biblioteka klas i obsługa języków](#class_library_and_language_support)  
  
-   [Zagnieżdżone typy i typy ogólne](#nested_types_and_generics)  
  
-   [Tematy pokrewne](#related_topics)  
  
-   [Dokumentacja](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a>Definiowanie i użycie typów ogólnych  
 Typy ogólne są klasy, struktury, interfejsy i metody, które mają symbole zastępcze (parametry typu) dla co najmniej jednego z typów, które przechowywania lub użyj. Klasa kolekcji ogólnej użyć parametru typu jako symbol zastępczy dla typ obiektów, które zawiera; parametrów typu są wyświetlane jako typy pól i typy parametrów metody. Metoda ogólna może używać jej parametr typu jako typu zwracanych wartości lub typ jednego z jego parametrów formalnych. Poniższy kod ilustruje definicji klasy ogólnej proste.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Podczas tworzenia wystąpienia klasy generycznej, należy określić rzeczywiste typy do zastąpienia dla parametrów typu. W ten sposób ustanawiany nowej klasy ogólnej, określany jako skonstruowane klasy ogólnej, z Twojego wybranych typów zastąpione wszędzie, który pojawia się parametry typu. Wynik jest dostosowane do wybór typu, klasę bezpieczny, jak pokazano w poniższym kodzie.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a>Terminologia ogólne  
 Poniższe terminy są używane w celu omówienia typy ogólne w .NET:  
  
-   A *definicji typu ogólnego* jest klasą, strukturą lub deklaracji interfejsu, który działa jako szablon, z symbole zastępcze dla typów, które mogą zawierać, lub użyj. Na przykład <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> klasy może zawierać dwa typy: klucze i wartości. Ponieważ w definicji typu ogólnego jest tylko szablon, nie można utworzyć wystąpienia klasy, struktury lub interfejsu, który jest definicją typu ogólnego.  
  
-   *Parametry typu ogólnego*, lub *parametry typu*, symboli zastępczych w ogólnym typie lub metodzie definicji. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Typu ogólnego ma dwa parametry typu `TKey` i `TValue`, reprezentujące typów kluczy i wartości.  
  
-   A *skonstruować typu ogólnego*, lub *skonstruować typu*, jest wynikiem Określanie typów parametrów typu ogólnego definicji typu ogólnego.  
  
-   A *argumentu typu ogólnego* jest dowolnego typu, który zostanie zastąpiony dla parametru typu ogólnego.  
  
-   Ogólny termin *typu ogólnego* zawiera typy utworzone i definicje typu ogólnego.  
  
-   *Kowariancja* i *kontrawariancja* typu ogólnego parametry umożliwiają korzystanie utworzone typy ogólne, którego argumenty typu są bardziej pochodny (kowariancja) lub mniej pochodnego (kontrawariancja) niż docelowy wykonane Typ. Kowariancja i kontrawariancja są nazywane zbiorczo *wariancji*. Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
-   *Ograniczenia* są umieszczane ograniczenia dotyczące parametrów typu ogólnego. Można na przykład ograniczenie parametr typu do typów, które implementują <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interfejs ogólny, aby upewnić się, że wystąpień tego typu może zostać określona. Można również ograniczyć parametrów typu do typów, które mają konkretnej klasy podstawowej, który ma domyślnego konstruktora lub typów referencyjnych lub typów wartości. Użytkownicy typ ogólny nie może zastąpić argumentów typu, które nie spełnia ograniczenia.  
  
-   A *ogólną definicją metody* jest metoda o dwie listy parametrów: lista parametrów typu ogólnego oraz listę parametrów formalnych. Parametry typu może występować jako zwracany typ lub typy parametrów formalnych, jak przedstawiono na poniższym kodem.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Metody ogólne może występować w typach ogólnych lub nierodzajowe. Należy pamiętać, że metoda nie jest rodzajowa tak, ponieważ należy on do typu ogólnego, lub nawet w przypadku, ponieważ ma ona parametrów formalnych których typy są parametry ogólne typu otaczającego. Metody jest rodzajowy, tylko wtedy, gdy ma własną listę parametrów typu. W poniższym kodzie, jedyną metodą `G` jest rodzajowy.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
 [Powrót do początku](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a>Zalety i wady ogólne  
 Istnieje wiele zalet przy użyciu kolekcji i obiektów delegowanych:  
  
-   Bezpieczeństwo typu. Typy ogólne przesunięcie obciążenia zabezpieczenie typów z należy do kompilatora. Nie istnieje potrzeba do pisania kodu, aby przetestować dla typu danych, ponieważ jest wymuszone w czasie kompilacji. Zostały zredukowane potrzebę rzutowanie typów i możliwość wystąpienia błędów czasu wykonywania.  
  
-   Mniej kod i kod łatwiej jest ponownie. Nie istnieje potrzeba aby dziedziczyć z typu podstawowego i Zastąp elementy członkowskie. Na przykład <xref:System.Collections.Generic.LinkedList%601> jest gotowy do użycia. Na przykład można utworzyć połączonej listy ciągów następujące deklaracje zmiennych:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
-   Lepszą wydajność. Typy kolekcji ogólnych zazwyczaj działać lepiej do przechowywania i manipulowanie typy wartości, ponieważ nie istnieje potrzeba do pola typu wartości.  
  
-   Delegaty ogólne włączyć bezpieczny wywołań zwrotnych, bez konieczności tworzenia delegata wielu klas. Na przykład <xref:System.Predicate%601> Delegat ogólny umożliwia tworzenie metody, która implementuje swoje własne kryteria wyszukiwania dla określonego typu i metodę za pomocą metody <xref:System.Array> wpisz na przykład <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>, i <xref:System.Array.FindAll%2A> .  
  
-   Typy ogólne usprawnić dynamicznie wygenerowanego kodu. Jeśli używasz typów ogólnych z kodem dynamicznie generowanym zbędna, nie można wygenerować typu. Zwiększa liczbę scenariusze, w których można używać lekkie metod dynamicznych zamiast generowania całego zestawów. Aby uzyskać więcej informacji, zobacz porady: definiowanie i wykonywanie metod dynamicznych, jak i elementu DynamicMethod.  
  
 Poniżej przedstawiono niektóre ograniczenia ogólne:  
  
-   Typy rodzajowe mogą pochodzić z najczęściej klasy podstawowej, takie jak <xref:System.MarshalByRefObject> (i warunków ograniczających służy do wymagają, aby parametry typu ogólnego pochodzi od klasy podstawowe, takie jak <xref:System.MarshalByRefObject>). Jednak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie obsługuje typów ogólnych związane z kontekstem. Typ ogólny mogą pochodzić z <xref:System.ContextBoundObject>, ale próby utworzenia wystąpienia tego typu przyczyny <xref:System.TypeLoadException>.  
  
-   Wyliczenia nie mogą mieć parametrów typu ogólnego. Wyliczenie może być rodzajowy tylko okazjonalnie (na przykład dlatego że zostało zagnieżdżone w typie ogólnym, który jest zdefiniowany w języku Visual Basic, C# lub języka C++). Aby uzyskać więcej informacji, zobacz "Wyliczenia" w [Wspólny System typów](../../../docs/standard/base-types/common-type-system.md).  
  
-   Lekkie metody dynamiczne nie mogą być ogólne.  
  
-   W języku Visual Basic, C# i C++ typu zagnieżdżonego, która jest zawarta w typie podstawowym nie można utworzyć wystąpienia, chyba że przypisano typy z parametrami typu wszystkich typów otaczającej. Innymi słowy to jest w odbicia, typu zagnieżdżonego, które zdefiniowano przy użyciu tych językach zawiera parametry typu z jego typów otaczającej. Dzięki temu parametrów typu w otaczającej typów do użycia w definicji elementu członkowskiego typu zagnieżdżonego. Aby uzyskać więcej informacji, zobacz "Typy zagnieżdżone" w <xref:System.Type.MakeGenericType%2A>.  
  
    > [!NOTE]
    >  Zagnieżdżony typ zdefiniowany przez emitowanie kodu w zestawie dynamicznym lub za pomocą [Ilasm.exe (asembler IL)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) uwzględnia parametry typu typu otaczającego; nie jest wymagane, jeśli nie obejmują ich parametry typu nie są w zakresie klasy zagnieżdżonej.  
  
     Aby uzyskać więcej informacji, zobacz "Typy zagnieżdżone" w <xref:System.Type.MakeGenericType%2A>.  
  
 [Powrót do początku](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a>Biblioteka klas i obsługa języków  
 .NET oferuje następujące klasy rodzajowej kolekcji w następujących przestrzeni nazw:  
  
-   <xref:System.Collections.Generic> Przestrzeń nazw zawiera większość typy kolekcji ogólnych udostępniane przez .NET, takie jak <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602> klas rodzajowych.  
  
-   <xref:System.Collections.ObjectModel> Przestrzeń nazw zawiera typy kolekcji ogólnych dodatkowe, takie jak <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> klasy ogólnej, które są przydatne w przypadku udostępnianie modeli obiektów użytkownikom klas.  
  
 Interfejsy ogólne wykonania porównania sortowania i o równość znajdują się w <xref:System> przestrzeni nazw, wraz z ogólnych typów delegata obsługi zdarzeń, konwersje i predykatów wyszukiwania.  
  
 Dodano obsługę ogólne <xref:System.Reflection> przestrzeni nazw do badania typy ogólne i metody rodzajowe <xref:System.Reflection.Emit> emitowanie dynamicznych zestawów, które zawierają typy ogólne i metody i do <xref:System.CodeDom> generowania wykresy źródła zawierające ogólne.  
  
 Środowisko uruchomieniowe języka wspólnego udostępnia nowe kody operacji i prefiksy do obsługi typów ogólnych w języku pośrednim firmy Microsoft (MSIL), w tym <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>, i <xref:System.Reflection.Emit.OpCodes.Readonly>.  
  
 Visual C++, C# i Visual Basic wszystkie zapewniają pełną obsługę do definiowania i użycie typów ogólnych. Aby uzyskać więcej informacji na temat obsługi language, zobacz [typy ogólne w Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md), [wprowadzenie do typów ogólnych](~/docs/csharp/programming-guide/generics/introduction-to-generics.md), i [Przegląd typów ogólnych w programie Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp).  
  
 [Powrót do początku](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a>Zagnieżdżone typy i typy ogólne  
 Typ, który jest zagnieżdżony w typie ogólnym może zależeć od parametrów typu ogólnego typu otaczającego. Środowisko uruchomieniowe języka wspólnego uwzględnia typy zagnieżdżone, aby wartość była ogólna, nawet jeśli nie ma parametrów typu ogólnego we własnym. Podczas tworzenia wystąpienia typu zagnieżdżonego, należy określić argumentów typu dla wszystkich otaczającego typów ogólnych.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Kolekcje ogólne w .NET](../../../docs/standard/generics/collections.md)|W tym artykule opisano klasy rodzajowej kolekcji i innych typów ogólnych w .NET.|  
|[Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|W tym artykule opisano delegatów konwersje, predykatów wyszukiwania i działań podejmowanych w przypadku elementów tablicy lub kolekcji.|  
|[Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)|W tym artykule opisano interfejsach zapewniające często używane funkcje w rodzin typów ogólnych.|  
|[Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)|Opisuje Kowariancja i kontrawariancja w parametrach typu ogólnego.|  
|[Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)|Zawiera informacje podsumowania scenariusze użycia typów kolekcji w programie .NET, w tym typy ogólne i właściwości.|  
|[Kiedy należy używać kolekcji ogólnych](../../../docs/standard/collections/when-to-use-generic-collections.md)|W tym artykule opisano ogólne reguły do określania, kiedy należy używać kolekcji ogólnych typów.|  
|[Instrukcje: definiowanie typu ogólnego przy użyciu emisji odbicia](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Wyjaśniono, jak można wygenerować zestawów dynamicznych, które obejmują typy ogólne i metody.|  
|[Typy ogólne w Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)|Zawiera opis funkcji ogólne dla użytkowników programu Visual Basic, w tym — tematy porad dotyczących korzystania oraz definiowanie typów ogólnych.|  
|[Wprowadzenie do typów ogólnych](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)|Zawiera omówienie definiowanie i C# użytkowników przy użyciu typów ogólnych.|  
|[Przegląd typów ogólnych w Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp)|Zawiera opis funkcji ogólne dla użytkowników C++, w tym różnice między typy ogólne i szablony.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
  
 [Powrót do początku](#top)
