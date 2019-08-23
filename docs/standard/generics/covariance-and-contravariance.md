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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08e6458f0a14b78c6d05f706afa710931d60094a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948798"
---
# <a name="covariance-and-contravariance-in-generics"></a>Kowariancja i kontrawariancja w typach ogólnych
<a name="top"></a>Kowariancja i kontrawariancja są terminami, które odwołują się do możliwości użycia bardziej pochodnej typu (bardziej szczegółowe) lub mniej pochodnego typu (mniej specyficznego) niż pierwotnie określony. Parametry typu ogólnego obsługują kowariancję i kontrawariancję, aby umożliwić większą elastyczność przypisywania i używania typów ogólnych. W kontekście systemu typów kowariancja, kontrawariancja i inwariancja mają następujące definicje. Przykłady zakładają klasę bazową o `Base` nazwie i klasę pochodną `Derived`o nazwie.  
  
- `Covariance`  
  
     Umożliwia użycie bardziej pochodnej typu niż pierwotnie określony.  
  
     Do zmiennej typu `IEnumerable<Derived>` `IEnumerable(Of Derived)` można`IEnumerable<Base>`przypisać wystąpienie (w Visual Basic).  
  
- `Contravariance`  
  
     Umożliwia użycie bardziej ogólnego (mniej pochodnego) typu niż oryginalnie określony.  
  
     Do zmiennej typu `Action<Base>` `Action(Of Base)` można`Action<Derived>`przypisać wystąpienie (w Visual Basic).  
  
- `Invariance`  
  
     Oznacza, że można użyć tylko oryginalnie określonego typu, więc inwariantny parametr typu ogólnego nie jest ani kowariantny, ani kontrawariantny.  
  
     Nie można przypisać wystąpienia `List<Base>` (`List(Of Base)` w Visual Basic) do zmiennej typu `List<Derived>` lub odwrotnie.  
  
 Parametry typu współwariantowego umożliwiają tworzenie przypisań, które wyglądają podobnie jak zwykłe [polimorfizm](../../csharp/programming-guide/classes-and-structs/polymorphism.md), jak pokazano w poniższym kodzie.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 `List<Derived>` `IEnumerable<Derived>`Klasa implementuje interfejs, więc(`List(Of Derived)` w Visual Basic) implementuje. <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.List%601> Kowariantny parametr typu wykonuje resztę zadania.  
  
 Z drugiej strony, kontrawariancja wydaje się nielogiczna. Poniższy przykład tworzy delegata typu `Action<Base>` (`Action(Of Base)` w Visual Basic), a następnie przypisuje tego delegata do zmiennej typu `Action<Derived>`.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Wydaje się to wsteczne, ale jest to bezpieczny dla typów kod, który można skompilować i uruchomić. Wyrażenie lambda jest zgodne z delegatem, do którego jest przypisany, więc definiuje metodę, która przyjmuje jeden parametr typu `Base` i która nie zwraca wartości. Otrzymany delegat można przypisać do zmiennej typu `Action<Derived>` , ponieważ parametr `T` <xref:System.Action%601> typu delegata to kontrawariantne. Kod jest bezpieczny dla typów, ponieważ `T` określa typ parametru. Gdy delegat typu `Action<Base>` jest wywoływany tak, jakby był delegatem typu `Action<Derived>`, jego argument musi być typu `Derived`. Ten argument można zawsze bezpiecznie przekazywać do bazowej metody, ponieważ parametr metody jest typu `Base`.  
  
 Ogólnie, kowariantnego parametru typu można użyć jako typu zwracanego delegata, a kontrawariantnych parametrów typu można używać jako typów parametrów. Na przykład kowariantnych parametrów typu można używać jako typów zwracanych metod interfejsu, a kontrawariantnych parametrów typu można używać jako typów parametrów metod interfejsu.  
  
 Kowariancja i kontrawariancja są określane zbiorczo jako *WARIANCJA*. Parametr typu generycznego, który nie jest oznaczony jako kontrawariantne, jest określany jako *niezmienny*. Krótkie podsumowanie faktów na temat wariancji w środowisku uruchomieniowym języka wspólnego:  
  
- W .NET Framework 4, parametry typu Variant są ograniczone do ogólnego typu interfejsu i rodzajowego delegata.  
  
- Ogólny typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
- Wariancja dotyczy tylko typów referencyjnych; określenie typu wartości dla wariantnego parametru typu spowoduje, że parametr typu będzie inwariantny dla wynikowego skonstruowanego typu.  
  
- Wariancja nie dotyczy kombinacji delegatów. Oznacza to, że w przypadku dwóch delegatów `Action<Base>` typów`Action(Of Derived)` `Action<Derived>` i `Action(Of Base)` (i w Visual Basic) nie można połączyć drugiego delegata z pierwszym, mimo że wynikiem byłyby typ bezpieczny. WARIANCJA umożliwia przypisanie drugiego delegata do zmiennej typu `Action<Derived>`, ale Delegaty mogą łączyć się tylko wtedy, gdy ich typy pasują do siebie.  
  
 Kowariantne i kontrawariantne parametry typu szczegółowo opisano w następujących sekcjach:  
  
- [Interfejsy ogólne z parametrami typu współwariantowego](#InterfaceCovariantTypeParameters)  
  
- [Interfejsy ogólne z parametrami typu ogólnego kontrawariantne](#InterfaceCovariantTypeParameters)  
  
- [Delegaty ogólne z parametrami typu Variant](#DelegateVariantTypeParameters)  
  
- [Definiowanie ogólnych interfejsów i delegatów dla wariantów](#DefiningVariantTypeParameters)  
  
- [Lista typów ogólnego interfejsu i delegatów wariantów](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Interfejsy ogólne z kowariantnymi parametrami typu  
 Począwszy od .NET Framework 4, kilka ogólnych interfejsów ma parametry typu współwariantowego; na przykład: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>, i <xref:System.Linq.IGrouping%602>. Wszystkie parametry typu tych interfejsów są kowariantne, więc parametry typu są używane tylko dla typów zwracanych elementów członkowskich.  
  
 W poniższym przykładzie pokazano kowariantne parametry typu. W przykładzie zdefiniowano dwa typy `Base` : ma statyczną metodę `PrintBases` o nazwie, `IEnumerable<Base>` która`IEnumerable(Of Base)` przyjmuje (w Visual Basic) i drukuje elementy. `Derived`dziedziczy z `Base`. Przykład tworzy puste `List<Derived>` (`List(Of Derived)` w Visual Basic) i pokazuje, że ten typ może być przesłany do `PrintBases` i przypisany do zmiennej typu `IEnumerable<Base>` bez rzutowania. <xref:System.Collections.Generic.List%601>implementuje <xref:System.Collections.Generic.IEnumerable%601>, który ma jeden parametr typu współwariantowego. Parametr typu współwariantowego to powód, dla `IEnumerable<Derived>` którego wystąpienie może być używane `IEnumerable<Base>`zamiast.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Powrót do początku](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Interfejsy ogólne z kontrawariantnymi parametrami typu  
 Począwszy od .NET Framework 4, kilka interfejsów ogólnych ma parametry typu kontrawariantne; na przykład: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, i <xref:System.Collections.Generic.IEqualityComparer%601>. Te interfejsy mają tylko kontrawariantne parametry typu, więc te parametry typów są używane tyko jako typy parametrów w elementach członkowskich tych interfejsów.  
  
 W poniższym przykładzie pokazano kontrawariantne parametry typu. W przykładzie zdefiniowano abstrakcyjną`MustInherit` (w Visual Basic `Shape` ) klasę z `Area` właściwością. W przykładzie zdefiniowano `ShapeAreaComparer` również klasę implementującą `IComparer<Shape>` (`IComparer(Of Shape)` w Visual Basic). Implementacja <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> metody jest oparta na wartości `Area` właściwości, więc `ShapeAreaComparer` może być używana do sortowania `Shape` obiektów według obszaru.  
  
 Klasa dziedziczy `Shape` i przesłania`Area`. `Circle` <xref:System.Collections.Generic.SortedSet%601> Przykład tworzy `Circle` Obiekt przy użyciu konstruktora, który przyjmuje `IComparer<Circle>` (`IComparer(Of Circle)` w Visual Basic). Jednak zamiast przekazywania `IComparer<Circle>`, przykład `ShapeAreaComparer` przekazuje obiekt, który implementuje `IComparer<Shape>`. Przykład może przekazać funkcję porównującą mniej pochodnego typu (`Shape`), gdy kod wywołuje funkcję porównującą z bardziej pochodnym typem (`Circle`), ponieważ parametr <xref:System.Collections.Generic.IComparer%601> Type interfejsu generycznego to kontrawariantne.  
  
 Po dodaniu `Circle` nowego obiektu `SortedSet<Circle>`do, `IComparer<Shape>.Compare` `IComparer(Of Shape).Compare`Metoda( Metoda w Visual Basic) obiektujestwywoływanazakażdymrazem,gdynowyelementjestporównywanyzistniejącymelementem.`ShapeAreaComparer` Typ parametru metody (`Shape`) jest mniej pochodny niż typ, który jest przesyłany (`Circle`), więc wywołanie jest bezpieczne typu. Kontrawariancja umożliwia `ShapeAreaComparer` sortowanie kolekcji dowolnego typu pojedynczego, a także mieszany zbiór typów, które pochodzą od `Shape`.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Powrót do początku](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Delegaty ogólne z wariantnymi parametrami typu  
 W .NET Framework 4, `Func` delegatów generycznych, takich jak <xref:System.Func%602>, mają typy zwracające współwarianty i typy parametrów kontrawariantne. <xref:System.Action%602>Delegaty `Action` ogólne, takie jak, mają typy parametrów kontrawariantne. Oznacza to, że Delegaty mogą być przypisywane do zmiennych, które mają bardziej pochodne typy parametrów i (w przypadku `Func` delegatów ogólnych) mniej pochodne typy zwracane.  
  
> [!NOTE]
> Ostatni parametr `Func` typu ogólnego delegatów ogólnych określa typ wartości zwracanej w sygnaturze delegata. Jest to współwariant (`out` słowo kluczowe), natomiast inne parametry typu ogólnego to kontrawariantne (`in` słowo kluczowe).  
  
 Ilustruje to poniższy kod. Pierwszy fragment kodu definiuje klasę o nazwie `Base`, klasę o nazwie `Derived` , która dziedziczy `Base`, i inną klasę z `static` metodą (`Shared` w Visual Basic) o nazwie `MyMethod`. Metoda przyjmuje wystąpienie klasy `Base` i zwraca `Derived`wystąpienie. (Jeśli argument jest wystąpieniem `Derived`, `MyMethod` zwraca go; jeśli `Base`argument jest wystąpieniem, `MyMethod` zwraca nowe wystąpienie `Derived`.) W `Main()`programie przykład tworzy `Func<Base, Derived>` wystąpienie (`Func(Of Base, Derived)` w Visual Basic) reprezentujące `MyMethod`i zapisuje je w zmiennej `f1`.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Drugi fragment kodu pokazuje, że delegat można przypisać do zmiennej typu `Func<Base, Base>` (`Func(Of Base, Base)` w Visual Basic), ponieważ typ zwracany jest współwariantem.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Trzeci fragment kodu pokazuje, że delegat można przypisać do zmiennej typu `Func<Derived, Derived>` (`Func(Of Derived, Derived)` w Visual Basic), ponieważ typ parametru to kontrawariantne.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Ostatni fragment kodu pokazuje, że delegat może być przypisany do zmiennej typu `Func<Derived, Base>` (`Func(Of Derived, Base)` w Visual Basic), łącząc efekty typu parametru kontrawariantne i typu zwracanego przez typ Variant.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Wariancja w delegatach ogólnych i nieogólnych  
 W poprzednim kodzie sygnatura `MyMethod` dokładnie pasuje do sygnatury konstruowanego delegata generycznego: `Func<Base, Derived>` (`Func(Of Base, Derived)` w Visual Basic). W przykładzie pokazano, że ten delegat generyczny może być przechowywany w zmiennych lub parametrach metod, które mają bardziej pochodne typy parametrów i mniej pochodne typy zwracane, o ile wszystkie typy delegatów są zbudowane z ogólnego <xref:System.Func%602>typu delegata.  
  
 Jest to ważny punkt. Skutki kowariancji i kontrawariancja w parametrach typu delegatów ogólnych są podobne do efektów kowariancji i kontrawariancja w zwykłych powiązaniach delegatów (zobacz WARIANCJA [w delegatach (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Wariancja w delegatach ( Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)). Jednak wariancja w powiązaniach delegatów działa ze wszystkimi typami delegatów, a nie tylko z ogólnymi typami delegatów, które mają wariantne parametry typu. Co więcej wariancja w powiązaniach delegatów umożliwia powiązanie metody z dowolnym delegatem, który ma bardziej restrykcyjne typy parametrów i mniej restrykcyjny typ zwracany, podczas gdy przypisanie delegatów ogólnych działa tylko wtedy, gdy oba typy delegatów są konstruowane na podstawie jednej definicji typu ogólnego.  
  
 W poniższym przykładzie pokazano połączone efekty zastosowania wariancji w powiązaniu delegatów oraz zastosowania wariancji w parametrach typu ogólnego. W przykładzie zdefiniowano hierarchię typów, która zawiera trzy typy, od najmniej`Type1`pochodnych () do najbardziej`Type3`pochodnej (). `Type1` Wariancja w zwykłych powiązaniach delegatów służy do powiązania metody z typem parametru i `Type3` typem zwracanym delegata generycznego `Type2` z typem parametru i typem `Type2`zwracanym. Wynikowy Delegat ogólny jest następnie przypisywany do innej zmiennej, której typ delegata generycznego ma `Type3` parametr typu i zwracany `Type1`typ, przy użyciu kowariancji i kontrawariancja parametrów typu ogólnego. Drugie przypisanie wymaga, aby zarówno typ zmiennej, jak i typ delegata były skonstruowane z tej samej definicji typu ogólnego, w tym przypadku <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Powrót do początku](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definiowanie wariantów interfejsów i delegatów ogólnych  
 Począwszy od .NET Framework 4 Visual Basic i C# zawiera słowa kluczowe, które umożliwiają oznaczenie parametrów typu ogólnego interfejsów i delegatów jako współvariant lub kontrawariantne.  
  
> [!NOTE]
> Począwszy od programu .NET Framework 2.0 środowisko uruchomieniowe języka wspólnego obsługuje adnotacje dotyczące wariancji w parametrach typu ogólnego. Przed .NET Framework 4, jedynym sposobem zdefiniowania klasy generycznej, która ma te adnotacje, jest użycie języka pośredniego firmy Microsoft (MSIL), przez skompilowanie klasy z [Ilasm. exe (ASEMBLER Il)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) lub przez emitowanie jej w zestawie dynamicznym.  
  
 Wartość parametru typu współwariantowego jest oznaczona za `out` pomocą słowa`Out` kluczowego (słowo `+` kluczowe w Visual Basic, dla [asemblera MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Kowariantnego parametru typu można użyć jako wartości zwracanej metody, która należy do interfejsu, lub typu zwracanego delegata. Kowariantnego parametru typu nie można użyć jako ograniczenia typu ogólnego dla metod interfejsu.  
  
> [!NOTE]
> Jeśli metoda interfejsu ma parametr, który jest typem ogólnym delegatów, kowariantny parametr typu dla typu interfejsu może być używany w celu określenia kontrawariantnego parametru typu dla typu delegata.  
  
 Kontrawariantne parametr typu jest oznaczany `in` słowem kluczowym (`In` słowo kluczowe w `-` Visual Basic, dla [asemblera MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Kontrawariantnego parametru typu można użyć jako typu parametru metody, która należy do interfejsu, lub typu parametru delegata. Kontrawariantnego parametru typu można użyć jako ograniczenia typu ogólnego dla metody interfejsu.  
  
 Tylko typy interfejsów i typy delegatów mogą mieć wariantne parametry typu. Typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
 Programy Visual Basic i C# nie zezwalają na naruszanie reguł używania kowariantnych i kontrawariantnych parametrów typu oraz dodawanie adnotacji o kowariancji i kontrawariancji do parametrów typu dla typów innych niż interfejsy i delegaty. [Asembler MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md) nie wykonuje takich testów, ale <xref:System.TypeLoadException> jest zgłaszany w przypadku próby załadowania typu, który narusza zasady.  
  
 Aby uzyskać informacje i przykładowy kod, zobacz [Wariancje w interfejsachC#ogólnych ()](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i wariancje [w interfejsach ogólnych (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
 [Powrót do początku](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Lista wariantów ogólnych typów interfejsów i delegatów  
 W .NET Framework 4 następujące typy interfejsów i delegatów mają parametry typu współvariant i/lub kontrawariantne.  
  
|Typ|Kowariantne parametry typu|Kontrawariantne parametry typu|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601>do<xref:System.Action%6016>||Tak|  
|<xref:System.Comparison%601>||Yes|  
|<xref:System.Converter%602>|Yes|Yes|  
|<xref:System.Func%601>|Tak||  
|<xref:System.Func%602>do<xref:System.Func%6017>|Tak|Yes|  
|<xref:System.IComparable%601>||Yes|  
|<xref:System.Predicate%601>||Yes|  
|<xref:System.Collections.Generic.IComparer%601>||Yes|  
|<xref:System.Collections.Generic.IEnumerable%601>|Yes||  
|<xref:System.Collections.Generic.IEnumerator%601>|Yes||  
|<xref:System.Collections.Generic.IEqualityComparer%601>||Yes|  
|<xref:System.Linq.IGrouping%602>|Yes||  
|<xref:System.Linq.IOrderedEnumerable%601>|Yes||  
|<xref:System.Linq.IOrderedQueryable%601>|Yes||  
|<xref:System.Linq.IQueryable%601>|Tak||  
  
## <a name="see-also"></a>Zobacz także

- [Kowariancja i kontrawariancja (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kowariancja i kontrawariancja (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Wariancja w delegatach (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Wariancja w delegatach (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
