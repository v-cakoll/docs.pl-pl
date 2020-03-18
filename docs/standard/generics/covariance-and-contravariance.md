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
ms.openlocfilehash: 909b03588d2a41f667bfa117a5cecb420b125088
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708400"
---
# <a name="covariance-and-contravariance-in-generics"></a>Kowariancja i kontrawariancja w typach ogólnych
Kowariancja i kontrawariancja to terminy, które odnoszą się do możliwości używania typu bardziej pochodnego (bardziej szczegółowego) lub mniej pochodnego typu (mniej specyficznego) niż pierwotnie określono. Parametry typu ogólnego obsługują kowariancję i kontrawariancję, aby umożliwić większą elastyczność przypisywania i używania typów ogólnych. W kontekście systemu typów kowariancja, kontrawariancja i inwariancja mają następujące definicje. W przykładach przyjęto `Base` klasę podstawową o `Derived`nazwie i klasę pochodną o nazwie .  
  
- `Covariance`  
  
     Umożliwia użycie typu bardziej pochodnego niż pierwotnie określony.  
  
     Można przypisać wystąpienie `IEnumerable<Derived>` (w`IEnumerable(Of Derived)` języku Visual Basic) `IEnumerable<Base>`do zmiennej typu .  
  
- `Contravariance`  
  
     Umożliwia użycie bardziej ogólnego (mniej pochodnego) typu niż oryginalnie określony.  
  
     Można przypisać wystąpienie `Action<Base>` (w`Action(Of Base)` języku Visual Basic) `Action<Derived>`do zmiennej typu .  
  
- `Invariance`  
  
     Oznacza, że można użyć tylko oryginalnie określonego typu, więc inwariantny parametr typu ogólnego nie jest ani kowariantny, ani kontrawariantny.  
  
     Nie można przypisać wystąpienia `List<Base>` `List(Of Base)` (w języku Visual Basic) do zmiennej typu `List<Derived>` lub odwrotnie.  
  
 Parametry typu kowariantnego umożliwiają wykonywanie przypisań, które wyglądają podobnie do zwykłego [polimorfizmu,](../../csharp/programming-guide/classes-and-structs/polymorphism.md)jak pokazano w poniższym kodzie.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 Klasa <xref:System.Collections.Generic.List%601> implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs, `List<Derived>` więc`List(Of Derived)` (w języku `IEnumerable<Derived>`Visual Basic) implementuje . Kowariantny parametr typu wykonuje resztę zadania.  
  
 Z drugiej strony, kontrawariancja wydaje się nielogiczna. Poniższy przykład tworzy delegata `Action<Base>` typu`Action(Of Base)` (w języku Visual Basic), a następnie `Action<Derived>`przypisuje tego delegata do zmiennej typu .  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Wydaje się to wsteczne, ale jest to bezpieczny dla typów kod, który można skompilować i uruchomić. Wyrażenie lambda pasuje do delegata, do której jest przypisany, więc `Base` definiuje metodę, która przyjmuje jeden parametr typu i która nie ma wartości zwracanej. Wynikowy delegat można przypisać do zmiennej `Action<Derived>` typu, ponieważ `T` parametr <xref:System.Action%601> typu delegata jest zmienny. Kod jest bezpieczny dla `T` typu, ponieważ określa typ parametru. Gdy delegat typu `Action<Base>` jest wywoływany tak, jakby był `Action<Derived>`pełnomocnikiem typu, jego `Derived`argument musi być typu . Ten argument zawsze można bezpiecznie przekazać do metody podstawowej, ponieważ `Base`parametr metody jest typu .  
  
 Ogólnie, kowariantnego parametru typu można użyć jako typu zwracanego delegata, a kontrawariantnych parametrów typu można używać jako typów parametrów. Na przykład kowariantnych parametrów typu można używać jako typów zwracanych metod interfejsu, a kontrawariantnych parametrów typu można używać jako typów parametrów metod interfejsu.  
  
 Kowariancja i kontrawariancja są zbiorczo określane jako *wariancja*. Parametr typu ogólnego, który nie jest oznaczony jako kowariantny lub kontrawariantny, jest określany jako *niezmienny.* Krótkie podsumowanie faktów na temat wariancji w środowisku uruchomieniowym języka wspólnego:  
  
- W .NET Framework 4 parametry typu wariantu są ograniczone do ogólnych typów interfejsu i delegatów ogólnych.  
  
- Ogólny typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
- Wariancja dotyczy tylko typów referencyjnych; określenie typu wartości dla wariantnego parametru typu spowoduje, że parametr typu będzie inwariantny dla wynikowego skonstruowanego typu.  
  
- Wariancja nie dotyczy kombinacji delegatów. Oznacza to, że biorąc `Action<Derived>` `Action<Base>` pod`Action(Of Derived)` `Action(Of Base)` uwagę dwóch delegatów typów i ( i w języku Visual Basic), nie można połączyć drugiego delegata z pierwszym chociaż wynik będzie typu bezpieczne. Wariancja umożliwia drugiemu delegatowi przypisanie do `Action<Derived>`zmiennej typu, ale pełnomocnicy mogą łączyć tylko wtedy, gdy ich typy są dokładnie zgodne.

<a name="InterfaceCovariantTypeParameters"></a>
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Interfejsy ogólne z kowariantnymi parametrami typu  
 Począwszy od .NET Framework 4, kilka ogólnych interfejsów mają parametry typu kowariantnego; na <xref:System.Collections.Generic.IEnumerable%601>przykład: <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Linq.IQueryable%601>, <xref:System.Linq.IGrouping%602>, i . Wszystkie parametry typu tych interfejsów są kowariantne, więc parametry typu są używane tylko dla typów zwracanych elementów członkowskich.  
  
 W poniższym przykładzie pokazano kowariantne parametry typu. W przykładzie definiuje dwa `Base` typy: ma `PrintBases` metodę `IEnumerable<Base>` statyczną o nazwie, która przyjmuje (`IEnumerable(Of Base)` w języku Visual Basic) i drukuje elementy. `Derived`dziedziczy `Base`z . W przykładzie tworzy `List<Derived>` `List(Of Derived)` pusty (w języku Visual Basic) i `PrintBases` pokazuje, że ten `IEnumerable<Base>` typ może być przekazywany do zmiennej typu bez rzutowania i przypisane do zmiennej typu. <xref:System.Collections.Generic.List%601>implementuje <xref:System.Collections.Generic.IEnumerable%601>, który ma jeden parametr typu kowariantowego. Parametr typu kowariantnego jest przyczyną, `IEnumerable<Derived>` dlaczego można `IEnumerable<Base>`użyć wystąpienia zamiast .  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Interfejsy ogólne z kontrawariantnymi parametrami typu  
 Począwszy od .NET Framework 4, kilka ogólnych interfejsów mają parametry typu kontrawariantnego; na <xref:System.Collections.Generic.IComparer%601>przykład: <xref:System.IComparable%601>, <xref:System.Collections.Generic.IEqualityComparer%601>, i . Te interfejsy mają tylko kontrawariantne parametry typu, więc te parametry typów są używane tyko jako typy parametrów w elementach członkowskich tych interfejsów.  
  
 W poniższym przykładzie pokazano kontrawariantne parametry typu. W przykładzie definiuje abstrakcyjne`MustInherit` (w `Shape` języku `Area` Visual Basic) klasy z właściwością. W przykładzie zdefiniowano również `ShapeAreaComparer` `IComparer<Shape>` klasę, która implementuje (`IComparer(Of Shape)` w języku Visual Basic). Implementacja <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> metody jest oparta na wartości `Area` właściwości, `ShapeAreaComparer` więc może `Shape` służyć do sortowania obiektów według obszaru.  
  
 Klasa `Circle` dziedziczy `Shape` i `Area`zastępuje . W przykładzie <xref:System.Collections.Generic.SortedSet%601> tworzy `Circle` obiektów, przy użyciu konstruktora, który ma ( `IComparer<Circle>` `IComparer(Of Circle)` w języku Visual Basic). Jednak zamiast przekazywania `IComparer<Circle>`, przykład przekazuje `ShapeAreaComparer` obiekt, który `IComparer<Shape>`implementuje . Przykład można przekazać moduł porównujący typu`Shape`mniej pochodne ( ), gdy kod wywołuje dla`Circle`porównania typu bardziej <xref:System.Collections.Generic.IComparer%601> pochodne ( ), ponieważ parametr typu interfejsu ogólnego jest kontrawariant.  
  
 Po `Circle` dodaniu nowego obiektu `SortedSet<Circle>`do `IComparer<Shape>.Compare` ,`IComparer(Of Shape).Compare` metoda (metoda w `ShapeAreaComparer` języku Visual Basic) obiektu jest wywoływana za każdym razem, gdy nowy element jest porównywany do istniejącego elementu. Typ parametru metody`Shape`( ) jest mniej pochodny niż`Circle`typ, który jest przekazywany ( ), więc wywołanie jest bezpieczne. Contravariance `ShapeAreaComparer` umożliwia sortowanie kolekcji dowolnego pojedynczego typu, a także mieszanekolekcji `Shape`typów, które pochodzą z .  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  

## <a name="generic-delegates-with-variant-type-parameters"></a>Delegaty ogólne z wariantnymi parametrami typu  
 W .NET Framework 4 `Func` ogólnych delegatów, takich jak <xref:System.Func%602>, mają typy zwrotów kowariantycznych i typy parametrów kontrawariantne. Delegaci `Action` rodzajowi, na przykład <xref:System.Action%602>, mają typy parametrów kontrawariantne. Oznacza to, że delegatów można przypisać do zmiennych, które mają więcej `Func` pochodnych typów parametrów i (w przypadku delegatów ogólnych) mniej pochodnych typów zwracanych.  
  
> [!NOTE]
> Ostatni parametr typu ogólnego `Func` delegatów ogólnych określa typ wartości zwracanej w podpisie delegata. Jest kowariant`out` (słowo kluczowe), podczas gdy inne ogólne parametry`in` typu są kontrawariantne (słowo kluczowe).  
  
 Ilustruje to poniższy kod. Pierwszy fragment kodu definiuje klasę `Base`o nazwie `Derived` , klasę `Base`o nazwie dziedziczy`Shared` , a `MyMethod`inną klasę z metodą (w języku `static` Visual Basic) o nazwie . Metoda przyjmuje wystąpienie `Base` i zwraca wystąpienie `Derived`. (Jeśli argument `Derived`jest wystąpieniem `MyMethod` , zwraca go; jeśli `Base`argument `MyMethod` jest wystąpieniem `Derived`, zwraca nowe wystąpienie .) W `Main()`przykładzie tworzy wystąpienie `Func<Base, Derived>` (`Func(Of Base, Derived)` w języku Visual `MyMethod`Basic), który reprezentuje `f1`i przechowuje go w zmiennej .  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Drugi fragment kodu pokazuje, że delegat a plik może `Func<Base, Base>` być`Func(Of Base, Base)` przypisany do zmiennej typu (w języku Visual Basic), ponieważ typ zwracany jest kowarianty.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Trzeci fragment kodu pokazuje, że delegat aplikator może `Func<Derived, Derived>` `Func(Of Derived, Derived)` być przypisany do zmiennej typu (w języku Visual Basic), ponieważ typ parametru jest kontrawariantny.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Ostatni fragment kodu pokazuje, że delegat może być przypisany do zmiennej typu `Func<Derived, Base>` (w`Func(Of Derived, Base)` języku Visual Basic), łącząc efekty typu parametru kontrawariantnego i typu zwrotu kowariantowego.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Wariancja w delegatach ogólnych i nieogólnych  
 W poprzednim kodzie podpis `MyMethod` dokładnie pasuje do podpisu skonstruowanego delegata ogólnego: `Func<Base, Derived>` (`Func(Of Base, Derived)` w języku Visual Basic). W przykładzie pokazano, że ten ogólny delegat mogą być przechowywane w zmiennych lub parametrów metody, które mają więcej pochodnych typów parametrów i <xref:System.Func%602>mniej pochodnych typów zwracanych, tak długo, jak wszystkie typy delegata są konstruowane z ogólnego typu delegata .  
  
 Jest to ważny punkt. Skutki kowariancji i kontrawariancji w parametrach typu ogólnych delegatów są podobne do skutków kowariancji i kontrawaracji w zwykłym powiązaniu delegata (zobacz [Wariancja w delegatach (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Wariancja w delegatach (Visual Basic).](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) Jednak wariancja w powiązaniach delegatów działa ze wszystkimi typami delegatów, a nie tylko z ogólnymi typami delegatów, które mają wariantne parametry typu. Co więcej wariancja w powiązaniach delegatów umożliwia powiązanie metody z dowolnym delegatem, który ma bardziej restrykcyjne typy parametrów i mniej restrykcyjny typ zwracany, podczas gdy przypisanie delegatów ogólnych działa tylko wtedy, gdy oba typy delegatów są konstruowane na podstawie jednej definicji typu ogólnego.  
  
 W poniższym przykładzie pokazano połączone efekty zastosowania wariancji w powiązaniu delegatów oraz zastosowania wariancji w parametrach typu ogólnego. W przykładzie definiuje hierarchię typów, która zawiera trzy`Type1`typy, od`Type3`najmniej pochodnych ( ) do większości pochodnych ( ). Wariancja w zwykłym powiązaniu delegata jest używana do `Type1` powiązania metody `Type3` z typem parametru i `Type2` typem zwracanym `Type2`do ogólnego delegata z typem parametru i zwracanym typem . Wynikowy delegat ogólny jest następnie przypisywany do innej zmiennej, której `Type3` ogólny typ `Type1`delegata ma parametr typu i zwracany typ , przy użyciu kowariancji i przeciwwariancji parametrów typu ogólnego. Drugie przypisanie wymaga, aby zarówno typ zmiennej, jak i typ delegata <xref:System.Func%602>były konstruowane z tej samej definicji typu ogólnego, w tym przypadku .  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  

## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definiowanie wariantów interfejsów i delegatów ogólnych
 Począwszy od .NET Framework 4, Visual Basic i C# mają słowa kluczowe, które umożliwiają oznaczenie ogólnych parametrów typu interfejsów i delegatów jako kowariantne lub kontrawariantne.  
  
> [!NOTE]
> Począwszy od programu .NET Framework 2.0 środowisko uruchomieniowe języka wspólnego obsługuje adnotacje dotyczące wariancji w parametrach typu ogólnego. Przed .NET Framework 4 jedynym sposobem definiowania klasy ogólnej, która ma te adnotacje jest użycie języka pośredniego firmy Microsoft (MSIL), albo przez skompilowanie klasy z [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) lub przez emitowanie go w dynamicznym zestawie.  
  
 Parametr typu kowariantowego jest `out` oznaczony`Out` słowem kluczowym `+` (słowo kluczowe w języku Visual Basic, dla [asemblera MSIL).](../../../docs/framework/tools/ilasm-exe-il-assembler.md) Kowariantnego parametru typu można użyć jako wartości zwracanej metody, która należy do interfejsu, lub typu zwracanego delegata. Kowariantnego parametru typu nie można użyć jako ograniczenia typu ogólnego dla metod interfejsu.  
  
> [!NOTE]
> Jeśli metoda interfejsu ma parametr, który jest typem ogólnym delegatów, kowariantny parametr typu dla typu interfejsu może być używany w celu określenia kontrawariantnego parametru typu dla typu delegata.  
  
 Parametr typu kontrawariantnego jest `in` oznaczony`In` słowem kluczowym (słowo kluczowe w języku Visual Basic, `-` dla [asemblera MSIL).](../../../docs/framework/tools/ilasm-exe-il-assembler.md) Kontrawariantnego parametru typu można użyć jako typu parametru metody, która należy do interfejsu, lub typu parametru delegata. Kontrawariantnego parametru typu można użyć jako ograniczenia typu ogólnego dla metody interfejsu.  
  
 Tylko typy interfejsów i typy delegatów mogą mieć wariantne parametry typu. Typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
 Programy Visual Basic i C# nie zezwalają na naruszanie reguł używania kowariantnych i kontrawariantnych parametrów typu oraz dodawanie adnotacji o kowariancji i kontrawariancji do parametrów typu dla typów innych niż interfejsy i delegaty. [Asembler MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md) nie wykonuje takich <xref:System.TypeLoadException> kontroli, ale jest generowany, jeśli spróbujesz załadować typ, który narusza reguły.  
  
 Aby uzyskać informacje i przykładowy kod, zobacz [Wariancja w interfejsach ogólnych (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [Odchylenie w interfejsach ogólnych (Visual Basic).](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  

## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Lista wariantów ogólnych typów interfejsów i delegatów
 W .NET Framework 4 następujące typy interfejsu i delegatów mają parametry typu kowariantnego i/lub kontrawariantnego.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Kowariancja i kontrawariancja (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kowariancja i kontrawariancja (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Wariancja w delegatach (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Wariancja w delegatach (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
