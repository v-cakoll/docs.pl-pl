---
title: x:FactoryMethod — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 436caa9b93467dcf2a0763bcc0962a2beb722315
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397533"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod — dyrektywa
Określa metody innej niż konstruktora, który procesor XAML powinna być używana do inicjowania obiektu po rozwiązaniu jego zapasowego typu.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Użycie atrybutu XAML, x: Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Użycie atrybutu XAML, x: Arguments, jako elementów:  
  
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
|`methodname`|Nazwa metody parametry metody, która procesorów XAML wywołania do inicjowania wystąpienia określony jako `object`. Zobacz uwagi.|  
|`oneOrMoreObjectElements`|Co najmniej jeden element obiektu dla obiektów, które określają parametry metody fabryki. Kolejność jest znacząca; oznacza kolejność, w której argumenty powinien zostać przekazany do metody fabryki.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `methodname` jest metodą wystąpienia nie może być kwalifikowana.  
  
 Metody statyczne służące jako metodami factory są obsługiwane. Jeśli `methodname` jest statycznej metody `methodname` jest dostarczana jako *typeName*. *methodName* kombinacji, gdzie *typeName* nazwy klasy, która definiuje metody statyczne fabryki. *Element typeName* może być prefiksem kwalifikowanego Jeśli odwołujące się do typu w mapowanych xmlns. *Element typeName* może być typ inny niż `typeof(object)`.  
  
 Metoda fabryki musi być zadeklarowany publiczną metodę typu, która będzie tworzyć kopię elementu odpowiedniego obiektu.  
  
 Metoda fabryki musi zwrócić wystąpienie, które można przypisać do odpowiedniego obiektu. Metodami Factory nigdy nie powinna zwracać wartość null.  
  
 `x:Arguments` działa na zasadzie najlepiej dopasowana podpisy metod fabryki. Dopasowywanie najpierw sprawdza liczba parametrów. Jeśli istnieje więcej niż jeden odpowiadającego liczba parametrów, typ parametru jest następnie oceniany i najlepsze dopasowanie jest określana. Jeśli po tym etapie oceny nadal jest niejednoznaczności, XAML procesora zachowanie jest niezdefiniowane.  
  
 `x:FactoryMethod` Użycie elementu nie jest użycie elementu właściwości w tym sensie, typowe, ponieważ znaczników dyrektywy nie odwołuje się do typu elementu obiektu nadrzędnego. Oczekuje się, że użycie elementu jest rzadziej niż użycie atrybutu. `x:Arguments` (użycie atrybutu lub elementu) może być używana wraz z `x:FactoryMethod` użycie elementu, ale nie jest specjalnie wyświetlany w sekcji użycia.  
  
 `x:FactoryMethod` jako element musi poprzedzać wszystkie inne elementy właściwości, należy poprzedzić dowolne `x:Arguments` również dostarczane jako elementy, a musi poprzedzać dowolny tekst zawartości/wewnętrzny tekst/inicjowania.  
  
## <a name="see-also"></a>Zobacz też  
 [x:Arguments, dyrektywa](../../../docs/framework/xaml-services/x-arguments-directive.md)
