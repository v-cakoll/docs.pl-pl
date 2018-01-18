---
title: "Ograniczenia dotyczące parametrów typu (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: "41"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f5382b0050b81ed3bb1a075a042bdc4034a3975d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Ograniczenia dotyczące parametrów typu (Przewodnik programowania w języku C#)
Podczas definiowania klasy ogólnej, można zastosować ograniczenia do rodzajów typów, których kod klienta można używać dla argumentów typu podczas tworzenia wystąpień klasy. Jeśli kod klienta próbuje utworzyć wystąpienia klasy przy użyciu typu, który nie jest dozwolona przez ograniczenie, wynikiem jest błąd kompilacji. Ograniczenia te są nazywane ograniczenia. Ograniczenia są określane przy użyciu `where` kontekstowe słowo kluczowe. W poniższej tabeli wymieniono sześć typy ograniczeń:  
  
|Ograniczenia|Opis|  
|----------------|-----------------|  
|where T: struct|Argument typu musi być typem wartości. Wszystkie wartości typu z wyjątkiem <xref:System.Nullable> można określić. Zobacz [przy użyciu typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/using-nullable-types.md) Aby uzyskać więcej informacji.|  
|where T: class|Argument typu musi być typu referencyjnego; dotyczy to również klasy, interfejsu, delegata lub typ tablicy.|  
|where T: new()|Typ argumentu musi mieć publicznego konstruktora bez parametrów. Gdy jest używany z innymi ograniczeniami `new()` ograniczenie musi być określony jako ostatni.|  
|where T: \<nazwę klasy podstawowej >|Argument typu musi być lub pochodzić od określonej klasy podstawowej.|  
|where T: \<Nazwa interfejsu >|Argument typu muszą być lub implementować określonego interfejsu. Można określić wiele ograniczeń interfejsu. Można też ogólnego ograniczający interfejsu.|  
|where T: U|Argumentu typu dostarczonego T musi być lub pochodzić od argument dostarczony dla U.|  
  
## <a name="why-use-constraints"></a>Dlaczego warto korzystać z ograniczeniami  
 Jeśli chcesz sprawdzić element listy ogólnej do ustalenia, czy jest nieprawidłowy lub porównaj je z inny element, kompilator musi mieć niektóre gwarantuje, że operator lub metoda, który musi wywołać będą obsługiwane przez wszystkich argumentów typu określoną przez co klient Niemcy. Gwarancji są uzyskiwane przez zastosowanie jednego lub więcej ograniczeń do definicji klasy ogólnej. Na przykład ograniczenie klasy podstawowej informuje kompilator, że tylko obiekty tego typu lub pochodzi z tego typu, będzie można używać jako argumentów typu. Kompilator ma gwarancji, umożliwiają metody tego typu można wywołać w klasie rodzajowej. Ograniczenia są stosowane przy użyciu kontekstowe słowo kluczowe `where`. Poniższy przykład kodu pokazuje funkcji, można dodać do `GenericList<T>` klasy (w [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)), stosując ograniczenie klasy podstawowej.  
  
 [!code-csharp[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 Klasy ogólnej użyć umożliwia ograniczenie `Employee.Name` właściwości, ponieważ wszystkie elementy typu T zapewniona jest albo `Employee` lub obiektu, który dziedziczy z `Employee`.  
  
 Wiele ograniczeń można zastosować do tego samego parametru typu, a same ograniczenia może mieć typów ogólnych w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 Ograniczający parametr typu, powoduje zwiększenie liczby operacji w dozwolonym i wywołania metody do obsługiwanych przez ograniczającego typu i wszystkie typy w jej hierarchii dziedziczenia. W związku z tym podczas projektowania klas ogólnego lub metody, jeśli operacji na ogólnych elementów członkowskich poza przypisanie proste lub wywoływania żadnych metod, które nie są obsługiwane przez `System.Object`, należy zastosować ograniczenia do parametru typu.  
  
 Podczas stosowania `where T : class` ograniczenia, należy unikać `==` i `!=` operatory w parametrze typu ponieważ tych operatorów sprawdza tożsamości odwołania, nie dla równości wartości. Dotyczy to nawet wtedy, gdy te operatory są przeciążone w typie, który jest używany jako argument. Poniższy kod ilustruje tę sytuację; nawet jeśli dane wyjściowe ma wartość false <xref:System.String> klasy przeciążenia `==` operatora.  
  
 [!code-csharp[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 Przyczyna to zachowanie jest, że w czasie kompilacji, kompilator tylko zna T jest typem referencyjnym czy w związku z tym należy użyć domyślnych operatorów, które są prawidłowe dla wszystkich typów odniesienia. Jeśli konieczne jest przetestowanie wartość pod kątem równości, zalecaną metodą jest również zastosować `where T : IComparable<T>` ograniczenia i wdrożenie, które interfejs w dowolnej klasy, która ma być użyty do utworzenia klasy ogólnej.  
  
## <a name="constraining-multiple-parameters"></a>Ograniczający wiele parametrów  
 Wiele parametrów, a wiele ograniczeń na jeden parametr, można zastosować ograniczenia, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## <a name="unbounded-type-parameters"></a>Parametry typu niepowiązanego  
 Wpisz parametry, które mają żadne ograniczenia, takie jak T w publicznej klasy `SampleClass<T>{}`, są nazywane parametrów niepowiązanego typu. Parametry typu niepowiązanego mają następujące reguły:  
  
-   `!=` i `==` nie można używać operatorów, ponieważ nie ma żadnej gwarancji, że argument typu konkretnego będzie obsługiwać tych operatorów.  
  
-   Może być przekonwertowany do i z `System.Object` lub jawnie przekonwertowane do dowolnego typu interfejsu.  
  
-   Możesz porównać [null](../../../csharp/language-reference/keywords/null.md). Jeśli jest porównywany niepowiązany parametr `null`, porównanie zawsze zwróci wartość false, jeśli argument Typ jest typem wartości.  
  
## <a name="type-parameters-as-constraints"></a>Parametry typu jako ograniczenia  
 Użyj parametru typu ogólnego jako ograniczenie jest przydatne w przypadku funkcji członkowskiej z własną parametr typu ma ograniczenie parametru typu parametru typu zawierającego, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 W poprzednim przykładzie `T` ograniczenie typu w kontekście `Add` — metoda i parametr niepowiązanego typu w kontekście `List` klasy.  
  
 Parametry typu mogą służyć jako ograniczeń w definicji klasy ogólnej. Należy pamiętać, że parametr typu musi być zadeklarowana w nawiasy razem z innymi parametrami typu:  
  
 [!code-csharp[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 Przydatność parametrów typu jako ograniczenia z klas ogólnych jest bardzo ograniczona, ponieważ kompilator można założyć, nie ma parametru typu z tą różnicą, że pochodzi od `System.Object`. Parametry typu jako ograniczenia dotyczące klas ogólnych w scenariuszach, w których chcesz wymusić relację dziedziczenia między dwoma parametrami typu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Klasy ogólne](../../../csharp/programming-guide/generics/generic-classes.md)  
 [New — ograniczenie](../../../csharp/language-reference/keywords/new-constraint.md)
