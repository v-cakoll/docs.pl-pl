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
ms.openlocfilehash: 85e6862d59284df1b51bf5ea7fbba786fe0492d7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458971"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey — Rozszerzenie znaczników
Definiuje i odwołuje się do kluczy dla zasobów, które są ładowane z zestawów zewnętrznych. Dzięki temu Wyszukiwanie zasobów pozwala określić typ docelowy w zestawie, a nie jawny słownik zasobów w zestawie lub w klasie.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Użycie atrybutu języka XAML (ustawienie klucza, Compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Użycie atrybutu języka XAML (klucz ustawienia, pełne)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Użycie atrybutu języka XAML (żądanie zasobu, Compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Użycie atrybutu języka XAML (żądanie zasobu, pełne)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`targetTypeName`|Nazwa typu publicznego środowiska uruchomieniowego języka wspólnego (CLR), który jest zdefiniowany w zestawie zasobów.|  
|`targetID`|Klucz zasobu. Podczas wyszukiwania zasobów `targetID` będą analogiczne do [dyrektywy x:Key](../../xaml-services/x-key-directive.md) zasobu.|  
  
## <a name="remarks"></a>Uwagi  
 Jak pokazano powyżej, użycie rozszerzenia znacznika {`ComponentResourceKey`} zostało znalezione w dwóch miejscach:  
  
- Definicja klucza w słowniku zasobów motywu zgodnie z opisem autora kontrolki.  
  
- Uzyskiwanie dostępu do zasobu motywu z zestawu, gdy retemplating formant, ale chcą używać wartości właściwości, które pochodzą z zasobów udostępnianych przez motywy formantu.  
  
 W przypadku odwołujących się do zasobów składników, które pochodzą z motywów, zazwyczaj zaleca się używanie `{DynamicResource}`, a nie `{StaticResource}`. Ta wartość jest wyświetlana w obszarze użycia. `{DynamicResource}` jest zalecana, ponieważ sama kompozycja może zostać zmieniona przez użytkownika. Jeśli chcesz, aby zasób składnika był najlepiej zgodny z intencją autora kontrolki do obsługi motywu, należy włączyć także odwołanie do zasobu składnika jako dynamiczne.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identyfikuje typ, który istnieje w zestawie docelowym, gdzie zasób jest w rzeczywistości zdefiniowany. `ComponentResourceKey` może być zdefiniowana i używana niezależnie do znajomości dokładnego miejsca, w którym zdefiniowano <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>, ale ostatecznie musi rozpoznać typ za pomocą przywoływanych zestawów.  
  
 Typowym zastosowaniem <xref:System.Windows.ComponentResourceKey> jest definiowanie kluczy, które są następnie udostępniane jako elementy członkowskie klasy. Do tego użycia należy użyć konstruktora klasy <xref:System.Windows.ComponentResourceKey>, a nie rozszerzenia znacznika. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.ComponentResourceKey>lub sekcję "Definiowanie i odwoływanie się do kluczy dla zasobów motywów" w temacie [Omówienie tworzenia kontrolek](../controls/control-authoring-overview.md)tematu.  
  
 W przypadku ustanawiania kluczy i odwoływania się do przywołujących się do nich, składnia atrybutu jest często używana dla rozszerzenia znaczników `ComponentResourceKey`.  
  
 Pokazana składnia Compact opiera się na sygnaturze konstruktora <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> i użyciu parametru pozycyjnego dla rozszerzenia znaczników. Kolejność, w której są określone `targetTypeName` i `targetID`, jest ważna. Składnia verbose opiera się na konstruktorze bez parametrów <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>, a następnie ustawia <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> w taki sposób, który jest analogiczny do prawdziwej składni atrybutu w elemencie obiektu. W pełnej składni kolejność, w jakiej są ustawiane właściwości, nie jest ważna. Relacje i mechanizmy tych dwóch alternatyw (Compact i verbose) są opisane bardziej szczegółowo w tematach [rozszerzeń znaczników tematu i języka XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 Technicznie wartość `targetID` może być dowolnym obiektem, nie musi być ciągiem. Jednak najbardziej typowym sposobem użycia w platformie WPF jest wyrównanie `targetID` wartości za pomocą ciągów, które są ciągami i gdzie takie ciągi są prawidłowe w [gramatyki XamlName](../../xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey` można używać w składni elementu obiektu. W takim przypadku określenie wartości właściwości <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> jest wymagane do prawidłowego zainicjowania rozszerzenia.  
  
 W implementacji czytnika [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], obsługa dla tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.ComponentResourceKey>.  
  
 `ComponentResourceKey` to rozszerzenie znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą której procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
