---
title: x:FactoryMethod — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071536"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod — dyrektywa
Określa metodę inną niż konstruktor, której procesor XAML powinien używać do inicjowania obiektu po rozwiązaniu jego typu kopii zapasowej.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Użycie atrybutu XAML, brak argumentów x:Argumenty  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Użycie atrybutu XAML, x:Argumenty jako elementy  
  
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
|`methodname`|Nazwa metody ciągu metody wywoływanej przez procesory XAML w `object`celu zainicjowania wystąpienia określonego jako . Zobacz uwagi.|  
|`oneOrMoreObjectElements`|Jeden lub więcej elementów obiektu dla obiektów, które określają parametry metody fabrycznej. Kolejność jest znacząca; oznacza kolejność, w jakiej argumenty powinny być przekazywane do metody fabrycznej.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `methodname` jest to metoda wystąpienia, nie można jej zakwalifikować.  
  
 Obsługiwane są metody statyczne jako metody fabryczne. Jeśli `methodname` jest metodą `methodname` statyczną, `typeName.methodName` jest dostarczana jako kombinacja, gdzie `typeName` nazwy klasy, która definiuje statyczną metodę fabryczną. `typeName`może być kwalifikowany prefiksem, jeśli odnosi się do typu w mapowanych xmlns. `typeName`może być inny `typeof(object)`typ niż .  
  
 Metoda fabryczna musi być zadeklarowaną metodą publiczną typu, która cofa odpowiedni element obiektu.  
  
 Metoda fabryczna musi zwracać wystąpienie, które można przypisać do odpowiedniego obiektu. Metody fabryczne nigdy nie powinny zwracać wartości null.  
  
 `x:Arguments`działa na zasadzie najlepszego dopasowania do podpisów metod fabrycznych. Dopasowanie najpierw ocenia liczbę parametrów. Jeśli istnieje więcej niż jedno możliwe dopasowanie dla liczby parametrów, typ parametru jest następnie oceniany i określa się najlepsze dopasowanie. Jeśli po tej fazie oceny nadal występują niejednoznaczności, zachowanie procesora XAML jest niezdefiniowane.  
  
 Użycie `x:FactoryMethod` elementu nie jest użycie elementu właściwości w typowym sensie, ponieważ znaczników dyrektywy nie odwołuje się do typu elementu zawierającego obiekt. Oczekuje się, że użycie elementu jest mniej powszechne niż użycie atrybutu. `x:Arguments`(użycie atrybutu lub elementu) może być `x:FactoryMethod` używany wraz z użyciem elementu, ale nie jest to wyraźnie pokazane w sekcjach Użycie.  
  
 `x:FactoryMethod`jako element musi poprzedzać wszelkie inne elementy `x:Arguments` właściwości, musi poprzedzać wszelkie również jako elementy i musi poprzedzać wszelkie content/tekst wewnętrzny/tekst inicjujący.  
  
## <a name="see-also"></a>Zobacz też

- [x:Arguments — dyrektywa](xarguments-directive.md)
