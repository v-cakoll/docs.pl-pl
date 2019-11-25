---
title: Odbicie i typy ogólne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
ms.openlocfilehash: 0a7d38c8177aa8f2c5f45dcc62a0ae6e5aaca2a7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975451"
---
# <a name="reflection-and-generic-types"></a>Odbicie i typy ogólne
Z punktu widzenia odbicia różnica między typem ogólnym i typem zwykłym polega na tym, że typ ogólny jest skojarzony z tym zestawem parametrów typu (jeśli jest to definicja typu ogólnego) lub argumentów typu (jeśli jest to typ skonstruowany). Metoda ogólna różni się od zwykłej metody w taki sam sposób.  
  
 Istnieją dwa klucze, aby zrozumieć, w jaki sposób odbicie obsługuje typy ogólne i metody:  
  
- Parametry typu definicji typów ogólnych i definicji metod ogólnych są reprezentowane przez wystąpienia klasy <xref:System.Type>.  
  
    > [!NOTE]
    > Wiele właściwości i metod <xref:System.Type> ma inne zachowanie, gdy obiekt <xref:System.Type> reprezentuje parametr typu ogólnego. Te różnice opisano w tematach dotyczących właściwości i metod. Na przykład zobacz <xref:System.Type.IsAutoClass%2A> i <xref:System.Type.DeclaringType%2A>. Ponadto niektóre elementy członkowskie są prawidłowe tylko wtedy, gdy obiekt <xref:System.Type> reprezentuje parametr typu ogólnego. Na przykład zobacz <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
- Jeśli wystąpienie <xref:System.Type> reprezentuje typ ogólny, zawiera tablicę typów reprezentujących parametry typu (dla definicji typu ogólnego) lub argumentów typu (dla konstruowanych typów). Ta sama wartość jest równa wystąpieniu klasy <xref:System.Reflection.MethodInfo>, która reprezentuje metodę rodzajową.  
  
 Odbicie zawiera metody <xref:System.Type> i <xref:System.Reflection.MethodInfo>, które umożliwiają dostęp do tablicy parametrów typu i określanie, czy wystąpienie klasy <xref:System.Type> reprezentuje parametr typu lub rzeczywisty typ.  
  
 Przykładowy kod pokazujący metody omówione tutaj można znaleźć w temacie [How to: badanie i Tworzenie wystąpień typów ogólnych za pomocą odbicia](how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 W poniższej dyskusji założono znajomość terminologii ogólnych, takich jak różnica między parametrami typu a argumentami i otwartymi lub zamkniętymi typami skonstruowanymi. Aby uzyskać więcej informacji, zobacz [Ogólne](../../standard/generics/index.md).  

## <a name="is-this-a-generic-type-or-method"></a>Czy jest to ogólny typ czy metoda?  
 W przypadku użycia odbicia do badania nieznanego typu reprezentowanego przez wystąpienie <xref:System.Type>, użyj właściwości <xref:System.Type.IsGenericType%2A>, aby określić, czy nieznany typ jest ogólny. Zwraca `true`, jeśli typ jest ogólny. Podobnie podczas badania nieznanej metody reprezentowanej przez wystąpienie klasy <xref:System.Reflection.MethodInfo> Użyj właściwości <xref:System.Reflection.MethodBase.IsGenericMethod%2A>, aby określić, czy metoda jest ogólna.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Czy jest to typ ogólny czy definicja metody?  
 Użyj właściwości <xref:System.Type.IsGenericTypeDefinition%2A>, aby określić, czy obiekt <xref:System.Type> reprezentuje definicję typu ogólnego, i użyj metody <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A>, aby określić, czy <xref:System.Reflection.MethodInfo> reprezentuje definicję metody ogólnej.  
  
 Typy ogólne i definicje metod są szablonami, z których tworzone są rodzaje instantiable. Typy ogólne w bibliotece klas .NET Framework, takie jak <xref:System.Collections.Generic.Dictionary%602>, są definicjami typów ogólnych.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Czy typ lub metoda jest otwarta lub ZAMKNIĘTA?  
 Typ ogólny lub metoda jest zamykana, jeśli podinstantiable typy zostały zastąpione dla wszystkich parametrów typu, w tym wszystkich parametrów typu wszystkich typów otaczających. Wystąpienie typu ogólnego można utworzyć tylko wtedy, gdy jest ono zamknięte. Właściwość <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> zwraca `true`, jeśli typ jest otwarty. Dla metod Metoda <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> wykonuje tę samą funkcję.   

## <a name="generating-closed-generic-types"></a>Generowanie zamkniętych typów ogólnych  
 Jeśli masz typ ogólny lub definicję metody, użyj metody <xref:System.Type.MakeGenericType%2A>, aby utworzyć zamknięty typ ogólny lub metodę <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> w celu utworzenia <xref:System.Reflection.MethodInfo> dla zamkniętej metody ogólnej.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Pobieranie typu ogólnego lub definicji metody  
 Jeśli masz otwarty typ ogólny lub metodę, która nie jest typem ogólnym lub definicją metody, nie można utworzyć wystąpień tego wystąpienia i nie można podać parametrów typu, które nie są spełnione. Musisz mieć typ ogólny lub definicję metody. Użyj metody <xref:System.Type.GetGenericTypeDefinition%2A>, aby uzyskać definicję typu ogólnego lub metodę <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> w celu uzyskania definicji metody ogólnej.  
  
 Na przykład jeśli masz obiekt <xref:System.Type> reprezentujący `Dictionary<int, string>` (`Dictionary(Of Integer, String)` w Visual Basic) i chcesz utworzyć typ `Dictionary<string, MyClass>`, można użyć metody <xref:System.Type.GetGenericTypeDefinition%2A>, aby uzyskać <xref:System.Type> reprezentującą `Dictionary<TKey, TValue>`, a następnie użyć metody <xref:System.Type.MakeGenericType%2A> do utworzenia <xref:System.Type> reprezentującego `Dictionary<int, MyClass>`.  
  
 Przykład otwartego typu ogólnego, który nie jest typem ogólnym, znajduje się w dalszej części tego tematu.   

## <a name="examining-type-arguments-and-type-parameters"></a>Badanie argumentów typu i parametrów typu  
 Użyj metody <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType>, aby uzyskać tablicę obiektów <xref:System.Type>, które reprezentują parametry typu lub argumenty typu ogólnego, i użyj metody <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType>, aby wykonać te same czynności dla metody ogólnej.  
  
 Gdy wiesz, że obiekt <xref:System.Type> reprezentuje parametr typu, można odpowiedzieć na wiele dodatkowych pytań. Można określić źródło parametru typu, jego pozycję i jego ograniczenia.  
  
### <a name="type-parameter-or-type-argument"></a>Parametr typu lub argument typu  
 Aby określić, czy konkretny element tablicy jest parametrem typu, czy typem argumentu, użyj właściwości <xref:System.Type.IsGenericParameter%2A>. Właściwość <xref:System.Type.IsGenericParameter%2A> jest `true`, jeśli element jest parametrem typu.  
  
 Typ ogólny może być otwarty bez standardowej definicji typu, w którym to przypadku ma kombinację argumentów typu i parametrów typu. Na przykład, w poniższym kodzie Klasa `D` pochodzi od typu utworzonego przez podstawianie pierwszego parametru typu `D` dla drugiego parametru typu `B`.  
  
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
  
 Jeśli zostanie uzyskany obiekt <xref:System.Type> reprezentujący `D<V, W>` i użycie właściwości <xref:System.Type.BaseType%2A> w celu uzyskania typu podstawowego, wynikiem `type B<int, V>` jest otwarty, ale nie jest to definicja typu ogólnego.  
  
### <a name="source-of-a-generic-parameter"></a>Źródło parametru generycznego  
 Parametry typu ogólnego mogą pochodzić z typu, który badasz, z typu otaczającego lub z metody ogólnej. Źródło parametru typu ogólnego można określić w następujący sposób:  
  
- Najpierw użyj właściwości <xref:System.Type.DeclaringMethod%2A>, aby określić, czy parametr typu pochodzi z metody ogólnej. Jeśli wartość właściwości nie jest odwołaniem null (`Nothing` w Visual Basic), źródłem jest metoda ogólna.  
  
- Jeśli źródłem nie jest metoda generyczna, użyj właściwości <xref:System.Type.DeclaringType%2A>, aby określić typ ogólny, do którego należy parametr typu ogólnego.  
  
 Jeśli parametr typu należy do metody ogólnej, właściwość <xref:System.Type.DeclaringType%2A> zwraca typ, który deklaruje metodę rodzajową, która jest istotna.  
  
### <a name="position-of-a-generic-parameter"></a>Pozycja parametru generycznego  
 W rzadkich sytuacjach należy określić pozycję parametru typu na liście parametrów typu swojej klasy deklarującej. Załóżmy na przykład, że masz obiekt <xref:System.Type> reprezentujący typ `B<int, V>` z poprzedniego przykładu. Metoda <xref:System.Type.GetGenericArguments%2A> zapewnia listę argumentów typu, a podczas badania `V` można użyć właściwości <xref:System.Type.DeclaringMethod%2A> i <xref:System.Type.DeclaringType%2A> do odnajdywania, z których pochodzi. Następnie można użyć właściwości <xref:System.Type.GenericParameterPosition%2A> do określenia jej pozycji na liście parametrów typu, gdzie została zdefiniowana. W tym przykładzie `V` znajduje się na pozycji 0 (zero) na liście parametrów typu, w której został zdefiniowany.  
  
### <a name="base-type-and-interface-constraints"></a>Ograniczenia typu podstawowego i interfejsu  
 Użyj metody <xref:System.Type.GetGenericParameterConstraints%2A>, aby uzyskać ograniczenia dotyczące typu podstawowego i ograniczeń interfejsu parametru typu. Kolejność elementów tablicy nie jest istotna. Element reprezentuje ograniczenie interfejsu, jeśli jest typem interfejsu.  
  
### <a name="generic-parameter-attributes"></a>Atrybuty parametru generycznego  
 Właściwość <xref:System.Type.GenericParameterAttributes%2A> Pobiera wartość <xref:System.Reflection.GenericParameterAttributes>, która wskazuje wariancję (kowariancję lub kontrawariancja) oraz specjalne ograniczenia parametru typu.  
  
#### <a name="covariance-and-contravariance"></a>Kowariancja i kontrawariancja  
 Aby określić, czy parametr typu jest współvariant lub kontrawariantne, Zastosuj maskę <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> do wartości <xref:System.Reflection.GenericParameterAttributes>, która jest zwracana przez właściwość <xref:System.Type.GenericParameterAttributes%2A>. Jeśli wynik jest <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, parametr typu jest niezmienny. Zobacz [Kowariancja i kontrawariancja](../../standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Ograniczenia specjalne  
 Aby określić specjalne ograniczenia parametru typu, Zastosuj maskę <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> do wartości <xref:System.Reflection.GenericParameterAttributes>, która jest zwracana przez właściwość <xref:System.Type.GenericParameterAttributes%2A>. Jeśli wynik jest <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, nie ma żadnych specjalnych ograniczeń. Parametr typu może być ograniczony jako typ referencyjny, jako typ wartości niedopuszczający wartości null i mieć konstruktora bez parametrów.    

## <a name="invariants"></a>Nieposiadające wariantów  
 Aby zapoznać się z tabelą warunków niezmiennej dla typowych warunków odbicia dla typów ogólnych, zobacz <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Aby uzyskać dodatkowe warunki dotyczące metod ogólnych, zobacz <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  

## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia](how-to-examine-and-instantiate-generic-types-with-reflection.md)|Pokazuje, jak używać właściwości i metod <xref:System.Type> i <xref:System.Reflection.MethodInfo> do badania typów ogólnych.|  
|[Typy ogólne](../../standard/generics/index.md)|Opisuje funkcję generyczną i sposób jej obsługi w .NET Framework.|  
|[Instrukcje: definiowanie typu ogólnego przy użyciu emisji odbicia](how-to-define-a-generic-type-with-reflection-emit.md)|Pokazuje, jak używać emisji odbicia do generowania typów ogólnych w zestawach dynamicznych.|  
|[Wyświetlanie informacji o typie](viewing-type-information.md)|Opisuje klasę <xref:System.Type> i zawiera przykłady kodu, które ilustrują sposób użycia <xref:System.Type> z różnymi klasami odbicia w celu uzyskania informacji dotyczących konstruktorów, metod, pól, właściwości i zdarzeń.|
