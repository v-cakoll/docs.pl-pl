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
ms.openlocfilehash: 104a0018896eb95255cf4054f9402ce5160b95f7
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584146"
---
# <a name="generics-in-net"></a>Typy ogólne w .NET

<a name="top"></a> Typy ogólne pozwalają dostosować metody, klasy, struktury lub interfejsu na typ dokładne dane, które działają. Na przykład, zamiast <xref:System.Collections.Hashtable> klasy, co pozwala klucze i wartości dowolnego typu, możesz użyć <xref:System.Collections.Generic.Dictionary%602> ogólne klasy, a następnie określ typ dozwolone dla klucza i typ, dozwolone wartości. Wśród zalety typów ogólnych są zwiększone kodu możliwość ponownego wykorzystania i bezpieczeństwo.  
  
 Ten temat zawiera przegląd typów ogólnych w programie .NET i podsumowanie typów ani metod ogólnych. Ten temat zawiera następujące sekcje:  
  
-   [Definiowanie i korzystanie z typów ogólnych](#defining_and_using_generics)  
  
-   [Terminologia typów ogólnych](#generics_terminology)  
  
-   [Biblioteka klas i obsługa języków](#class_library_and_language_support)  
  
-   [Zagnieżdżone typy i typy ogólne](#nested_types_and_generics)  
  
-   [Tematy pokrewne](#related_topics)  
  
-   [Dokumentacja](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a>Definiowanie i korzystanie z typów ogólnych  
 Typy ogólne są klasy, struktury, interfejsy i metody, które mają symboli zastępczych (parametry typu) dla jednego lub kilku typów, które mogą przechowywać lub używać. Klasy ogólne kolekcji użyć parametru typu jako symbol zastępczy dla typów obiektów, które przechowuje; Parametry typu są traktowane jako typy jej pola i typy parametrów jego metod. Jego parametru typu może użyć metody rodzajowej, jako typ wartości zwracanej lub typ jednego z jego parametrów formalnych. Poniższy kod przedstawia definicję klasy ogólnej proste.  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 Podczas tworzenia wystąpienia klasy generycznej, należy określić rzeczywiste typy podstawiane dla parametrów typu. Spowoduje to utworzenie nowej klasy ogólnej, określane jako klasę ogólną skonstruowany przy użyciu wybranych typów zastępowane wszędzie, które są wyświetlane parametry typu. Wynik jest klasą bezpieczny, dostosowane do wybranego typu, tak jak pokazano w poniższym kodzie.  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a>Terminologia typów ogólnych  
 Poniższe terminy są używane w celu omówienia ich typy ogólne w .NET:  
  
-   A *definicji typu ogólnego* klasy, struktury lub deklaracji interfejsu, który działa jako szablon przy użyciu symboli zastępczych dla typów, które mogą zawierać, lub użyć. Na przykład <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> klasy może zawierać dwa typy: klucze i wartości. Ponieważ tylko szablon, który znajduje się w definicji typu ogólnego, nie można utworzyć wystąpienia klasy, struktury lub interfejsu, który jest definicja typu ogólnego.  
  
-   *Parametry typu ogólnego*, lub *parametry typu*, jest symboli zastępczych w ogólne definicji typu lub metody. <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Typu ogólnego ma dwa parametry typu `TKey` i `TValue`, reprezentujące typy wartości i kluczy.  
  
-   A *skonstruowany typ rodzajowy*, lub *skonstruowany typ*, jest wynikiem Określanie typów dla parametrów typu genetycznego definicji typu ogólnego.  
  
-   A *argument typu ogólnego* jest dowolny typ, który zostanie zastąpiony dla parametru typu ogólnego.  
  
-   Ogólny termin *typu ogólnego* zawiera typy utworzone i definicji typu ogólnego.  
  
-   *Kowariancja* i *kontrawariancja* typu rodzajowego parametry umożliwiają korzystanie skonstruowany typów ogólnych, w której argumenty typu są bardziej pochodnego (korelacja) lub mniej pochodnego (kontrawariancja) niż docelowy skonstruowany Typ. Kowariancja i kontrawariancja są nazywane zbiorczo *wariancji*. Aby uzyskać więcej informacji, zobacz [kowariancji i kontrawariancji](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
-   *Ograniczenia* obowiązują limity dotyczące parametrów typu ogólnego. Na przykład może ograniczać parametr typu dla typów, które implementują <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> ogólny interfejs, aby upewnić się, czy wystąpienia typu, może zostać określona. Możesz również ograniczyć parametrów typu do typów, które mają konkretnej klasy podstawowej, która ma domyślnego konstruktora lub są typy odwołań i typy wartości. Użytkownicy typ ogólny nie może zastąpić argumentów typu, które nie spełniają ograniczeń.  
  
-   A *definicję metody ogólnej* jest metodą o dwie listy parametrów: lista parametrów typu genetycznego oraz listę parametrów formalnych. Parametry typu mogą być wyświetlane jako zwracany typ lub typy parametrów formalnych, co ilustruje poniższy kod.  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 Metody ogólne mogą być wyświetlane na ogólny lub nierodzajowymi typami. Należy zauważyć, że metoda nie jest ogólna, po prostu, ponieważ należy on do typu ogólnego lub nawet w przypadku, ponieważ ma ona parametrów formalnych których typy są parametrom typu otaczającego. Metoda jest ogólna tylko wtedy, gdy ma ona własną lista parametrów typu. W poniższym kodzie, tylko metoda `G` ogólnego.  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
 [Powrót do początku](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a>Wady i zalety typów ogólnych  
 Istnieje wiele zalet, używając kolekcji ogólnych i delegatach:  
  
-   Bezpieczeństwo typów. Typy ogólne przesunięcie obciążenia bezpieczeństwo typów ze strony użytkownika do kompilatora. Nie ma potrzeby pisania kodu do testowania na prawidłowy typ danych, ponieważ jest wymuszone w czasie kompilacji. Zostały zredukowane potrzebę rzutowanie typów i możliwość wystąpienia błędów czasu wykonywania.  
  
-   Mniej kodu i kodu łatwiej jest użyć ponownie. Nie ma potrzeby aby dziedziczyć z typu podstawowego, a także Przesłoń składowe. Na przykład <xref:System.Collections.Generic.LinkedList%601> jest gotowy do bezpośredniego użycia. Na przykład można utworzyć połączonej listy ciągów z następującą deklarację zmiennej:  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
-   Lepsza wydajność. Typy generyczne kolekcji ogólnie poprawienia do przechowywania i manipulowanie typów wartości, ponieważ nie ma potrzeby na polu typów wartości.  
  
-   Delegaci ogólni Włącz wywołania zwrotne bezpieczny, bez konieczności tworzenia delegata wielu klas. Na przykład <xref:System.Predicate%601> Delegat ogólny umożliwia tworzenie metody, która implementuje własne kryteria wyszukiwania dla danego typu i metodę za pomocą metody <xref:System.Array> wpisz na przykład <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>, i <xref:System.Array.FindAll%2A> .  
  
-   Typy ogólne Usprawnij dynamicznie generowanego kodu. Kiedy używasz typów ogólnych z dynamicznie generowanego kodu, nie trzeba wygenerować typu. Powoduje to zwiększenie liczby scenariuszy, w których można użyć uproszczone metod dynamicznych, zamiast generować całe zestawy. Aby uzyskać więcej informacji, zobacz [porady: definiowanie i wykonywanie metod dynamicznych](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md) i <xref:System.Reflection.Emit.DynamicMethod>.  
  
 Poniżej przedstawiono niektóre ograniczenia typów ogólnych:  
  
-   Typy rodzajowe mogą pochodzić z większości klas podstawowych, takich jak <xref:System.MarshalByRefObject> (i ograniczenia może służyć do wymagają, że parametry typu ogólnego pochodzić od klasy bazowej, takie jak <xref:System.MarshalByRefObject>). Jednak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie obsługuje typów ogólnych związane z kontekstem. Typ ogólny, mogą pochodzić z <xref:System.ContextBoundObject>, ale próba utworzenia instancji tego typu powoduje, że <xref:System.TypeLoadException>.  
  
-   Wyliczenia nie może mieć parametrów typu genetycznego. Wyliczenie może być ogólny tylko przy okazji (ponieważ na przykład, że zostało zagnieżdżone w typie ogólnym, która jest zdefiniowana za pomocą języka Visual Basic, C# lub C++). Aby uzyskać więcej informacji, zobacz "Wyliczenia" w [Wspólny System typów](../../../docs/standard/base-types/common-type-system.md).  
  
-   Uproszczone metody dynamiczne nie mogą być ogólne.  
  
-   W języku Visual Basic, C# i C++ zagnieżdżony typ, który jest ujęty w typie podstawowym nie można utworzyć wystąpienia, chyba że typy zostały przypisane do wszystkich typów otaczającej parametrów typu. Innym sposobem powiedzenia, to jest w odbiciu, zagnieżdżony typ, który jest zdefiniowany w tych językach zawiera parametry typu wszystkie jego typy otaczającej. Dzięki temu parametrów typu w otaczającej typów do użycia także w definicjach składowej typu zagnieżdżonego. Aby uzyskać więcej informacji, zobacz "Zagnieżdżone typy" w <xref:System.Type.MakeGenericType%2A>.  
  
    > [!NOTE]
    >  Zagnieżdżony typ, który jest zdefiniowany przez emitowanie kodu w zestawie dynamicznym lub za pomocą [Ilasm.exe (asembler IL)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) zawierają parametry typu otaczającego; nie jest wymagane, jeśli go nie ma ich parametrów typu nie są w zakresie klasy zagnieżdżonej.  
  
     Aby uzyskać więcej informacji, zobacz "Zagnieżdżone typy" w <xref:System.Type.MakeGenericType%2A>.  
  
 [Powrót do początku](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a>Biblioteka klas i obsługa języków  
 .NET oferuje pewną liczbę klasy kolekcji rodzajowej w następujących przestrzeni nazw:  
  
-   <xref:System.Collections.Generic> Przestrzeń nazw zawiera większość typów kolekcji ogólnej, dostarczone przez platformy .NET, takich jak <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602> klas ogólnych.  
  
-   <xref:System.Collections.ObjectModel> Przestrzeń nazw zawiera dodatkowe rodzajowych typów kolekcji, takie jak <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> klasy ogólnej, które są przydatne w wypadku ujawniania modele obiektów użytkowników klas.  
  
 Interfejsy ogólne dotyczące implementowania porównania sortowania i równości znajdują się w <xref:System> przestrzeni nazw, wraz z ogólnymi typami delegatów obsługi zdarzeń, konwersji i predykaty wyszukiwania.  
  
 Dodano obsługę typów ogólnych <xref:System.Reflection> przestrzeni nazw do badania typy ogólne i metody rodzajowe <xref:System.Reflection.Emit> dla emitowanie dynamicznych zestawów, które zawierają typy ogólne i metody i <xref:System.CodeDom> do generowania wykresów źródła które obejmują typy ogólne.  
  
 Środowisko uruchomieniowe języka wspólnego udostępnia nowe rozkazów i prefiksy do obsługi typów ogólnych w języka Microsoft intermediate language (MSIL), w tym <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>, i <xref:System.Reflection.Emit.OpCodes.Readonly>.  
  
 Visual C++, C# i Visual Basic wszystkich zapewniają pełną obsługę definiowania i za pomocą typów ogólnych. Aby uzyskać więcej informacji na temat obsługi języków, zobacz [typów ogólnych w Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md), [wprowadzenie do typów ogólnych](~/docs/csharp/programming-guide/generics/introduction-to-generics.md), i [Przegląd typów ogólnych w Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp).  
  
 [Powrót do początku](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a>Zagnieżdżone typy i typy ogólne  
 Typ, który jest zagnieżdżony w typie ogólnym może zależeć od parametrów typu ogólnego typu otaczającego. Środowisko uruchomieniowe języka wspólnego uwzględnia zagnieżdżonych typów do być rodzajowe, nawet jeśli nie mają parametrów typu rodzajowego, własnych. Podczas tworzenia wystąpienia typu zagnieżdżonego, należy określić argumentów typu dla wszystkich otaczających typów ogólnych.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Kolekcje ogólne w .NET](../../../docs/standard/generics/collections.md)|W tym artykule opisano klasy kolekcji rodzajowej i inne typy ogólne w .NET.|  
|[Delegaci ogólni do manipulowania tablicami i listami](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|W tym artykule opisano delegaci ogólni do konwersji, predykaty wyszukiwania i akcje do wykonania w przypadku elementów tablicy lub kolekcji.|  
|[Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)|W tym artykule opisano ogólne interfejsy, które udostępniają funkcje wspólne dla rodziny typów ogólnych.|  
|[Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)|W tym artykule opisano kowariancji i kontrawariancji w parametrach typu ogólnego.|  
|[Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)|Zawiera podsumowanie informacji o właściwości i scenariusze użycia typów kolekcji na platformie .NET, w tym typów ogólnych.|  
|[Kiedy należy używać kolekcji ogólnych](../../../docs/standard/collections/when-to-use-generic-collections.md)|W tym artykule opisano ogólne zasady ustalania, kiedy należy używać rodzajowych typów kolekcji.|  
|[Instrukcje: definiowanie typu ogólnego przy użyciu emisji odbicia](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Wyjaśnia, jak można wygenerować zestawów dynamicznych, które obejmują typy ogólne i metody.|  
|[Typy ogólne w Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)|Opis funkcji ogólne dla użytkowników programu Visual Basic, w tym tematów zawierających porady dotyczące korzystania z i definiowania typów ogólnych.|  
|[Wprowadzenie do typów ogólnych](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)|Zawiera omówienie definiowanie i używanie typów ogólnych dla użytkowników języka C#.|  
|[Przegląd typów ogólnych w Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp)|Opis funkcji ogólne dla użytkowników języka C++, włącznie z różnicami między typy ogólne i szablony.|  
  
<a name="reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
  
 [Powrót do początku](#top)
