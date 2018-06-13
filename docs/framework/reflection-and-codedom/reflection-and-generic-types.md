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
ms.openlocfilehash: a45ef91eba38223270a04cff2f00c30decb019f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399707"
---
# <a name="reflection-and-generic-types"></a>Odbicie i typy ogólne
<a name="top"></a> Z punktu widzenia odbicia, że typu ogólnego jest skojarzony z nim zestaw parametrów typu (jeśli jest definicją typu ogólnego) jest różnica między typem ogólnym i typu zwykłego lub argumentów typu (jeśli jest skonstruowanego typu). Metoda ogólna różni się od zwykłej metody w taki sam sposób.  
  
 Dostępne są dwa klucze do zrozumienia, jak odbicia obsługuje typy ogólne i metody:  
  
-   Parametrów typu w definicji typu ogólnego i definicji metody ogólnej są reprezentowane przez wystąpień <xref:System.Type> klasy.  
  
    > [!NOTE]
    >  Wiele właściwości i metod <xref:System.Type> mają różne zachowanie podczas <xref:System.Type> obiekt reprezentuje parametr typu ogólnego. Te różnice są opisane w tematach właściwości i metody. Na przykład, zobacz <xref:System.Type.IsAutoClass%2A> i <xref:System.Type.DeclaringType%2A>. Ponadto niektóre elementy członkowskie są prawidłowe tylko w przypadku <xref:System.Type> obiekt reprezentuje parametr typu ogólnego. Na przykład, zobacz <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
-   Jeśli wystąpienie <xref:System.Type> reprezentuje typu ogólnego, a następnie zawiera tablicę typów, które reprezentują parametry typu (dla definicji typu ogólnego) lub typu argumenty (typy utworzone). To samo dotyczy wystąpienia <xref:System.Reflection.MethodInfo> klasa, która reprezentuje metody rodzajowej.  
  
 Odbicie udostępnia metody <xref:System.Type> i <xref:System.Reflection.MethodInfo> umożliwiającą dostęp do tablicy parametrów typu i określić, czy wystąpienie <xref:System.Type> reprezentuje parametr typu lub rzeczywistego typu.  
  
 Na przykład zobacz kod prezentacja metod omówionych w tym miejscu [porady: zbadanie i rodzajowy wystąpień typów za pomocą odbicia](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 Następujące dyskusji zakłada się znajomość terminologii ogólne, takie jak różnica między parametrów typu i argumentów i open lub closed typy utworzone. Aby uzyskać więcej informacji, zobacz [ogólne](../../../docs/standard/generics/index.md).  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [To jest typu ogólnego lub metody?](#is_this_a_generic_type_or_method)  
  
-   [Generowanie zamkniętego typów ogólnych](#generating_closed_generic_types)  
  
-   [Badanie typu argumentów i parametrów typu](#examining_type_arguments)  
  
-   [Invariants](#invariants)  
  
-   [Tematy pokrewne](#related_topics)  
  
<a name="is_this_a_generic_type_or_method"></a>   
## <a name="is-this-a-generic-type-or-method"></a>To jest typu ogólnego lub metody?  
 Jeśli używasz odbicia do sprawdzenia nieznany typ reprezentowany przez wystąpienie <xref:System.Type>, użyj <xref:System.Type.IsGenericType%2A> właściwości w celu określenia, czy nieznany typ jest rodzajowy. Zwraca `true` Jeśli typ jest rodzajowy. Podobnie podczas badania Nieznana metoda reprezentowany przez wystąpienie <xref:System.Reflection.MethodInfo> klasy, należy użyć <xref:System.Reflection.MethodBase.IsGenericMethod%2A> właściwości w celu określenia, czy metoda jest rodzajowy.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>To jest ogólnym typie lub metoda definicji?  
 Użyj <xref:System.Type.IsGenericTypeDefinition%2A> umożliwia określenie, czy <xref:System.Type> obiekt reprezentuje definicji typu ogólnego i użyj <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> metodę, aby określić, czy <xref:System.Reflection.MethodInfo> reprezentuje definicję metody rodzajowej.  
  
 Ogólny definicje typu i metody są szablony, z których tworzone jako wystąpienia typów są tworzone. Ogólne typy w bibliotece klas programu .NET Framework, takich jak <xref:System.Collections.Generic.Dictionary%602>, definicji typu ogólnego.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Typ lub metoda Open lub Closed?  
 Jeśli dla wszystkich jego parametrów typu, w tym wszystkie parametry typu wszystkich typów otaczającego zostać podstawione tworzone jako wystąpienia typów, typie ogólnym lub metodzie jest zamknięty. Można tylko utworzyć wystąpienia typu ogólnego, jeśli jest ono zamknięte. <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> Zwraca `true` Jeśli typ jest otwarty. W przypadku metod <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> taką samą funkcję wykonuje metodę.  
  
 [Powrót do początku](#top)  
  
<a name="generating_closed_generic_types"></a>   
## <a name="generating-closed-generic-types"></a>Generowanie zamkniętego typów ogólnych  
 Po utworzeniu typu ogólnego lub metody definicji, użyj <xref:System.Type.MakeGenericType%2A> metodę w celu utworzenia zamkniętego typu ogólnego lub <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> metodę w celu utworzenia <xref:System.Reflection.MethodInfo> zamkniętej metody rodzajowej.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Pobieranie typie ogólnym lub definicji — metoda  
 Jeśli masz otwarty typ ogólny lub metodę, która nie jest typu ogólnego lub metody definicji, nie można utworzyć wystąpień i nie można podać parametrów typu, które nie są spełnione. Musi mieć ogólnych definicji typu lub metody. Użyj <xref:System.Type.GetGenericTypeDefinition%2A> metodę, aby uzyskać definicji typu ogólnego lub <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> metodę, aby uzyskać definicję metody rodzajowej.  
  
 Na przykład, jeśli masz <xref:System.Type> reprezentujący obiekt `Dictionary<int, string>` (`Dictionary(Of Integer, String)` w języku Visual Basic) i chcesz utworzyć typ `Dictionary<string, MyClass>`, można użyć <xref:System.Type.GetGenericTypeDefinition%2A> metodę, aby pobrać <xref:System.Type> reprezentujący `Dictionary<TKey, TValue>` i następnie użyj <xref:System.Type.MakeGenericType%2A> metody do tworzenia <xref:System.Type> reprezentujący `Dictionary<int, MyClass>`.  
  
 Na przykład otwarty typ ogólny, który nie jest typem ogólnym zobacz "Parametr lub typ Argument typu" w dalszej części tego tematu.  
  
 [Powrót do początku](#top)  
  
<a name="examining_type_arguments"></a>   
## <a name="examining-type-arguments-and-type-parameters"></a>Badanie typu argumentów i parametrów typu  
 Użyj <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> metodę, aby uzyskać tablicę <xref:System.Type> obiekty, które reprezentują parametry typu lub argumentów typu ogólnego typu i użyj <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> metodę wykonaj te same metody rodzajowej.  
  
 Po sprawdzeniu, że <xref:System.Type> obiekt reprezentuje parametr typu, istnieje wiele dodatkowych pytań odbicia pozwala uzyskać odpowiedzi. Można określić parametru typu źródła, jego położenie i jego ograniczeń.  
  
### <a name="type-parameter-or-type-argument"></a>Parametr typu lub argumentu typu  
 Aby określić, czy dany element tablicy jest parametrem typu lub argumentu typu, użyj <xref:System.Type.IsGenericParameter%2A> właściwości. <xref:System.Type.IsGenericParameter%2A> Właściwość jest `true` Jeśli element jest parametrem typu.  
  
 Typu ogólnego może być otwarty bez definicji typu ogólnego, w którym to przypadku ma typ argumentów i parametrów typu. Na przykład w poniższym kodzie klasy `D` pochodzi z typu utworzone przez podstawiając pierwszy parametr typu `D` dla drugiego parametru typu `B`.  
  
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
  
 Po uzyskaniu <xref:System.Type> reprezentujący obiekt `D<V, W>` i użyj <xref:System.Type.BaseType%2A> właściwości, aby uzyskać jego typ podstawowy powstałe w ten sposób `type B<int, V>` jest otwarty, ale nie jest definicją typu ogólnego.  
  
### <a name="source-of-a-generic-parameter"></a>Źródło parametru ogólnego  
 Parametr typu ogólnego może pochodzić z typu, które są badanie, typ otaczający lub metody rodzajowej. Można określić źródło parametru typu ogólnego w następujący sposób:  
  
-   Najpierw użyj <xref:System.Type.DeclaringMethod%2A> właściwości w celu określenia, czy parametr typu pochodzi z metody rodzajowej. Jeśli wartość właściwości nie jest odwołanie o wartości null (`Nothing` w języku Visual Basic), następnie źródła jest to metoda ogólna.  
  
-   Jeśli źródło nie jest metodą podstawową, użyj <xref:System.Type.DeclaringType%2A> należy właściwości w celu określenia typu ogólnego parametru typu ogólnego.  
  
 Jeśli parametr typu należy do metody rodzajowej <xref:System.Type.DeclaringType%2A> właściwość zwraca typ zadeklarowany ogólnego metodę, która nie ma znaczenia.  
  
### <a name="position-of-a-generic-parameter"></a>Pozycja parametru ogólnego  
 W rzadkich przypadkach jest niezbędne do określenia pozycji parametr typu na liście parametrów typu jego deklarujący klasy. Na przykład, załóżmy, że masz <xref:System.Type> reprezentujący obiekt `B<int, V>` typu z poprzedniego przykładu. <xref:System.Type.GetGenericArguments%2A> Metoda zawiera listę argumentów typu, a po sprawdzeniu `V` można użyć <xref:System.Type.DeclaringMethod%2A> i <xref:System.Type.DeclaringType%2A> właściwości, aby dowiedzieć się, skąd pochodzą z. Następnie można użyć <xref:System.Type.GenericParameterPosition%2A> właściwości w celu określenia jego pozycji na liście parametrów typu, gdzie został zdefiniowany. W tym przykładzie `V` jest na pozycji 0 (zero) na liście parametrów typu, gdzie został zdefiniowany.  
  
### <a name="base-type-and-interface-constraints"></a>Typ podstawowy i ograniczenia interfejsu  
 Użyj <xref:System.Type.GetGenericParameterConstraints%2A> metodę, aby uzyskać typ podstawowy warunek ograniczający i interfejs ograniczenia parametru typu. Kolejność elementów tablicy nie ma znaczenia. Element reprezentuje ograniczenie interfejsu, jeśli jest to typ interfejsu.  
  
### <a name="generic-parameter-attributes"></a>Atrybuty parametrów ogólnych  
 <xref:System.Type.GenericParameterAttributes%2A> Pobiera właściwość <xref:System.Reflection.GenericParameterAttributes> wartość, która wskazuje wariancję (kowariancja i kontrawariancja) i ograniczeń specjalnych parametru typu.  
  
#### <a name="covariance-and-contravariance"></a>Kowariancja i kontrawariancja  
 Aby ustalić, czy parametr typu jest kowariantnego lub kontrawariantnego, zastosuj <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> maski do <xref:System.Reflection.GenericParameterAttributes> wartość zwracana przez <xref:System.Type.GenericParameterAttributes%2A> właściwości. Jeśli wynik wynosi <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, parametr typu jest niezmienne. Zobacz [Kowariancja i Kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Ograniczeń specjalnych  
 Aby określić specjalne ograniczenia parametru typu, należy zastosować <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> maski do <xref:System.Reflection.GenericParameterAttributes> wartość zwracana przez <xref:System.Type.GenericParameterAttributes%2A> właściwości. Jeśli wynik wynosi <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, istnieją nie ograniczeń specjalnych. Parametr typu może być ograniczona do być typem referencyjnym, typ niedopuszczający wartości null i mieć konstruktora domyślnego.  
  
 [Powrót do początku](#top)  
  
<a name="invariants"></a>   
## <a name="invariants"></a>Invariants  
 Dla tabeli niezmiennej warunków typowe terminy w odbicia dla typów ogólnych, zobacz <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Aby uzyskać dodatkowe postanowienia dotyczące metody ogólne, zobacz <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia](../../../docs/framework/reflection-and-codedom/how-to-examine-and-instantiate-generic-types-with-reflection.md)|Przedstawia sposób użycia właściwości i metod <xref:System.Type> i <xref:System.Reflection.MethodInfo> do sprawdzenia typów ogólnych.|  
|[Typy ogólne](../../../docs/standard/generics/index.md)|Zawiera opis funkcji ogólne i jak jest obsługiwana w programie .NET Framework.|  
|[Instrukcje: definiowanie typu ogólnego przy użyciu emisji odbicia](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|Przedstawia sposób użycia odbicia emisji do generowania typów ogólnych w zestawów dynamicznych.|  
|[Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|W tym artykule opisano <xref:System.Type> klasy i przykłady kodu, które ilustrują sposób użycia <xref:System.Type> z różnymi klasami odbicia, aby uzyskać informacje o konstruktorów, metod, pola, właściwości i zdarzeń.|
