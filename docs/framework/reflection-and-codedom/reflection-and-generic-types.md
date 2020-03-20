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
ms.openlocfilehash: 4894b5cc64dca431c8d05b638847dd6cb7017bde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180497"
---
# <a name="reflection-and-generic-types"></a>Odbicie i typy ogólne
Z punktu widzenia odbicia różnica między typem rodzajowym a zwykłym typem polega na tym, że typ ogólny skojarzył z nim zestaw parametrów typu (jeśli jest to definicja typu ogólnego) lub argumenty typu (jeśli jest to typ skonstruowany). Metoda rodzajowa różni się od zwykłej metody w ten sam sposób.  
  
 Istnieją dwa klucze do zrozumienia, jak odbicie obsługuje typy ogólne i metody:  
  
- Parametry typu definicje typów ogólnych i definicje metod rodzajowych <xref:System.Type> są reprezentowane przez wystąpienia klasy.  
  
    > [!NOTE]
    > Wiele właściwości i <xref:System.Type> metody mają różne <xref:System.Type> zachowanie, gdy obiekt reprezentuje parametr typu ogólnego. Różnice te są udokumentowane w tematach właściwości i metody. Na przykład <xref:System.Type.IsAutoClass%2A> zobacz <xref:System.Type.DeclaringType%2A>i . Ponadto niektóre elementy członkowskie są <xref:System.Type> prawidłowe tylko wtedy, gdy obiekt reprezentuje parametr typu ogólnego. Na przykład <xref:System.Type.GetGenericTypeDefinition%2A>zobacz .  
  
- Jeśli wystąpienie <xref:System.Type> reprezentuje typ ogólny, zawiera tablicę typów, które reprezentują parametry typu (dla definicji typów ogólnych) lub argumenty typu (dla typów konstruowanych). To samo dotyczy wystąpienia <xref:System.Reflection.MethodInfo> klasy, która reprezentuje metodę rodzajową.  
  
 Odbicie zapewnia <xref:System.Type> <xref:System.Reflection.MethodInfo> metody i które umożliwiają dostęp do tablicy parametrów <xref:System.Type> typu i określić, czy wystąpienie reprezentuje parametr typu lub typ rzeczywisty.  
  
 Na przykład kod demonstrujący metody omówione w tym miejscu, zobacz [Jak: Badanie i tworzenie wystąpienia typów ogólnych za pomocą odbicia](how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 W poniższej dyskusji przyjęto założenie, że jest zaznajomiona z terminologią rodzajowych, takich jak różnica między parametrami typu i argumentami oraz typy konstruowane otwarte lub zamknięte. Aby uzyskać więcej informacji, zobacz [Ogólne](../../standard/generics/index.md).  

## <a name="is-this-a-generic-type-or-method"></a>Czy jest to typ ogólny lub metoda?  
 Podczas korzystania z odbicia do zbadania nieznanego <xref:System.Type>typu, <xref:System.Type.IsGenericType%2A> reprezentowane przez wystąpienie , użyj właściwości, aby ustalić, czy nieznany typ jest ogólny. Zwraca, `true` jeśli typ jest ogólny. Podobnie podczas badania nieznanej metody, reprezentowane przez <xref:System.Reflection.MethodInfo> wystąpienie klasy, należy użyć <xref:System.Reflection.MethodBase.IsGenericMethod%2A> właściwości, aby ustalić, czy metoda jest rodzajowy.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>Czy jest to rodzajowy typ lub definicja metody?  
 Użyj <xref:System.Type.IsGenericTypeDefinition%2A> właściwości, aby <xref:System.Type> ustalić, czy obiekt reprezentuje definicję typu ogólnego i użyj <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> metody, aby określić, czy reprezentuje definicję <xref:System.Reflection.MethodInfo> metody rodzajowej.  
  
 Definicje typów i metod ogólnych to szablony, z których tworzone są typy wystąpienia. Typy ogólne w bibliotece klas <xref:System.Collections.Generic.Dictionary%602>programu .NET Framework, takie jak , są definicjami typów ogólnych.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Czy typ lub metoda jest otwarta lub zamknięta?  
 Typ lub metoda rodzajowa jest zamykana, jeśli typy wystąpienia zostały zastąpione dla wszystkich parametrów typu, w tym wszystkich parametrów typu wszystkich typów otaczających. Wystąpienie typu ogólnego można utworzyć tylko wtedy, gdy jest zamknięte. Właściwość <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> `true` zwraca, jeśli typ jest otwarty. Dla metod <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> metoda wykonuje tę samą funkcję.

## <a name="generating-closed-generic-types"></a>Generowanie zamkniętych typów ogólnych  
 Po uzyskaniu definicji typu ogólnego lub <xref:System.Type.MakeGenericType%2A> metody użyj tej metody, <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> aby utworzyć <xref:System.Reflection.MethodInfo> zamknięty typ ogólny lub metodę tworzenia zamkniętej metody ogólnej.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Uzyskiwanie definicji typu ogólnego lub metody  
 Jeśli masz otwarty typ ogólny lub metodę, która nie jest typem rodzajowym lub definicją metody, nie można utworzyć jego wystąpień i nie można podać parametrów typu, których brakuje. Musisz mieć rodzajowy typ lub definicję metody. Użyj <xref:System.Type.GetGenericTypeDefinition%2A> tej metody, aby uzyskać <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> definicję typu ogólnego lub metodę, aby uzyskać definicję metody ogólnej.  
  
 Na przykład, jeśli <xref:System.Type> masz obiekt `Dictionary<int, string>` `Dictionary(Of Integer, String)` reprezentujący (w języku Visual Basic) i `Dictionary<string, MyClass>`chcesz <xref:System.Type.GetGenericTypeDefinition%2A> utworzyć typ, możesz użyć tej metody, <xref:System.Type> aby `Dictionary<int, MyClass>`uzyskać reprezentację, <xref:System.Type> `Dictionary<TKey, TValue>` a następnie użyć <xref:System.Type.MakeGenericType%2A> tej metody do utworzenia reprezentującego .  
  
 Na przykład otwartego typu ogólnego, który nie jest typem rodzajowym, zobacz "Parametr typu lub argument typu" w dalszej części tego tematu.

## <a name="examining-type-arguments-and-type-parameters"></a>Badanie argumentów typu i parametrów typu  
 Użyj <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> tej metody, aby <xref:System.Type> uzyskać tablicę obiektów, które reprezentują parametry typu <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> lub argumenty typu typu ogólnego i użyj metody, aby zrobić to samo dla metody ogólnej.  
  
 Gdy wiadomo, <xref:System.Type> że obiekt reprezentuje parametr typu, istnieje wiele dodatkowych pytań, na które można odpowiedzieć. Można określić źródło parametru typu, jego położenie i jego ograniczenia.  
  
### <a name="type-parameter-or-type-argument"></a>Parametr typu lub argument typu  
 Aby ustalić, czy określony element tablicy jest parametrem typu <xref:System.Type.IsGenericParameter%2A> lub argumentem typu, należy użyć właściwości. Właściwość <xref:System.Type.IsGenericParameter%2A> `true` jest, jeśli element jest parametrem typu.  
  
 Typ ogólny może być otwarty bez definicji typu ogólnego, w którym to przypadku ma mieszaninę argumentów typu i parametrów typu. Na przykład w poniższym `D` kodzie klasa wywodzi się od typu `D` utworzonego przez `B`zastąpienie pierwszego parametru typu dla drugiego parametru typu .  
  
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
  
 Jeśli uzyskasz <xref:System.Type> obiekt `D<V, W>` reprezentujący <xref:System.Type.BaseType%2A> i użyjesz właściwości, aby `type B<int, V>` uzyskać jego typ podstawowy, wynikowy jest otwarty, ale nie jest definicją typu ogólnego.  
  
### <a name="source-of-a-generic-parameter"></a>Źródło parametru ogólnego  
 Parametr typu ogólnego może pochodzić z typu, który są sprawdzane, z otaczającego typu lub z metody rodzajowej. Źródło parametru typu ogólnego można określić w następujący sposób:  
  
- Najpierw należy <xref:System.Type.DeclaringMethod%2A> użyć właściwości, aby ustalić, czy parametr type pochodzi z metody rodzajowej. Jeśli wartość właściwości nie jest`Nothing` odwołaniem null (w języku Visual Basic), to źródło jest metodą rodzajową.  
  
- Jeśli źródło nie jest metodą <xref:System.Type.DeclaringType%2A> rodzajową, należy użyć właściwości, aby określić typ ogólny, do którego należy parametr typu ogólnego.  
  
 Jeśli parametr type należy do metody <xref:System.Type.DeclaringType%2A> rodzajowej, właściwość zwraca typ, który zadeklarował metodę rodzajową, która jest nieistotna.  
  
### <a name="position-of-a-generic-parameter"></a>Położenie parametru ogólnego  
 W rzadkich sytuacjach konieczne jest określenie pozycji parametru typu na liście parametrów typu jego klasy deklarującej. Załóżmy na przykład, że masz <xref:System.Type> obiekt reprezentujący `B<int, V>` typ z poprzedniego przykładu. Metoda <xref:System.Type.GetGenericArguments%2A> daje listę argumentów typu, a `V` podczas badania <xref:System.Type.DeclaringMethod%2A> można <xref:System.Type.DeclaringType%2A> użyć i właściwości, aby odkryć, skąd pochodzi. Następnie można użyć <xref:System.Type.GenericParameterPosition%2A> właściwości, aby określić jego położenie na liście parametrów typu, gdzie została zdefiniowana. W tym `V` przykładzie znajduje się w pozycji 0 (zero) na liście parametrów typu, gdzie został zdefiniowany.  
  
### <a name="base-type-and-interface-constraints"></a>Wiązania typu podstawowego i interfejsu  
 Użyj <xref:System.Type.GetGenericParameterConstraints%2A> metody, aby uzyskać ograniczenie typu podstawowego i ograniczenia interfejsu parametru typu. Kolejność elementów tablicy nie jest znacząca. Element reprezentuje ograniczenie interfejsu, jeśli jest typem interfejsu.  
  
### <a name="generic-parameter-attributes"></a>Atrybuty parametrów ogólnych  
 Właściwość <xref:System.Type.GenericParameterAttributes%2A> pobiera <xref:System.Reflection.GenericParameterAttributes> wartość, która wskazuje wariancję (kowariancja lub kontrawarancja) i specjalne ograniczenia parametru typu.  
  
#### <a name="covariance-and-contravariance"></a>Kowariancja i kontrawariancja  
 Aby ustalić, czy parametr typu jest kowariancyjny lub <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> kontrawariant, zastosuj maskę do <xref:System.Reflection.GenericParameterAttributes> wartości zwracana <xref:System.Type.GenericParameterAttributes%2A> przez właściwość. Jeśli wynik <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>jest , parametr typu jest niezmienny. Zobacz [Covariance i Contravariance](../../standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Ograniczenia specjalne  
 Aby określić specjalne ograniczenia parametru typu, zastosuj maskę <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> do <xref:System.Reflection.GenericParameterAttributes> wartości zwracanej <xref:System.Type.GenericParameterAttributes%2A> przez właściwość. Jeśli wynik <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>jest , nie ma żadnych specjalnych ograniczeń. Parametr typu może być powiązany jako typ odwołania, jest typem wartości nienastępującym do wartości i ma konstrukcję bez parametrów.

## <a name="invariants"></a>Invariants  
 Aby zapoznać się z tabelą niezmiennych warunków wspólnych terminów w refleksji dla typów ogólnych, zobacz <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Dodatkowe terminy odnoszące się <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>do metod ogólnych można znaleźć w pliku .  

## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia](how-to-examine-and-instantiate-generic-types-with-reflection.md)|Pokazuje, jak używać właściwości i <xref:System.Type> <xref:System.Reflection.MethodInfo> metod i do badania typów ogólnych.|  
|[Typy ogólne](../../standard/generics/index.md)|W tym artykule opisano funkcję generics i sposób jej obsługi w ramach .NET Framework.|  
|[Instrukcje: definiowanie typu ogólnego przy użyciu emisji odbicia](how-to-define-a-generic-type-with-reflection-emit.md)|Pokazuje, jak używać odbicia emitować do generowania typów ogólnych w zestawach dynamicznych.|  
|[Wyświetlanie informacji o typie](viewing-type-information.md)|W <xref:System.Type> tym artykule opisano klasę i zawiera <xref:System.Type> przykłady kodu, które ilustrują, jak używać z różnych klas odbić, aby uzyskać informacje na temat konstruktorów, metod, pól, właściwości i zdarzeń.|
