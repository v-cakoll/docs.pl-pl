---
title: Odbicie i typy ogólne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic types
- reflection, generic types
- type arguments
- generics [.NET Framework], reflection
- viewing type information
- type information, viewing
- types, generic
- type parameters
ms.assetid: f7180fc5-dd41-42d4-8a8e-1b34288e06de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0536acbcc71ae7792ec668ac352e95e604bd979
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591368"
---
# <a name="reflection-and-generic-types"></a>Odbicie i typy ogólne
<a name="top"></a> Z punktu widzenia odbicia, czy typem ogólnym skojarzył z nim zestaw parametrów typu (jeśli jest definicja typu ogólnego) jest różnica między typem ogólnym i typu zwykłego lub argumentów typu (jeśli jest skonstruowanego typu). Metody ogólnej różni się od zwykłej metody w taki sam sposób.  
  
 Istnieją dwa klucze do zrozumienia, jak odbicie obsługuje typy ogólne i metody:  
  
- Parametry typu w definicji typu ogólnego i definicji metody ogólnej są reprezentowane przez wystąpienia <xref:System.Type> klasy.  
  
    > [!NOTE]
    >  Wiele właściwości i metod <xref:System.Type> mają różne zachowanie podczas <xref:System.Type> obiekt reprezentuje parametr typu ogólnego. Te różnice są opisane w tematach właściwości i metody. Na przykład zobacz <xref:System.Type.IsAutoClass%2A> i <xref:System.Type.DeclaringType%2A>. Ponadto niektóre elementy członkowskie są prawidłowe tylko wtedy, gdy <xref:System.Type> obiekt reprezentuje parametr typu ogólnego. Na przykład zobacz <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
- Jeśli wystąpienie <xref:System.Type> reprezentuje typ ogólny, a następnie obejmuje szereg typów, które reprezentują parametry typu (w przypadku definicji typu ogólnego) lub typu argumentów (typy utworzone). To samo dotyczy wystąpienia <xref:System.Reflection.MethodInfo> klasa, która reprezentuje metody rodzajowej.  
  
 Odbicie zapewnia metody <xref:System.Type> i <xref:System.Reflection.MethodInfo> umożliwiające dostęp do tablicy parametrów typu oraz określić, czy wystąpienie <xref:System.Type> reprezentuje parametr typu lub rzeczywistego typu.  
  
 Na przykład zobacz kod ukazujące metody omówionych w tym miejscu [jak: Badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Następujące dyskusji założono znajomość terminologii typów ogólnych, takich jak różnicę między parametrami typu i argumentów i otwarte lub zamknięte typy utworzone. Aby uzyskać więcej informacji, zobacz [ogólne](../../../docs/standard/generics/index.md).  
  
 To omówienie składa się z następujących sekcji:  
  
- [To jest typu ogólnego lub metody?](#is_this_a_generic_type_or_method)  
  
- [Generowanie zamknięte typy rodzajowe](#generating_closed_generic_types)  
  
- [Badanie argumenty typu i parametrów typu](#examining_type_arguments)  
  
- [Invariants](#invariants)  
  
- [Tematy pokrewne](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a>To jest typu ogólnego lub metody?  
 Kiedy używać odbicia do sprawdzenia nieznanym typem, reprezentowany przez wystąpienie <xref:System.Type>, użyj <xref:System.Type.IsGenericType%2A> właściwości w celu określenia, czy jest nieznany typ ogólny. Zwraca `true` przypadku typu ogólnego. Podobnie podczas badania Nieznana metoda, reprezentowany przez wystąpienie <xref:System.Reflection.MethodInfo> klasy, należy użyć <xref:System.Reflection.MethodBase.IsGenericMethod%2A> właściwości w celu określenia, czy metoda jest ogólna.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>To jest typu ogólnego lub definicję metody?  
 Użyj <xref:System.Type.IsGenericTypeDefinition%2A> właściwości, aby określić, czy <xref:System.Type> obiekt reprezentuje definicji typu ogólnego i użyć <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> metodę pozwala ustalić czy <xref:System.Reflection.MethodInfo> reprezentuje definicję metody rodzajowej.  
  
 Ogólne definicji typu i metody są szablony, z których tworzone są tworzone jako wystąpienia typy. Ogólne typy w bibliotece klas programu .NET Framework, takie jak <xref:System.Collections.Generic.Dictionary%602>, są definicje typu ogólnego.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Jest to typ lub metoda otwarte lub zamknięte?  
 Typu ogólnego lub metody jest zamknięte, jeśli tworzone jako wystąpienia typów zostać podstawione dla wszystkich jego parametrów typu, w tym wszystkich parametrów typu dla wszystkich typów otaczającej. Tylko można utworzyć wystąpienia typu ogólnego, jeśli wystąpienie jest zamykane. <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> Właściwość zwraca `true` Jeśli typ jest otwarty. W przypadku metod <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> metoda wykonuje tę samą funkcję.  
  
 [Powrót do początku](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a>Generowanie zamknięte typy rodzajowe  
 Po utworzeniu typu ogólnego lub definicję metody, użyj <xref:System.Type.MakeGenericType%2A> metodę w celu utworzenia zamknięty typ ogólny lub <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> metodę w celu utworzenia <xref:System.Reflection.MethodInfo> zamkniętego metody rodzajowej.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Wprowadzenie w ogólnym typie lub definicję metody  
 Jeśli masz otwarty typ ogólny lub metody, która nie jest typu ogólnego lub definicję metody, nie można utworzyć jego wystąpienia, a nie może dostarczyć parametry typu, które nie mają. Musisz mieć ogólne definicji typu lub metody. Użyj <xref:System.Type.GetGenericTypeDefinition%2A> metody uzyskiwania definicji typu ogólnego lub <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> metodę, aby uzyskać definicję metody rodzajowej.  
  
 Na przykład, jeśli masz <xref:System.Type> obiekt reprezentujący `Dictionary<int, string>` (`Dictionary(Of Integer, String)` w języku Visual Basic) i chcesz utworzyć typ `Dictionary<string, MyClass>`, możesz użyć <xref:System.Type.GetGenericTypeDefinition%2A> metodę, aby uzyskać <xref:System.Type> reprezentujący `Dictionary<TKey, TValue>` i następnie użyj <xref:System.Type.MakeGenericType%2A> metody do tworzenia <xref:System.Type> reprezentujący `Dictionary<int, MyClass>`.  
  
 Na przykład to otwarty typ ogólny, który nie jest typem ogólnym zobacz "Typ parametr lub Argument typu" w dalszej części tego tematu.  
  
 [Powrót do początku](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a>Badanie argumenty typu i parametrów typu  
 Użyj <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> metodę, aby uzyskać tablicę <xref:System.Type> obiektów, które reprezentują parametry typu lub typów argumentów typu rodzajowego, a następnie użyj <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> metodę, aby zrobić to samo dla metody rodzajowej.  
  
 Gdy wiesz, że <xref:System.Type> obiekt reprezentuje parametr typu, wiele dodatkowych pytań odbicia pozwala uzyskać odpowiedzi. Można określić parametru typu źródła, położenia i ograniczenia.  
  
### <a name="type-parameter-or-type-argument"></a>Parametr typu lub Argument typu  
 Aby określić, czy określony element tablicy jest parametrem typu, czy argument typu, należy użyć <xref:System.Type.IsGenericParameter%2A> właściwości. <xref:System.Type.IsGenericParameter%2A> Właściwość `true` Jeśli element jest parametrem typu.  
  
 Typ ogólny może być otwarty, nie będąc definicji typu ogólnego, w którym to przypadku musi kombinację argumentów typu parametrów typu. Na przykład, poniższy kod klasy `D` pochodzi od typu utworzone, zastępując pierwszy parametr typu `D` dla drugiego parametru typu `B`.  
  
```csharp  
class B<T, U> {}  
class D<V, W> : B<int, V> {}  
```  
  
```vb  
Class B(Of T, U)  
End Class  
Class D(Of V, W)  
    Inherits B(Of Integer, V)  
End Class  
```  
  
```cpp  
generic<typename T, typename U> ref class B {};  
generic<typename V, typename W> ref class D : B<int, V> {};  
```  
  
 Po uzyskaniu <xref:System.Type> obiekt reprezentujący `D<V, W>` i użyj <xref:System.Type.BaseType%2A> właściwości, aby uzyskać jego typ podstawowy, wynikowy `type B<int, V>` jest otwarty, ale nie jest definicja typu ogólnego.  
  
### <a name="source-of-a-generic-parameter"></a>Źródło parametru ogólnego  
 Parametr typu ogólnego może pochodzić z typu, który sprawdzasz, typ otaczający lub metody rodzajowej. Można określić źródło parametru typu ogólnego w następujący sposób:  
  
- Najpierw za pomocą <xref:System.Type.DeclaringMethod%2A> właściwości w celu określenia, czy parametr typu pochodzi z metody rodzajowej. Jeśli wartość właściwości nie jest odwołanie o wartości null (`Nothing` w języku Visual Basic), źródło jest metody rodzajowej.  
  
- Jeśli źródło nie jest metodą podstawową, użyj <xref:System.Type.DeclaringType%2A> należy właściwości w celu określenia typu ogólnego, parametr typu ogólnego.  
  
 Jeśli parametr typu należy do metody rodzajowej, <xref:System.Type.DeclaringType%2A> właściwość zwraca typ, który zadeklarowana metody rodzajowej, która nie ma znaczenia.  
  
### <a name="position-of-a-generic-parameter"></a>Pozycja parametru ogólnego  
 W rzadkich przypadkach jest niezbędne do określenia pozycji parametr typu na liście parametrów typu deklarującego klasy. Załóżmy, że masz <xref:System.Type> obiekt reprezentujący `B<int, V>` typu z poprzedniego przykładu. <xref:System.Type.GetGenericArguments%2A> Metoda zawiera listę argumentów typu, a podczas badania `V` można użyć <xref:System.Type.DeclaringMethod%2A> i <xref:System.Type.DeclaringType%2A> właściwości, aby dowiedzieć się, gdzie pochodzi on z. Następnie można użyć <xref:System.Type.GenericParameterPosition%2A> właściwości w celu określenia jego pozycja w lista parametrów typu, w którym został zdefiniowany. W tym przykładzie `V` znajduje się na pozycji 0 (zero) na liście parametrów typu, gdzie został zdefiniowany.  
  
### <a name="base-type-and-interface-constraints"></a>Typ podstawowy i ograniczenia interfejsu  
 Użyj <xref:System.Type.GetGenericParameterConstraints%2A> metodę, aby uzyskać typ podstawowy, ograniczenia i interfejs ograniczenia parametru typu. Kolejność elementów w tablicy nie ma znaczenia. Element reprezentuje ograniczenie interfejsu, jeśli jest typem interfejsu.  
  
### <a name="generic-parameter-attributes"></a>Atrybuty parametrów ogólnych  
 <xref:System.Type.GenericParameterAttributes%2A> Pobiera właściwość <xref:System.Reflection.GenericParameterAttributes> wartość, która wskazuje odchylenia (kowariancji i kontrawariancji), jak i szczególne ograniczenia parametru typu.  
  
#### <a name="covariance-and-contravariance"></a>Kowariancja i kontrawariancja  
 Aby ustalić, czy parametr typu jest kowariantny lub kontrawariantny, zastosuj <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> maski do <xref:System.Reflection.GenericParameterAttributes> wartość, która jest zwracana przez <xref:System.Type.GenericParameterAttributes%2A> właściwości. Jeśli wynik jest <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, parametr typu będzie inwariantny. Zobacz [kowariancji i kontrawariancji](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Ograniczenia specjalne  
 Aby określić specjalne ograniczenia parametru typu, należy zastosować <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> maski do <xref:System.Reflection.GenericParameterAttributes> wartość, która jest zwracana przez <xref:System.Type.GenericParameterAttributes%2A> właściwości. Jeśli wynik jest <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, istnieją nie specjalne ograniczenia. Parametr typu mogą być ograniczone do być typem referencyjnym, aby być typem wartościowym niebędącym i ma konstruktora domyślnego.  
  
 [Powrót do początku](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a>Invariants  
 Dla tabeli niezmiennych warunków dla typowe terminy w odbiciu do typów ogólnych, zobacz <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Aby uzyskać dodatkowe postanowienia dotyczące metod ogólnych, zobacz <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|Przedstawia sposób użycia właściwości i metod <xref:System.Type> i <xref:System.Reflection.MethodInfo> do sprawdzenia typów ogólnych.|  
|[Typy ogólne](../../../docs/standard/generics/index.md)|Zawiera opis funkcji ogólne i jak jest obsługiwana w programie .NET Framework.|  
|[Instrukcje: Definiowanie typu ogólnego przy użyciu odbicia emisji](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Pokazuje, jak używać odbicia emisji do generowania typów ogólnych w zestawach dynamicznych.|  
|[Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|W tym artykule opisano <xref:System.Type> klasy i przykłady kodu, które ilustrują sposób korzystania <xref:System.Type> z różnymi klasami odbicia do uzyskiwania informacji o konstruktory, metody, pola, właściwości i zdarzenia.|
