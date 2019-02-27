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
ms.openlocfilehash: 931edf3610d083f6821ec87d3e05db855e88c6f9
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836425"
---
# <a name="covariance-and-contravariance-in-generics"></a>Kowariancja i kontrawariancja w typach ogólnych
<a name="top"></a> Kowariancja i kontrawariancja to terminy odwołujące się do możliwość używania typu bardziej pochodnego (bardziej szczegółowe) lub mniej pochodnego typu (specyficzne dla języka less) niż oryginalnie określony. Parametry typu ogólnego obsługują kowariancję i kontrawariancję, aby umożliwić większą elastyczność przypisywania i używania typów ogólnych. W kontekście systemu typów kowariancja, kontrawariancja i inwariancja mają następujące definicje. W przykładach założono, klasa bazowa o nazwie `Base` i Klasa pochodna o nazwie `Derived`.  
  
-   `Covariance`  
  
     Umożliwia użycie typu bardziej pochodnego niż oryginalnie określony.  
  
     Możesz przypisać wystąpienie `IEnumerable<Derived>` (`IEnumerable(Of Derived)` w języku Visual Basic) do zmiennej typu `IEnumerable<Base>`.  
  
-   `Contravariance`  
  
     Umożliwia użycie bardziej ogólnego (mniej pochodnego) typu niż oryginalnie określony.  
  
     Możesz przypisać wystąpienie `Action<Base>` (`Action(Of Base)` w języku Visual Basic) do zmiennej typu `Action<Derived>`.  
  
-   `Invariance`  
  
     Oznacza, że można użyć tylko oryginalnie określonego typu, więc inwariantny parametr typu ogólnego nie jest ani kowariantny, ani kontrawariantny.  
  
     Nie można przypisać wystąpienie `List<Base>` (`List(Of Base)` w języku Visual Basic) do zmiennej typu `List<Derived>` lub na odwrót.  
  
 Kowariantne parametry typu umożliwiają wykonywanie przypisań przypominających zwykły [polimorfizm](~/docs/csharp/programming-guide/classes-and-structs/polymorphism.md), jak pokazano w poniższym kodzie.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601> Klasy implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu, więc `List<Derived>` (`List(Of Derived)` w języku Visual Basic) implementuje `IEnumerable<Derived>`. Kowariantny parametr typu wykonuje resztę zadania.  
  
 Z drugiej strony, kontrawariancja wydaje się nielogiczna. Poniższy przykład tworzy delegat typu `Action<Base>` (`Action(Of Base)` w języku Visual Basic), a następnie ten delegat jest przypisywany do zmiennej typu `Action<Derived>`.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Wydaje się to wsteczne, ale jest to bezpieczny dla typów kod, który można skompilować i uruchomić. Wyrażenie lambda zgodnego z delegatem, jest ona przypisana do użytkownika, więc definiuje metodę przyjmującą jeden parametr typu `Base` i która nie zwraca żadnej wartości. Wynikowego delegata można przypisać do zmiennej typu `Action<Derived>` ponieważ parametr typu `T` z <xref:System.Action%601> delegata jest kontrawariantny. Kod jest bezpieczny ponieważ `T` Określa typ parametru. Gdy delegat typu `Action<Base>` jest wywoływany tak, jakby był delegatem typu `Action<Derived>`, jego argument musi być typu `Derived`. Ten argument zawsze można bezpiecznie przekazać do metody podstawowej, ponieważ parametr metody jest kolumną typu `Base`.  
  
 Ogólnie, kowariantnego parametru typu można użyć jako typu zwracanego delegata, a kontrawariantnych parametrów typu można używać jako typów parametrów. Na przykład kowariantnych parametrów typu można używać jako typów zwracanych metod interfejsu, a kontrawariantnych parametrów typu można używać jako typów parametrów metod interfejsu.  
  
 Kowariancja i kontrawariancja są nazywane zbiorczo *wariancji*. Parametr typu ogólnego, który nie jest oznaczony jako kowariantny lub kontrawariantny nazywa się *niezmiennej*. Krótkie podsumowanie faktów na temat wariancji w środowisku uruchomieniowym języka wspólnego:  
  
-   W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], wariantne parametry typu są ograniczone do typów ogólnych interfejsów i delegatów ogólnych.  
  
-   Ogólny typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
-   Wariancja dotyczy tylko typów referencyjnych; określenie typu wartości dla wariantnego parametru typu spowoduje, że parametr typu będzie inwariantny dla wynikowego skonstruowanego typu.  
  
-   Wariancja nie dotyczy kombinacji delegatów. Oznacza to, jeśli istnieją dwa delegaty typu `Action<Derived>` i `Action<Base>` (`Action(Of Derived)` i `Action(Of Base)` w języku Visual Basic), nie można połączyć drugiego delegata z pierwszym, mimo że wynik byłby bezpieczny typ. Wariancja umożliwia drugiego delegata do przypisania do zmiennej typu `Action<Derived>`, ale delegaty można łączyć tylko wtedy, gdy jest to dokładnie takie same ich typy.  
  
 Kowariantne i kontrawariantne parametry typu szczegółowo opisano w następujących sekcjach:  
  
-   [Interfejsy ogólne z Kowariantnymi parametrami typu](#InterfaceCovariantTypeParameters)  
  
-   [Interfejsy ogólne z Kontrawariantnymi parametrami typu](#InterfaceCovariantTypeParameters)  
  
-   [Delegaty ogólne z Wariantnymi parametry typu](#DelegateVariantTypeParameters)  
  
-   [Definiowanie interfejsów ogólnych typu Variant i delegatów](#DefiningVariantTypeParameters)  
  
-   [Lista typów Variant ogólnego interfejsów i delegatów](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Interfejsy ogólne z kowariantnymi parametrami typu  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], kilka interfejsów ogólnych ma kowariantne parametry typu; na przykład: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>, i <xref:System.Linq.IGrouping%602>. Wszystkie parametry typu tych interfejsów są kowariantne, więc parametry typu są używane tylko dla typów zwracanych elementów członkowskich.  
  
 W poniższym przykładzie pokazano kowariantne parametry typu. W przykładzie zdefiniowano dwa typy: `Base` ma metodę statyczną o nazwie `PrintBases` przyjmującej `IEnumerable<Base>` (`IEnumerable(Of Base)` w języku Visual Basic) i drukującą elementy. `Derived` dziedziczy `Base`. W przykładzie jest tworzona pusta `List<Derived>` (`List(Of Derived)` w języku Visual Basic) i pokazuje, że tego typu mogą być przekazywane do `PrintBases` i przypisane do zmiennej typu `IEnumerable<Base>` bez rzutowania. <xref:System.Collections.Generic.List%601> implementuje <xref:System.Collections.Generic.IEnumerable%601>, który ma jeden kowariantny parametr typu. Kowariantny parametr typu jest przyczyną wystąpienia `IEnumerable<Derived>` mogą być używane zamiast `IEnumerable<Base>`.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Powrót do początku](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Interfejsy ogólne z kontrawariantnymi parametrami typu  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], kilka interfejsów ogólnych ma kontrawariantne parametry typu; na przykład: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, i <xref:System.Collections.Generic.IEqualityComparer%601>. Te interfejsy mają tylko kontrawariantne parametry typu, więc te parametry typów są używane tyko jako typy parametrów w elementach członkowskich tych interfejsów.  
  
 W poniższym przykładzie pokazano kontrawariantne parametry typu. W przykładzie zdefiniowano abstrakcyjny (`MustInherit` w języku Visual Basic) `Shape` klasy `Area` właściwości. Przykładzie zdefiniowano też `ShapeAreaComparer` klasę, która implementuje `IComparer<Shape>` (`IComparer(Of Shape)` w języku Visual Basic). Implementacja <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> Metoda opiera się na wartość `Area` właściwości, więc `ShapeAreaComparer` mogą być używane do sortowania `Shape` obiektów według obszaru.  
  
 `Circle` Klasa dziedziczy `Shape` i zastępuje `Area`. W przykładzie jest tworzony <xref:System.Collections.Generic.SortedSet%601> z `Circle` obiektów, przy użyciu konstruktora przyjmującego `IComparer<Circle>` (`IComparer(Of Circle)` w języku Visual Basic). Jednak zamiast `IComparer<Circle>`, przykład przekazuje `ShapeAreaComparer` obiektu, który implementuje `IComparer<Shape>`. W przykładzie można przekazać funkcję porównującą mniej pochodnego typu (`Shape`) kiedy kod wywołuje funkcję porównującą bardziej pochodnego typu (`Circle`), ponieważ parametr typu <xref:System.Collections.Generic.IComparer%601> ogólny interfejs jest kontrawariantny.  
  
 Gdy nowy `Circle` obiekt jest dodawany do `SortedSet<Circle>`, `IComparer<Shape>.Compare` — metoda (`IComparer(Of Shape).Compare` w języku Visual Basic) z `ShapeAreaComparer` obiektu jest wywoływana za każdym razem, nowy element jest porównywany z istniejącym elementem. Typ parametru metody (`Shape`) jest mniej pochodny niż typ przekazywany (`Circle`), więc wywołanie jest bezpieczne dla typów. Kontrawariancja umożliwia `ShapeAreaComparer` sortowanie kolekcji dowolnego pojedynczego typu oraz mieszanej kolekcji typów, które wynikają z `Shape`.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Powrót do początku](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Delegaty ogólne z wariantnymi parametrami typu  
 W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], `Func` delegaty ogólne, takie jak <xref:System.Func%602>, mają kowariantne typy zwracane i kontrawariantne typy parametrów. `Action` Delegaty ogólne, takie jak <xref:System.Action%602>, mają kontrawariantne typy parametrów. Oznacza to, że delegaty można przypisać do zmiennych, które mają bardziej pochodne typy parametrów i (w przypadku właściwości `Func` delegatów ogólnych) mniej pochodne typy zwracane.  
  
> [!NOTE]
>  Ostatni parametr typu ogólnego `Func` delegatów ogólnych Określa typ wartości zwracanej w podpisie delegata. Jest kowariantny (`out` — słowo kluczowe), podczas gdy inne parametry typu ogólnego są kontrawariantne (`in` — słowo kluczowe).  
  
 Ilustruje to poniższy kod. Pierwsza część kodu definiuje klasę o nazwie `Base`, klasę o nazwie `Derived` dziedziczący po klasie `Base`oraz inną klasę z `static` — metoda (`Shared` w języku Visual Basic) o nazwie `MyMethod`. Ta metoda przyjmuje wystąpienie `Base` i zwraca wystąpienie `Derived`. (Jeśli argument jest wystąpieniem `Derived`, `MyMethod` zwraca go; Jeśli argument jest wystąpieniem `Base`, `MyMethod` zwraca nowe wystąpienie klasy `Derived`.) W `Main()`, przykład tworzy wystąpienie `Func<Base, Derived>` (`Func(Of Base, Derived)` w języku Visual Basic) reprezentujący `MyMethod`i zapisuje ją w zmiennej `f1`.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Drugi fragment kodu pokazuje, że tego delegata można przypisać do zmiennej typu `Func<Base, Base>` (`Func(Of Base, Base)` w języku Visual Basic), ponieważ zwracany typ jest kowariantny.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Trzeciej części kodu widać, że tego delegata można przypisać do zmiennej typu `Func<Derived, Derived>` (`Func(Of Derived, Derived)` w języku Visual Basic), ponieważ typ parametru jest kowariantny.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Końcowy fragment kodu pokazuje, że tego delegata można przypisać do zmiennej typu `Func<Derived, Base>` (`Func(Of Derived, Base)` w języku Visual Basic), łącząc efekty użycia kontrawariantnego typu parametru i kowariantnego typu zwracanego.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Wariancja w delegatach ogólnych i nieogólnych  
 W poprzednim kodzie podpis `MyMethod` dokładnie pasuje do podpisu skonstruowanego delegata ogólnego: `Func<Base, Derived>` (`Func(Of Base, Derived)` w języku Visual Basic). W przykładzie pokazano czy ten delegat ogólny mogą być przechowywane w zmiennych lub parametrach metody, które mają bardziej pochodne typy parametrów i mniej pochodne typy zwracane, tak długo, jak wszystkie typy delegatów są konstruowane na podstawie ogólnego typu delegatów <xref:System.Func%602>.  
  
 Jest to ważny punkt. Efekty zastosowania kowariancji i kontrawariancji w parametrach typu delegatów ogólnych są podobne do efektów zastosowania kowariancji i kontrawariancji w zwykłych powiązaniach delegatów (zobacz [wariancje w Delegatach (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [ Wariancje w Delegatach (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)). Jednak wariancja w powiązaniach delegatów działa ze wszystkimi typami delegatów, a nie tylko z ogólnymi typami delegatów, które mają wariantne parametry typu. Co więcej wariancja w powiązaniach delegatów umożliwia powiązanie metody z dowolnym delegatem, który ma bardziej restrykcyjne typy parametrów i mniej restrykcyjny typ zwracany, podczas gdy przypisanie delegatów ogólnych działa tylko wtedy, gdy oba typy delegatów są konstruowane na podstawie jednej definicji typu ogólnego.  
  
 W poniższym przykładzie pokazano połączone efekty zastosowania wariancji w powiązaniu delegatów oraz zastosowania wariancji w parametrach typu ogólnego. Przykładzie zdefiniowano hierarchię typów zawierającą trzy typy, od najmniej pochodnych (`Type1`) do najbardziej pochodnego (`Type3`). Wariancja w zwykłym powiązaniu delegatów służy do tworzenia powiązania metody mającej typ parametru z `Type1` i zwracanym typem `Type3` z delegatem ogólnym mającym typ parametru elementu `Type2` i zwracanym typem `Type2`. Następnie wynikowy Delegat ogólny jest przypisywany do innej zmiennej, której typ delegata ogólnego ma parametr typu `Type3` i zwracanym typem `Type1`, przy użyciu kowariancji i kontrawariancji parametrów typu genetycznego. Drugie przypisanie wymaga zarówno typ zmiennej i typ delegata zostały skonstruowane na podstawie jednej definicji typu ogólnego, w tym przypadku <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Powrót do początku](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definiowanie wariantów interfejsów i delegatów ogólnych  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Visual Basic i C# mają słowa kluczowe umożliwiające oznaczanie parametrów typu ogólnego interfejsów i delegatów jako kowariantnych lub kontrawariantnych.  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 2.0 środowisko uruchomieniowe języka wspólnego obsługuje adnotacje dotyczące wariancji w parametrach typu ogólnego. Przed [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], jedynym sposobem zdefiniowania klasy ogólnej z tymi adnotacjami jest użycie języka Microsoft intermediate language (MSIL) przez skompilowanie klasy za pomocą [Ilasm.exe (asembler IL)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) lub wyemitowanie jej w dynamicznym zestaw.  
  
 Kowariantny parametr typu jest oznaczona atrybutem `out` — słowo kluczowe (`Out` — słowo kluczowe w języku Visual Basic `+` dla [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Kowariantnego parametru typu można użyć jako wartości zwracanej metody, która należy do interfejsu, lub typu zwracanego delegata. Kowariantnego parametru typu nie można użyć jako ograniczenia typu ogólnego dla metod interfejsu.  
  
> [!NOTE]
>  Jeśli metoda interfejsu ma parametr, który jest typem ogólnym delegatów, kowariantny parametr typu dla typu interfejsu może być używany w celu określenia kontrawariantnego parametru typu dla typu delegata.  
  
 Kontrawariantnego parametru typu jest oznaczona atrybutem `in` — słowo kluczowe (`In` — słowo kluczowe w języku Visual Basic `-` dla [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Kontrawariantnego parametru typu można użyć jako typu parametru metody, która należy do interfejsu, lub typu parametru delegata. Kontrawariantnego parametru typu można użyć jako ograniczenia typu ogólnego dla metody interfejsu.  
  
 Tylko typy interfejsów i typy delegatów mogą mieć wariantne parametry typu. Typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
 Programy Visual Basic i C# nie zezwalają na naruszanie reguł używania kowariantnych i kontrawariantnych parametrów typu oraz dodawanie adnotacji o kowariancji i kontrawariancji do parametrów typu dla typów innych niż interfejsy i delegaty. [MSIL Assembler](../../../docs/framework/tools/ilasm-exe-il-assembler.md) nie wykonuje takich kontroli, ale <xref:System.TypeLoadException> jest generowany, jeśli zostanie podjęta próba załadowania typu naruszającego reguły.  
  
 Aby uzyskać informacji i przykładowy kod, zobacz [wariancje w interfejsach (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) i [wariancje w interfejsach (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
 [Powrót do początku](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Lista wariantów ogólnych typów interfejsów i delegatów  
 W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], następujące typy interfejsów i delegatów mają kowariantne i/lub kontrawariantne parametry typu.  
  
|Typ|Kowariantne parametry typu|Kontrawariantne parametry typu|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601> Aby <xref:System.Action%6016>||Tak|  
|<xref:System.Comparison%601>||Yes|  
|<xref:System.Converter%602>|Yes|Yes|  
|<xref:System.Func%601>|Tak||  
|<xref:System.Func%602> Aby <xref:System.Func%6017>|Tak|Yes|  
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

- [Kowariancja i Kontrawariancja (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Kowariancja i Kontrawariancja (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Wariancje w Delegatach (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Wariancje w Delegatach (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
