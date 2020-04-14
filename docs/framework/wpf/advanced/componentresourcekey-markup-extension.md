---
title: ComponentResourceKey — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243365"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey — Rozszerzenie znaczników
Definiuje i odwołuje się do kluczy dla zasobów, które są ładowane z zestawów zewnętrznych. Dzięki temu wyszukiwanie zasobów, aby określić typ obiektu docelowego w zestawie, a nie jawny słownik zasobów w zestawie lub w klasie.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Użycie atrybutu XAML (klucz ustawień, kompaktowy)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Użycie atrybutu XAML (klucz ustawień, pełne)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Użycie atrybutu XAML (żądanie zasobu, kompaktowy)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Użycie atrybutu XAML (żądanie zasobu, pełne)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`targetTypeName`|Nazwa typu środowiska wykonawczego języka powszechnego (CLR), który jest zdefiniowany w zestawie zasobów.|  
|`targetID`|Klucz dla zasobu. Gdy zasoby są wyszukane, `targetID` będzie analogiczna do [x:Key dyrektywy](../../../desktop-wpf/xaml-services/xkey-directive.md) zasobu.|  
  
## <a name="remarks"></a>Uwagi  
 Jak widać w powyższych zastosowaniach, użycie rozszerzenia znaczników {`ComponentResourceKey`} znajduje się w dwóch miejscach:  
  
- Definicja klucza w słowniku zasobów motywu, dostarczone przez autora kontroli.  
  
- Uzyskiwanie dostępu do zasobu motywu z zestawu, gdy są retemplating formantu, ale chcesz użyć wartości właściwości, które pochodzą z zasobów dostarczonych przez formantu tematów.  
  
 W przypadku odwoływania się do zasobów składowych pochodzących `{DynamicResource}` z `{StaticResource}`motywów zaleca się użycie, a nie użycie . Jest to pokazane w użyciach. `{DynamicResource}`jest zalecane, ponieważ sam motyw może być zmieniony przez użytkownika. Jeśli chcesz, aby zasób składnika, który najbardziej odpowiada intencji autora formantu do obsługi motywu, należy włączyć odwołanie do zasobu składnika być dynamiczne również.  
  
 Identyfikuje <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> typ, który istnieje w zestawie docelowym, gdzie zasób jest faktycznie zdefiniowany. A `ComponentResourceKey` mogą być definiowane i używane niezależnie <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> od wiedząc dokładnie, gdzie jest zdefiniowany, ale ostatecznie musi rozwiązać typ za pomocą zestawów, do których istnieje odwołanie.  
  
 Typowym zastosowaniem <xref:System.Windows.ComponentResourceKey> jest zdefiniowanie kluczy, które są następnie udostępniane jako członkowie klasy. W tym celu należy <xref:System.Windows.ComponentResourceKey> użyć konstruktora klasy, a nie rozszerzenia znaczników. Aby uzyskać więcej <xref:System.Windows.ComponentResourceKey>informacji, zobacz sekcję "Definiowanie i odwoływanie się do kluczy dla zasobów motywu" w temacie [Omówienie tworzenia formantu](../controls/control-authoring-overview.md).  
  
 W przypadku zarówno ustanawiania kluczy, jak i odwoływania się `ComponentResourceKey` do zasobów z kluczami składnia atrybutów jest często używana dla rozszerzenia znaczników.  
  
 Przedstawiona składnia kompaktowa <xref:System.Windows.ComponentResourceKey.%23ctor%2A> opiera się na użyciu sygnatury konstruktora i parametru pozycyjnego rozszerzenia znaczników. Ważna jest kolejność, w jakiej `targetTypeName` i `targetID` są podane. Składnia pełnej opiera się na <xref:System.Windows.ComponentResourceKey.%23ctor%2A> konstruktorze bez parametrów, a następnie ustawia <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> w sposób, który jest analogiczny do składni atrybutu true na element obiektu. W składni pełnej kolejność, w której właściwości są ustawione nie jest ważne. Relacja i mechanizmy tych dwóch alternatyw (kompaktowych i pełnych) opisano bardziej szczegółowo w temacie [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Technicznie wartość dla `targetID` może być dowolny obiekt, nie musi być ciąg. Jednak najczęstszym zastosowaniem w WPF `targetID` WPF jest wyrównanie wartości z formularzami, które są ciągami znaków i gdzie takie ciągi są prawidłowe w [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`może być stosowany w składni elementu obiektu. W takim przypadku określenie wartości <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> właściwości jest wymagane do prawidłowego zainicjowania rozszerzenia.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] W implementacji czytnika obsługi dla tego rozszerzenia <xref:System.Windows.ComponentResourceKey> znaczników jest zdefiniowany przez klasę.  
  
 `ComponentResourceKey`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w użyciu { i } znaków w składni atrybutu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] który jest konwencją, za pomocą której procesor rozpoznaje, że rozszerzenie znaczników musi przetwarzać atrybut. Aby uzyskać więcej informacji, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
