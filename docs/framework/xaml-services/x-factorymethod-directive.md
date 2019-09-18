---
title: x:FactoryMethod — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053773"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod — dyrektywa
Określa metodę inną niż Konstruktor, który powinien być używany przez procesor XAML do inicjowania obiektu po rozwiązaniu jego typu zapasowego.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Użycie atrybutu języka XAML, brak X:arguments —  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Użycie atrybutu języka XAML, X:arguments — jako elementy  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`methodname`|Nazwa metody ciągu metody, którą procesory XAML wywołują w celu zainicjowania wystąpienia określonego jako `object`. Zobacz uwagi.|  
|`oneOrMoreObjectElements`|Co najmniej jeden element obiektu dla obiektów, które określają parametry metody fabryki. Kolejność jest istotna. oznacza kolejność, w jakiej argumenty powinny być przekazane do metody fabryki.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `methodname` jest to metoda wystąpienia, nie może być kwalifikowana.  
  
 Metody statyczne jako metody fabryki są obsługiwane. If `methodname` jest metodą statyczną, `methodname` jest podana jako *TypeName*. *kombinacja methodName* , gdzie *TypeName* nazywa klasę, która definiuje metodę dla fabryki statycznej. *Właściwość TypeName* może być kwalifikowana przy użyciu prefiksu, jeśli odwołuje się do typu w zmapowanym xmlns. Typ *TypeName* może być inny niż `typeof(object)`.  
  
 Metoda fabryki musi być zadeklarowaną metodą publiczną typu, który wykonuje kopię zapasową odpowiedniego elementu obiektu.  
  
 Metoda fabryki musi zwracać wystąpienie, które można przypisać do odpowiedniego obiektu. Metody fabryki nigdy nie powinny zwracać wartości null.  
  
 `x:Arguments`działa na zasadzie najlepszego dopasowania dla sygnatur metod fabryki. Dopasowanie najpierw oblicza liczbę parametrów. Jeśli istnieje więcej niż jedno możliwe dopasowanie liczby parametrów, typ parametru jest następnie oceniany i jest określany optymalny odpowiednik. Jeśli po tej fazie oceny nadal występuje niejednoznaczność, zachowanie procesora XAML nie jest zdefiniowane.  
  
 Użycie `x:FactoryMethod` elementu nie jest użyciem elementu właściwości w typowym sensie, ponieważ znacznik dyrektywy nie odwołuje się do typu elementu obiektu zawierającego. Oczekuje się, że użycie elementu jest mniej typowe niż użycie atrybutu. `x:Arguments`(użycie atrybutu lub elementu) może być używane razem z `x:FactoryMethod` użyciem elementu, ale nie jest to pokazane w sekcjach użycia.  
  
 `x:FactoryMethod`jako element musi poprzedzać wszystkie inne elementy właściwości, muszą poprzedzać `x:Arguments` wszelkie elementy, które również muszą poprzedzać dowolny tekst zawartości/wewnętrznego tekstu inicjującego.  
  
## <a name="see-also"></a>Zobacz także

- [x:Arguments, dyrektywa](x-arguments-directive.md)
