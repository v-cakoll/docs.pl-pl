---
title: "x:FactoryMethod — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58349c5440d0062c64346933e48b64de6c4c7b60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod — dyrektywa
Określa metodę innego niż konstruktor, który procesor XAML powinna być używana do zainicjowania obiektu po rozwiązaniu jego typ zapasowy.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Użycie atrybutu XAML, x: Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Użycie atrybutu XAML, x: Arguments jako elementów:  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`methodname`|Nazwa metody ciąg metody, która procesorów XAML wywołania do inicjowania wystąpienia określony jako `object`. Zobacz uwagi.|  
|`oneOrMoreObjectElements`|Co najmniej jeden element obiektu dla obiektów, które parametry metody fabryki. Kolejność jest znacząca; oznacza on, kolejność, w którym argumenty powinny zostać przekazane do metody fabryki.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `methodname` jest metodą wystąpienia nie może być kwalifikowany.  
  
 Metody statycznej metody fabryki są obsługiwane. Jeśli `methodname` jest metodą statyczną `methodname` jest dostarczane jako *typeName*. *methodName* razem, gdy *typeName* nazwy klasy, która definiuje metody statycznej fabryki. *właściwość typeName* może być prefiks kwalifikowana Jeśli odwołuje się do typu w mapowanej xmlns. *właściwość typeName* może być innego typu niż `typeof(``object``)`.  
  
 Metoda fabryki musi być zadeklarowany publiczną metodę typu, aby utworzyć kopię zapasową elementu odpowiedniego obiektu.  
  
 Metoda fabryki musi zwracać wystąpienie, które można przypisać do odpowiedniego obiektu. Metody fabryki nigdy nie powinien zwrócić wartość null.  
  
 `x:Arguments`działa na zasadzie najlepszego dopasowania dla sygnatury metody fabryki. Dopasowywanie oblicza najpierw liczba parametrów. Jeśli istnieje więcej niż jedno dopasowanie możliwe w dla liczby parametrów, typ parametru jest obliczane i najlepsze dopasowanie jest określana. Jeśli po tym etapie oceny nadal jest niejednoznaczności, zachowanie procesora XAML jest niezdefiniowany.  
  
 `x:FactoryMethod` Użycie elementu nie jest użycie elementu właściwości w tym sensie, typowe, ponieważ znacznika dyrektywy nie odwołuje się do typu zawierającego element object. Oczekuje się użycie tego elementu jest mniej typowych niż użycie atrybutu. `x:Arguments`(użycie atrybutu lub elementu) może być używany wraz z `x:FactoryMethod` użycie elementu, ale nie jest specjalnie widoczne w sekcji użycia.  
  
 `x:FactoryMethod`jako element musi poprzedzać wszystkie inne elementy właściwości, należy poprzedzić żadnego `x:Arguments` również dostarczane jako elementy i musi poprzedzać tekst zawartości/wewnętrzny tekst/inicjowania.  
  
## <a name="see-also"></a>Zobacz też  
 [x:Arguments, dyrektywa](../../../docs/framework/xaml-services/x-arguments-directive.md)
