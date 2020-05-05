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
ms.openlocfilehash: f86b7000b97bbc1287347947a9244c24a7de74c2
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141137"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey — Rozszerzenie znaczników
Definiuje i odwołuje się do kluczy dla zasobów, które są ładowane z zestawów zewnętrznych. Dzięki temu Wyszukiwanie zasobów pozwala określić typ docelowy w zestawie, a nie jawny słownik zasobów w zestawie lub w klasie.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Użycie atrybutu języka XAML (ustawienie klucza, Compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" ... />  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Użycie atrybutu języka XAML (klucz ustawienia, pełne)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" ... />  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Użycie atrybutu języka XAML (żądanie zasobu, Compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" ... />  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Użycie atrybutu języka XAML (żądanie zasobu, pełne)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" ... />  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`targetTypeName`|Nazwa typu publicznego środowiska uruchomieniowego języka wspólnego (CLR), który jest zdefiniowany w zestawie zasobów.|  
|`targetID`|Klucz zasobu. Gdy zasoby są wyszukiwane `targetID` , będą analogiczne do [dyrektywy x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) zasobu.|  
  
## <a name="remarks"></a>Uwagi  
 Jak pokazano powyżej, użycie rozszerzenia znacznika {`ComponentResourceKey`} zostało znalezione w dwóch miejscach:  
  
- Definicja klucza w słowniku zasobów motywu zgodnie z opisem autora kontrolki.  
  
- Uzyskiwanie dostępu do zasobu motywu z zestawu, gdy retemplating formant, ale chcą używać wartości właściwości, które pochodzą z zasobów udostępnianych przez motywy formantu.  
  
 W przypadku odwołujących się do zasobów składników, które pochodzą z motywów, `{DynamicResource}` zazwyczaj zaleca `{StaticResource}`się użycie zamiast. Ta wartość jest wyświetlana w obszarze użycia. `{DynamicResource}`jest zalecany, ponieważ sam motyw może zostać zmieniony przez użytkownika. Jeśli chcesz, aby zasób składnika był najlepiej zgodny z intencją autora kontrolki do obsługi motywu, należy włączyć także odwołanie do zasobu składnika jako dynamiczne.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Identyfikuje typ, który istnieje w zestawie docelowym, gdzie zasób jest w rzeczywistości zdefiniowany. `ComponentResourceKey` Może być zdefiniowana i używana niezależnie do znajomości dokładnego miejsca, <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> w którym jest zdefiniowana, ale ostatecznie musi rozpoznać typ za pomocą przywoływanych zestawów.  
  
 Typowym zastosowaniem <xref:System.Windows.ComponentResourceKey> programu jest zdefiniowanie kluczy, które są następnie udostępniane jako elementy członkowskie klasy. Do tego użycia należy użyć konstruktora <xref:System.Windows.ComponentResourceKey> klasy, a nie rozszerzenia znaczników. Więcej informacji można znaleźć <xref:System.Windows.ComponentResourceKey>w sekcji "Definiowanie i odwoływanie się do kluczy dla zasobów motywów" w temacie [Omówienie tworzenia kontrolek](../controls/control-authoring-overview.md)tematu.  
  
 W przypadku ustanawiania kluczy i odwoływania się do przywołujących się do nich `ComponentResourceKey` , składnia atrybutu jest często używana dla rozszerzenia znaczników.  
  
 Pokazana składnia Compact opiera się <xref:System.Windows.ComponentResourceKey.%23ctor%2A> na sygnaturze konstruktora i użyciu parametru pozycyjnego dla rozszerzenia znaczników. Kolejność, w której są `targetTypeName` określone `targetID` i są ważne. Składnia verbose opiera się na konstruktorze bez <xref:System.Windows.ComponentResourceKey.%23ctor%2A> parametrów, a następnie ustawia <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> w sposób analogiczny do prawdziwej składni atrybutu dla elementu obiektu. W pełnej składni kolejność, w jakiej są ustawiane właściwości, nie jest ważna. Relacje i mechanizmy tych dwóch alternatyw (Compact i verbose) są opisane bardziej szczegółowo w tematach [rozszerzeń znaczników tematu i języka XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 Technicznie, wartością dla `targetID` może być dowolny obiekt, nie musi być ciągiem. Jednak najbardziej typowym sposobem użycia w WPF jest wyrównanie `targetID` wartości za pomocą ciągów, które są ciągami i gdzie te ciągi są prawidłowe w [gramatycename XAML](../../../desktop-wpf/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`może być używany w składni elementu obiektu. W takim przypadku określenie wartości właściwości <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> jest wymagane do prawidłowego zainicjowania rozszerzenia.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] W implementacji czytnika obsługa tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.ComponentResourceKey> klasę.  
  
 `ComponentResourceKey`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której procesor rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Przegląd Autorstwo formantów](../controls/control-authoring-overview.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
