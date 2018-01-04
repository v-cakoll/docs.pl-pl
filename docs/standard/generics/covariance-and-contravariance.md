---
title: "Kowariancja i kontrawariancja w typach ogólnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics, covariance and contravariance
- generics, variance
- covariance and contravariance in generics
- generic type parameters
ms.assetid: 2678dc63-c7f9-4590-9ddc-0a4df684d42e
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2abd4c772c02c431ecb73139be7f620fe04d5d82
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="covariance-and-contravariance-in-generics"></a>Kowariancja i kontrawariancja w typach ogólnych
<a name="top"></a>Kowariancja i kontrawariancja są warunki, które odwołują się do możliwość używania mniej pochodnego (szerszym) lub typu (więcej określonych) więcej pochodnego niż określona pierwotnie. Parametry typu ogólnego obsługują kowariancję i kontrawariancję, aby umożliwić większą elastyczność przypisywania i używania typów ogólnych. W kontekście systemu typów kowariancja, kontrawariancja i inwariancja mają następujące definicje. Przykłady założono klasy podstawowej o nazwie `Base` i pochodne klasy o nazwie `Derived`.  
  
-   `Covariance`  
  
     Umożliwia korzystanie z typu pochodnego więcej niż określona pierwotnie.  
  
     Można przypisać wystąpienia `IEnumerable<Derived>` (`IEnumerable(Of Derived)` w języku Visual Basic) do zmiennej typu `IEnumerable<Base>`.  
  
-   `Contravariance`  
  
     Umożliwia użycie bardziej ogólnego (mniej pochodnego) typu niż oryginalnie określony.  
  
     Można przypisać wystąpienia `IEnumerable<Base>` (`IEnumerable(Of Base)` w języku Visual Basic) do zmiennej typu `IEnumerable<Derived>`.  
  
-   `Invariance`  
  
     Oznacza, że można użyć tylko oryginalnie określonego typu, więc inwariantny parametr typu ogólnego nie jest ani kowariantny, ani kontrawariantny.  
  
     Nie można przypisać wystąpienia `IEnumerable<Base>` (`IEnumerable(Of Base)` w języku Visual Basic) do zmiennej typu `IEnumerable<Derived>` lub na odwrót.  
  
 Parametry typu kowariantnego pozwalają utworzyć przydziałów, które wyglądają bardzo podobnie zwykłych [polimorfizm](~/docs/csharp/programming-guide/classes-and-structs/polymorphism.md), jak pokazano w poniższym kodzie.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 <xref:System.Collections.Generic.List%601> Klasa implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu, dlatego `List<Derived>` (`List(Of Derived)` w języku Visual Basic) implementuje `IEnumerable<Derived>`. Kowariantny parametr typu wykonuje resztę zadania.  
  
 Z drugiej strony, kontrawariancja wydaje się nielogiczna. Poniższy przykład tworzy delegowanego typu `Action<Base>` (`Action(Of Base)` w języku Visual Basic), a następnie przypisuje do zmiennej typu tego delegata `Action<Derived>`.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Wydaje się to wsteczne, ale jest to bezpieczny dla typów kod, który można skompilować i uruchomić. Wyrażenia lambda zgodnego z delegatem, jest przypisany do, więc definiuje metodę, która przyjmuje jeden parametr typu `Base` i który nie ma wartości zwracanych. Wynikowa delegata można przypisać do zmiennej typu `Action<Derived>` ponieważ parametr typu `T` z <xref:System.Action%601> delegata jest kontrawariantny. Kod jest bezpieczne ponieważ `T` Określa typ parametru. Gdy delegowanego typu `Action<Base>` tak, jakby był on delegowanego typu `Action<Derived>`, jej argument musi być typu `Derived`. Ten argument zawsze można przekazać bezpiecznie do metody podstawowej, ponieważ parametr metody jest typu `Base`.  
  
 Ogólnie, kowariantnego parametru typu można użyć jako typu zwracanego delegata, a kontrawariantnych parametrów typu można używać jako typów parametrów. Na przykład kowariantnych parametrów typu można używać jako typów zwracanych metod interfejsu, a kontrawariantnych parametrów typu można używać jako typów parametrów metod interfejsu.  
  
 Kowariancja i kontrawariancja są nazywane zbiorczo *wariancji*. Parametr typu ogólnego, który nie jest oznaczony jako kowariantnego lub kontrawariantnego nazywa się *niezmiennej*. Krótkie podsumowanie faktów na temat wariancji w środowisku uruchomieniowym języka wspólnego:  
  
-   W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], parametry typu variant są ograniczone do ogólny interfejs i ogólnych typów delegata.  
  
-   Ogólny typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
-   Wariancja dotyczy tylko typów referencyjnych; określenie typu wartości dla wariantnego parametru typu spowoduje, że parametr typu będzie inwariantny dla wynikowego skonstruowanego typu.  
  
-   Wariancja nie dotyczy kombinacji delegatów. Oznacza to, że podane delegatów dwóch typów `Action<Derived>` i `Action<Base>` (`Action(Of Derived)` i `Action(Of Base)` w języku Visual Basic), drugi delegata nie można łączyć z pierwszego, mimo że wynikiem byłby typu bezpieczne. Wariancja pełnomocnik drugi do przypisania do zmiennej typu `Action<Derived>`, ale delegatów można połączyć tylko wtedy, gdy ich typy są takie same.  
  
 Kowariantne i kontrawariantne parametry typu szczegółowo opisano w następujących sekcjach:  
  
-   [Interfejsy ogólne z parametrami typu kowariantnego](#InterfaceCovariantTypeParameters)  
  
-   [Interfejsy ogólne z parametrami typu ogólnego kontrawariantnego](#InterfaceCovariantTypeParameters)  
  
-   [Parametry typu ogólnego delegatów z wariantu](#DelegateVariantTypeParameters)  
  
-   [Definiowanie interfejsów ogólnych typu Variant i Delegaty](#DefiningVariantTypeParameters)  
  
-   [Lista Variant ogólny interfejs i typy delegatów](#VariantList)  
  
<a name="InterfaceCovariantTypeParameters"></a>   
## <a name="generic-interfaces-with-covariant-type-parameters"></a>Interfejsy ogólne z kowariantnymi parametrami typu  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], kilku interfejsach ma parametry typu kowariantnego; na przykład: <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Linq.IQueryable%601>, i <xref:System.Linq.IGrouping%602>. Wszystkie parametry typu tych interfejsów są kowariantne, więc parametry typu są używane tylko dla typów zwracanych elementów członkowskich.  
  
 W poniższym przykładzie pokazano kowariantne parametry typu. W przykładzie zdefiniowano dwa typy: `Base` ma statycznej metody o nazwie `PrintBases` pobierającej `IEnumerable<Base>` (`IEnumerable(Of Base)` w języku Visual Basic) i wyświetla elementy. `Derived`dziedziczy `Base`. W przykładzie jest tworzony pustą `List<Derived>` (`List(Of Derived)` w języku Visual Basic) i pokazuje, że tego typu mogą zostać przekazane do `PrintBases` i przypisany do zmiennej typu `IEnumerable<Base>` bez rzutowania. <xref:System.Collections.Generic.List%601>implementuje <xref:System.Collections.Generic.IEnumerable%601>, który ma parametr typu kowariantnego pojedynczego. Parametr typu kowariantnego dlaczego jest przyczyną wystąpienia `IEnumerable<Derived>` można użyć zamiast `IEnumerable<Base>`.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
 [Powrót do początku](#top)  
  
<a name="InterfaceContravariantTypeParameters"></a>   
## <a name="generic-interfaces-with-contravariant-generic-type-parameters"></a>Interfejsy ogólne z kontrawariantnymi parametrami typu  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], kilku interfejsach mieć kontrawariantnego parametrów typu, na przykład: <xref:System.Collections.Generic.IComparer%601>, <xref:System.IComparable%601>, i <xref:System.Collections.Generic.IEqualityComparer%601>. Te interfejsy mają tylko kontrawariantne parametry typu, więc te parametry typów są używane tyko jako typy parametrów w elementach członkowskich tych interfejsów.  
  
 W poniższym przykładzie pokazano kontrawariantne parametry typu. W przykładzie zdefiniowano abstrakcyjnego (`MustInherit` w języku Visual Basic) `Shape` klasy z `Area` właściwości. Definiuje również przykładzie `ShapeAreaComparer` klasa implementująca `IComparer<Shape>` (`IComparer(Of Shape)` w języku Visual Basic). Implementacja <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> metoda jest oparta na wartości `Area` właściwości, więc `ShapeAreaComparer` mogą być używane do sortowania `Shape` obiekty według obszaru.  
  
 `Circle` Klasa dziedziczy `Shape` i zastępuje `Area`. W przykładzie jest tworzony <xref:System.Collections.Generic.SortedSet%601> z `Circle` obiektów przy użyciu konstruktora przyjmującego `IComparer<Circle>` (`IComparer(Of Circle)` w języku Visual Basic). Jednak zamiast przekazywanie `IComparer<Circle>`, przekazuje przykładzie `ShapeAreaComparer` obiektu, który implementuje `IComparer<Shape>`. Przykład można przekazać porównania typu mniej pochodnego (`Shape`) gdy kod odwołuje się do porównania z typu pochodnego (`Circle`), ponieważ parametr typu <xref:System.Collections.Generic.IComparer%601> ogólny interfejs jest kontrawariantny.  
  
 Podczas tworzenia nowego `Circle` obiekt jest dodawany do `SortedSet<Circle>`, `IComparer<Shape>.Compare` — metoda (`IComparer(Of Shape).Compare` metody w języku Visual Basic) z `ShapeAreaComparer` obiektu jest wywoływana za każdym razem nowego elementu jest porównywany z istniejącego elementu. Typ parametru metody (`Shape`) jest mniejsza pochodzi od typu, który jest przekazywany (`Circle`), dlatego wywołanie jest typu bezpieczne. Umożliwia Kontrawariancja `ShapeAreaComparer` sortowanie kolekcji dowolnego pojedynczego typu, a także typy, które pochodzą z kolekcji mieszanej `Shape`.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  
  
 [Powrót do początku](#top)  
  
<a name="DelegateVariantTypeParameters"></a>   
## <a name="generic-delegates-with-variant-type-parameters"></a>Delegaty ogólne z wariantnymi parametrami typu  
 W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], `Func` deleguje ogólne, takie jak <xref:System.Func%602>, kowariantne typy zwracane i typy parametrów kontrawariantny. `Action` Deleguje ogólne, takie jak <xref:System.Action%602>, mają kontrawariantnego typy parametrów. Oznacza to, że delegatów mogą być przypisane do zmiennych, które mają bardziej pochodnego typy parametrów i (w przypadku liczby `Func` delegatów) mniej zwracanych typów pochodnych.  
  
> [!NOTE]
>  Ostatni parametr typu ogólnego `Func` delegatów Określa typ zwracanej wartości w podpisie delegata. Jest kowariantny (`out` — słowo kluczowe), podczas gdy inne parametry typu ogólnego są kontrawariantnego (`in` — słowo kluczowe).  
  
 Ilustruje to poniższy kod. Pierwszy element kod definiuje klasę o nazwie `Base`, klasę o nazwie `Derived` dziedziczącego `Base`i innej klasy z `static` — metoda (`Shared` w języku Visual Basic) o nazwie `MyMethod`. Metoda korzysta z wystąpienia `Base` i zwraca wystąpienie klasy `Derived`. (Jeśli argument jest wystąpieniem `Derived`, `MyMethod` zwraca; Jeśli argument wystąpienia `Base`, `MyMethod` zwraca nowe wystąpienie klasy `Derived`.) W `Main()`, przykładzie tworzy wystąpienie `Func<Base, Derived>` (`Func(Of Base, Derived)` w języku Visual Basic) reprezentujący `MyMethod`i zapisuje go w zmiennej `f1`.  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 Drugi fragment kodu pokazuje, że delegata można przypisać do zmiennej typu `Func<Base, Base>` (`Func(Of Base, Base)` w języku Visual Basic), ponieważ typ zwracany jest kowariantny.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 Trzeci fragment kodu pokazuje, że delegata można przypisać do zmiennej typu `Func<Derived, Derived>` (`Func(Of Derived, Derived)` w języku Visual Basic), ponieważ parametr typu jest kontrawariantny.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 Ostatni element kodu pokazuje, że delegata można przypisać do zmiennej typu `Func<Derived, Base>` (`Func(Of Derived, Base)` w języku Visual Basic), typ parametru łączenie skutków kontrawariantnego i kowariantnego typ zwracany.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-generic-and-non-generic-delegates"></a>Wariancja w delegatach ogólnych i nieogólnych  
 W powyższym kodzie podpis `MyMethod` dokładnie odpowiada podpis skonstruowane Delegat ogólny: `Func<Base, Derived>` (`Func(Of Base, Derived)` w języku Visual Basic). Przykład pokazuje, że ten delegat ogólny może być przechowywana w zmiennych i parametrów metody, które mają bardziej pochodnego typy parametrów i mniej pochodnego zwracane typy, tak długo, jak wszystkie typy delegata są tworzone na podstawie typu Delegat ogólny <xref:System.Func%602>.  
  
 Jest to ważny punkt. Efekty Kowariancja i kontrawariancja w parametrach typu delegaty ogólne są podobne do skutków Kowariancja i kontrawariancja w zwykłym delegata powiązania (zobacz [wariancji w Delegatach](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)). Jednak wariancja w powiązaniach delegatów działa ze wszystkimi typami delegatów, a nie tylko z ogólnymi typami delegatów, które mają wariantne parametry typu. Co więcej wariancja w powiązaniach delegatów umożliwia powiązanie metody z dowolnym delegatem, który ma bardziej restrykcyjne typy parametrów i mniej restrykcyjny typ zwracany, podczas gdy przypisanie delegatów ogólnych działa tylko wtedy, gdy oba typy delegatów są konstruowane na podstawie jednej definicji typu ogólnego.  
  
 W poniższym przykładzie pokazano połączone efekty zastosowania wariancji w powiązaniu delegatów oraz zastosowania wariancji w parametrach typu ogólnego. W przykładzie zdefiniowano hierarchii typów, która obejmuje trzy typy, od najmniejszej pochodnych (`Type1`) do najbardziej pochodnej (`Type3`). Wariancje w zwykłym delegata powiązanie jest używana do powiązania z typem parametru metody `Type1` i typ zwracany `Type3` do delegata ogólnego typu parametru `Type2` i typ zwracany `Type2`. Delegat ogólny wynikowy jest przypisywana do innej zmiennej o typie Delegat ogólny ma parametr typu `Type3` i typ zwracany `Type1`, przy użyciu Kowariancja i kontrawariancja parametrów typu ogólnego. Drugi przypisania wymaga zarówno typ zmiennej i z typem obiektu delegowanego, aby zostać utworzone na podstawie tej samej definicji typu ogólnego, w tym przypadku <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  
  
 [Powrót do początku](#top)  
  
<a name="DefiningVariantTypeParameters"></a>   
## <a name="defining-variant-generic-interfaces-and-delegates"></a>Definiowanie wariantów interfejsów i delegatów ogólnych  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Visual Basic i C# ma słów kluczowych, które umożliwiają oznaczenie parametry typu ogólnego interfejsów i deleguje jako kowariantnego lub kontrawariantnego.  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 2.0 środowisko uruchomieniowe języka wspólnego obsługuje adnotacje dotyczące wariancji w parametrach typu ogólnego. Przed [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], jedynym sposobem, aby zdefiniować ogólny klasy, która ma adnotacje jest użycie język pośredni firmy Microsoft (MSIL), albo przez skompilowanie klasy z [Ilasm.exe (asembler IL)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) lub przez emitowanie go w dynamicznym zestaw.  
  
 Parametr typu kowariantnego jest oznaczony atrybutem `out` — słowo kluczowe (`Out` słów kluczowych w języku Visual Basic `+` dla [asembler MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Kowariantnego parametru typu można użyć jako wartości zwracanej metody, która należy do interfejsu, lub typu zwracanego delegata. Kowariantnego parametru typu nie można użyć jako ograniczenia typu ogólnego dla metod interfejsu.  
  
> [!NOTE]
>  Jeśli metoda interfejsu ma parametr, który jest typem ogólnym delegatów, kowariantny parametr typu dla typu interfejsu może być używany w celu określenia kontrawariantnego parametru typu dla typu delegata.  
  
 Parametr typu kontrawariantnego jest oznaczony atrybutem `in` — słowo kluczowe (`In` słów kluczowych w języku Visual Basic `-` dla [asembler MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md)). Kontrawariantnego parametru typu można użyć jako typu parametru metody, która należy do interfejsu, lub typu parametru delegata. Kontrawariantnego parametru typu można użyć jako ograniczenia typu ogólnego dla metody interfejsu.  
  
 Tylko typy interfejsów i typy delegatów mogą mieć wariantne parametry typu. Typ interfejsu lub delegata może mieć kowariantne i kontrawariantne parametry typu.  
  
 Programy Visual Basic i C# nie zezwalają na naruszanie reguł używania kowariantnych i kontrawariantnych parametrów typu oraz dodawanie adnotacji o kowariancji i kontrawariancji do parametrów typu dla typów innych niż interfejsy i delegaty. [Asembler MSIL](../../../docs/framework/tools/ilasm-exe-il-assembler.md) nie przeprowadza kontrole, ale <xref:System.TypeLoadException> jest generowany, jeśli użytkownik próbuje załadować typu, który narusza zasady.  
  
 Informacje i przykładowy kod, zobacz [wariancje w interfejsach](http://msdn.microsoft.com/library/e14322da-1db3-42f2-9a67-397daddd6b6a).  
  
 [Powrót do początku](#top)  
  
<a name="VariantList"></a>   
## <a name="list-of-variant-generic-interface-and-delegate-types"></a>Lista wariantów ogólnych typów interfejsów i delegatów  
 W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], następujących typów interfejsu i delegata ma kowariantnego lub kontrawariantnego parametry typu.  
  
|Typ|Kowariantne parametry typu|Kontrawariantne parametry typu|  
|----------|-------------------------------|-----------------------------------|  
|<xref:System.Action%601>Aby<xref:System.Action%6016>||Tak|  
|<xref:System.Comparison%601>||Tak|  
|<xref:System.Converter%602>|Tak|Tak|  
|<xref:System.Func%601>|Tak||  
|<xref:System.Func%602>Aby<xref:System.Func%6017>|Tak|Tak|  
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
 [Kowariancja i Kontrawariancja (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
 [Kowariancja i Kontrawariancja (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)    
 [Wariancje w delegatach](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)
