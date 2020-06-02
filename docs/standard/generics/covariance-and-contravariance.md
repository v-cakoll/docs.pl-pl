---
title: Kowariancja i kontrawariancja w typach ogólnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics, covariance and contravariance
- generics, variance
- covariance and contravariance in generics
- generic type parameters
ms.assetid: 2678dc63-c7f9-4590-9ddc-0a4df684d42e
ms.openlocfilehash: b11b5fc93d9b7289e62d6abc9d3ca19027a107c5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287561"
---
# <a name="covariance-and-contravariance-in-generics"></a>Kowariancja i kontrawariancja w typach ogólnych
Kowariancja i kontrawariancja są terminami, które odwołują się do możliwości użycia bardziej pochodnej typu (bardziej szczegółowe) lub mniej pochodnego typu (mniej specyficznego) niż pierwotnie określony. Parametry typu ogólnego obsługują kowariancję i kontrawariancję, aby umożliwić większą elastyczność przypisywania i używania typów ogólnych. W kontekście systemu typów kowariancja, kontrawariancja i inwariancja mają następujące definicje. Przykłady zakładają klasę bazową o nazwie `Base` i klasę pochodną o nazwie `Derived` .  
  
- `Covariance`  
  
     Umożliwia użycie bardziej pochodnej typu niż pierwotnie określony.  
  
     Do zmiennej typu można przypisać wystąpienie `IEnumerable<Derived>` ( `IEnumerable(Of Derived)` w Visual Basic) `IEnumerable<Base>` .  
  
- `Contravariance`  
  
     Umożliwia użycie bardziej ogólnego (mniej pochodnego) typu niż oryginalnie określony.  
  
     Do zmiennej typu można przypisać wystąpienie `Action<Base>` ( `Action(Of Base)` w Visual Basic) `Action<Derived>` .  
  
- `Invariance`  
  
     Oznacza, że można użyć tylko oryginalnie określonego typu, więc inwariantny parametr typu ogólnego nie jest ani kowariantny, ani kontrawariantny.  
  
     Nie można przypisać wystąpienia `List<Base>` ( `List(Of Base)` w Visual Basic) do zmiennej typu `List<Derived>` lub odwrotnie.  
  
 Parametry typu współwariantowego umożliwiają tworzenie przypisań, które wyglądają podobnie jak zwykłe [polimorfizm](../../csharp/programming-guide/classes-and-structs/polymorphism.md), jak pokazano w poniższym kodzie.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601>Klasa implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs, więc `List<Derived>` ( `List(Of Derived)` w Visual Basic) implementuje `IEnumerable<Derived>` . Kowariantny parametr typu wykonuje resztę zadania.  
  
 Z drugiej strony, kontrawariancja wydaje się nielogiczna. Poniższy przykład tworzy delegata typu `Action<Base>` ( `Action(Of Base)` w Visual Basic), a następnie przypisuje tego delegata do zmiennej typu `Action<Derived>` .  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Wydaje się to wsteczne, ale jest to bezpieczny dla typów kod, który można skompilować i uruchomić. Wyrażenie lambda jest zgodne z delegatem, do którego jest przypisany, więc definiuje metodę, która przyjmuje jeden parametr typu `Base` i która nie zwraca wartości. Otrzymany delegat można przypisać do zmiennej typu, `Action<Derived>` ponieważ parametr typu `T` <xref:System.Action%601> delegata to kontrawariantne. Kod jest bezpieczny dla typów, ponieważ `T` określa typ parametru. Gdy delegat typu `Action<Base>` jest wywoływany tak, jakby był delegatem typu `Action<Derived>` , jego argument musi być typu `Derived` . Ten argument można zawsze bezpiecznie przekazywać do bazowej metody, ponieważ parametr metody jest typu `Base` .  
  
 Ogólnie, kowariantnego parametru typu można użyć jako typu zwracanego delegata, a kontrawariantnych parametrów typu można używać jako typów parametrów. Na przykład kowariantnych parametrów typu można używać jako typów zwracanych metod interfejsu, a kontrawariantnych parametrów typu można używać jako typów parametrów metod interfejsu.  
  
 Kowariancja i kontrawariancja są określane zbiorczo jako *WARIANCJA*. Parametr typu generycznego, który nie jest oznaczony jako kontrawariantne, jest określany jako *niezmienny*. Krótkie podsumowanie faktów na temat wariancji w środowisku uruchomieniowym języka wspólnego:  
  
- W .NET Framework 4, parametry typu Variant są ograniczone do ogólnego typu interfejsu i rodzajowego delegata.  
  
- Ogólny typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
- Wariancja dotyczy tylko typów referencyjnych; określenie typu wartości dla wariantnego parametru typu spowoduje, że parametr typu będzie inwariantny dla wynikowego skonstruowanego typu.  
  
- Wariancja nie dotyczy kombinacji delegatów. Oznacza to, że w przypadku dwóch delegatów typów `Action<Derived>` i `Action<Base>` ( `Action(Of Derived)` i `Action(Of Base)` w Visual Basic) nie można połączyć drugiego delegata z pierwszym, mimo że wynikiem byłyby typ bezpieczny. WARIANCJA umożliwia przypisanie drugiego delegata do zmiennej typu `Action<Derived>` , ale Delegaty mogą łączyć się tylko wtedy, gdy ich typy pasują do siebie.

<a name="InterfaceCovariantTypeParameters"></a>
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Interfejsy ogólne z kowariantnymi parametrami typu  
 Począwszy od .NET Framework 4, kilka ogólnych interfejsów ma parametry typu współwariantowego; na przykład: <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.Generic.IEnumerator%601> , <xref:System.Linq.IQueryable%601> , i <xref:System.Linq.IGrouping%602> . Wszystkie parametry typu tych interfejsów są kowariantne, więc parametry typu są używane tylko dla typów zwracanych elementów członkowskich.  
  
 W poniższym przykładzie pokazano kowariantne parametry typu. W przykładzie zdefiniowano dwa typy: `Base` ma statyczną metodę o nazwie `PrintBases` , która przyjmuje `IEnumerable<Base>` ( `IEnumerable(Of Base)` w Visual Basic) i drukuje elementy. `Derived`dziedziczy z `Base` . Przykład tworzy puste `List<Derived>` ( `List(Of Derived)` w Visual Basic) i pokazuje, że ten typ może być przesłany do `PrintBases` i przypisany do zmiennej typu `IEnumerable<Base>` bez rzutowania. <xref:System.Collections.Generic.List%601>implementuje <xref:System.Collections.Generic.IEnumerable%601> , który ma jeden parametr typu współwariantowego. Parametr typu współwariantowego to powód, dla którego wystąpienie `IEnumerable<Derived>` może być używane zamiast `IEnumerable<Base>` .  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Interfejsy ogólne z kontrawariantnymi parametrami typu  
 Począwszy od .NET Framework 4, kilka interfejsów ogólnych ma parametry typu kontrawariantne; na przykład: <xref:System.Collections.Generic.IComparer%601> , <xref:System.IComparable%601> , i <xref:System.Collections.Generic.IEqualityComparer%601> . Te interfejsy mają tylko kontrawariantne parametry typu, więc te parametry typów są używane tyko jako typy parametrów w elementach członkowskich tych interfejsów.  
  
 W poniższym przykładzie pokazano kontrawariantne parametry typu. W przykładzie zdefiniowano abstrakcyjną ( `MustInherit` w Visual Basic) `Shape` klasę z `Area` właściwością. W przykładzie zdefiniowano również `ShapeAreaComparer` klasę implementującą `IComparer<Shape>` ( `IComparer(Of Shape)` w Visual Basic). Implementacja <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> metody jest oparta na wartości `Area` właściwości, więc `ShapeAreaComparer` może być używana do sortowania `Shape` obiektów według obszaru.  
  
 `Circle`Klasa dziedziczy `Shape` i przesłania `Area` . Przykład tworzy <xref:System.Collections.Generic.SortedSet%601> `Circle` Obiekt przy użyciu konstruktora, który przyjmuje `IComparer<Circle>` ( `IComparer(Of Circle)` w Visual Basic). Jednak zamiast przekazywania `IComparer<Circle>` , przykład przekazuje `ShapeAreaComparer` obiekt, który implementuje `IComparer<Shape>` . Przykład może przekazać funkcję porównującą mniej pochodnego typu ( `Shape` ), gdy kod wywołuje funkcję porównującą z bardziej pochodnym typem ( `Circle` ), ponieważ parametr type <xref:System.Collections.Generic.IComparer%601> interfejsu generycznego to kontrawariantne.  
  
 Po `Circle` dodaniu nowego obiektu do `SortedSet<Circle>` , `IComparer<Shape>.Compare` Metoda ( `IComparer(Of Shape).Compare` Metoda w Visual Basic) `ShapeAreaComparer` obiektu jest wywoływana za każdym razem, gdy nowy element jest porównywany z istniejącym elementem. Typ parametru metody ( `Shape` ) jest mniej pochodny niż typ, który jest przesyłany ( `Circle` ), więc wywołanie jest bezpieczne typu. Kontrawariancja umożliwia `ShapeAreaComparer` Sortowanie kolekcji dowolnego typu pojedynczego, a także mieszany zbiór typów, które pochodzą od `Shape` .  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  

## <a name="generic-delegates-with-variant-type-parameters"></a>Delegaty ogólne z wariantnymi parametrami typu  
 W .NET Framework 4, `Func` delegatów generycznych, takich jak <xref:System.Func%602> , mają typy zwracające współwarianty i typy parametrów kontrawariantne. `Action`Delegaty ogólne, takie jak <xref:System.Action%602> , mają typy parametrów kontrawariantne. Oznacza to, że Delegaty mogą być przypisywane do zmiennych, które mają bardziej pochodne typy parametrów i (w przypadku `Func` delegatów ogólnych) mniej pochodne typy zwracane.  
  
> [!NOTE]
> Ostatni parametr typu ogólnego `Func` delegatów ogólnych określa typ wartości zwracanej w sygnaturze delegata. Jest to współwariant ( `out` słowo kluczowe), natomiast inne parametry typu ogólnego to kontrawariantne ( `in` słowo kluczowe).  
  
 Ilustruje to poniższy kod. Pierwszy fragment kodu definiuje klasę o nazwie `Base` , klasę o nazwie, `Derived` która dziedziczy `Base` , i inną klasę z `static` metodą ( `Shared` w Visual Basic) o nazwie `MyMethod` . Metoda przyjmuje wystąpienie klasy `Base` i zwraca wystąpienie `Derived` . (Jeśli argument jest wystąpieniem `Derived` , `MyMethod` zwraca go; Jeśli argument jest wystąpieniem `Base` , `MyMethod` zwraca nowe wystąpienie `Derived` .) W programie `Main()` przykład tworzy wystąpienie `Func<Base, Derived>` ( `Func(Of Base, Derived)` w Visual Basic) reprezentujące `MyMethod` i zapisuje je w zmiennej `f1` .  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Drugi fragment kodu pokazuje, że delegat można przypisać do zmiennej typu `Func<Base, Base>` ( `Func(Of Base, Base)` w Visual Basic), ponieważ typ zwracany jest współwariantem.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Trzeci fragment kodu pokazuje, że delegat można przypisać do zmiennej typu `Func<Derived, Derived>` ( `Func(Of Derived, Derived)` w Visual Basic), ponieważ typ parametru to kontrawariantne.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Ostatni fragment kodu pokazuje, że delegat może być przypisany do zmiennej typu `Func<Derived, Base>` ( `Func(Of Derived, Base)` w Visual Basic), łącząc efekty typu parametru kontrawariantne i typu zwracanego przez typ Variant.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Wariancja w delegatach ogólnych i nieogólnych  
 W poprzednim kodzie sygnatura `MyMethod` dokładnie pasuje do sygnatury konstruowanego delegata generycznego: `Func<Base, Derived>` ( `Func(Of Base, Derived)` w Visual Basic). W przykładzie pokazano, że ten delegat generyczny może być przechowywany w zmiennych lub parametrach metod, które mają bardziej pochodne typy parametrów i mniej pochodne typy zwracane, o ile wszystkie typy delegatów są zbudowane z ogólnego typu delegata <xref:System.Func%602> .  
  
 Jest to ważny punkt. Skutki kowariancji i kontrawariancja w parametrach typu delegatów ogólnych są podobne do efektów kowariancji i kontrawariancja w zwykłych powiązaniach delegatów (zobacz [Wariancja w delegatach (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Wariancja w delegatach (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)). Jednak wariancja w powiązaniach delegatów działa ze wszystkimi typami delegatów, a nie tylko z ogólnymi typami delegatów, które mają wariantne parametry typu. Co więcej wariancja w powiązaniach delegatów umożliwia powiązanie metody z dowolnym delegatem, który ma bardziej restrykcyjne typy parametrów i mniej restrykcyjny typ zwracany, podczas gdy przypisanie delegatów ogólnych działa tylko wtedy, gdy oba typy delegatów są konstruowane na podstawie jednej definicji typu ogólnego.  
  
 W poniższym przykładzie pokazano połączone efekty zastosowania wariancji w powiązaniu delegatów oraz zastosowania wariancji w parametrach typu ogólnego. W przykładzie zdefiniowano hierarchię typów, która zawiera trzy typy, od najmniej pochodnych ( `Type1` ) do najbardziej pochodnej ( `Type3` ). Wariancja w zwykłych powiązaniach delegatów służy do powiązania metody z typem parametru `Type1` i typem zwracanym `Type3` delegata generycznego z typem parametru `Type2` i typem zwracanym `Type2` . Wynikowy Delegat ogólny jest następnie przypisywany do innej zmiennej, której typ delegata generycznego ma parametr typu `Type3` i zwracany typ `Type1` , przy użyciu kowariancji i kontrawariancja parametrów typu ogólnego. Drugie przypisanie wymaga, aby zarówno typ zmiennej, jak i typ delegata były skonstruowane z tej samej definicji typu ogólnego, w tym przypadku <xref:System.Func%602> .  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  

## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definiowanie wariantów interfejsów i delegatów ogólnych
 Począwszy od .NET Framework 4, Visual Basic i C# mają słowa kluczowe, które umożliwiają oznaczenie parametrów typu ogólnego interfejsów i delegatów jako współvariant lub kontrawariantne.  
  
> [!NOTE]
> Począwszy od programu .NET Framework 2.0 środowisko uruchomieniowe języka wspólnego obsługuje adnotacje dotyczące wariancji w parametrach typu ogólnego. Przed .NET Framework 4, jedynym sposobem zdefiniowania klasy generycznej, która ma te adnotacje, jest użycie języka pośredniego firmy Microsoft (MSIL), przez skompilowanie klasy z [Ilasm. exe (ASEMBLER Il)](../../framework/tools/ilasm-exe-il-assembler.md) lub przez emitowanie jej w zestawie dynamicznym.  
  
 Wartość parametru typu współwariantowego jest oznaczona za pomocą `out` słowa kluczowego ( `Out` słowo kluczowe w Visual Basic, `+` dla [asemblera MSIL](../../framework/tools/ilasm-exe-il-assembler.md)). Kowariantnego parametru typu można użyć jako wartości zwracanej metody, która należy do interfejsu, lub typu zwracanego delegata. Kowariantnego parametru typu nie można użyć jako ograniczenia typu ogólnego dla metod interfejsu.  
  
> [!NOTE]
> Jeśli metoda interfejsu ma parametr, który jest typem ogólnym delegatów, kowariantny parametr typu dla typu interfejsu może być używany w celu określenia kontrawariantnego parametru typu dla typu delegata.  
  
 Kontrawariantne parametr typu jest oznaczany `in` słowem kluczowym ( `In` słowo kluczowe w Visual Basic, `-` dla [asemblera MSIL](../../framework/tools/ilasm-exe-il-assembler.md)). Kontrawariantnego parametru typu można użyć jako typu parametru metody, która należy do interfejsu, lub typu parametru delegata. Kontrawariantnego parametru typu można użyć jako ograniczenia typu ogólnego dla metody interfejsu.  
  
 Tylko typy interfejsów i typy delegatów mogą mieć wariantne parametry typu. Typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
 Programy Visual Basic i C# nie zezwalają na naruszanie reguł używania kowariantnych i kontrawariantnych parametrów typu oraz dodawanie adnotacji o kowariancji i kontrawariancji do parametrów typu dla typów innych niż interfejsy i delegaty. [Asembler MSIL](../../framework/tools/ilasm-exe-il-assembler.md) nie wykonuje takich testów, ale <xref:System.TypeLoadException> jest zgłaszany w przypadku próby załadowania typu, który narusza zasady.  
  
 Aby uzyskać informacje i przykładowy kod, zobacz [Wariancje w interfejsach ogólnych (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [Wariancje w interfejsach ogólnych (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  

## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Lista wariantów ogólnych typów interfejsów i delegatów
 W .NET Framework 4 następujące typy interfejsów i delegatów mają parametry typu współvariant i/lub kontrawariantne.  
  
|Typ|Kowariantne parametry typu|Kontrawariantne parametry typu|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601>do<xref:System.Action%6016>||Tak|  
|<xref:System.Comparison%601>||Tak|  
|<xref:System.Converter%602>|Tak|Tak|  
|<xref:System.Func%601>|Tak||  
|<xref:System.Func%602>do<xref:System.Func%6017>|Tak|Tak|  
|<xref:System.IComparable%601>||Tak|  
|<xref:System.Predicate%601>||Tak|  
|<xref:System.Collections.Generic.IComparer%601>||Tak|  
|<xref:System.Collections.Generic.IEnumerable%601>|Tak||  
|<xref:System.Collections.Generic.IEnumerator%601>|Tak||  
|<xref:System.Collections.Generic.IEqualityComparer%601>||Tak|  
|<xref:System.Linq.IGrouping%602>|Tak||  
|<xref:System.Linq.IOrderedEnumerable%601>|Tak||  
|<xref:System.Linq.IOrderedQueryable%601>|Tak||  
|<xref:System.Linq.IQueryable%601>|Tak||  
  
## <a name="see-also"></a>Zobacz także

- [Kowariancja i kontrawariancja (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kowariancja i kontrawariancja (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Wariancja w delegatach (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Wariancja w delegatach (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
