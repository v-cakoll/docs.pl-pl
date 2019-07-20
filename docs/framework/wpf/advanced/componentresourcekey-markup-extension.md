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
ms.openlocfilehash: 93735d12426042fd6517c10a55d1a9bd32f906bb
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363056"
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
|`targetTypeName`|Nazwa typu publicznego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , który jest zdefiniowany w zestawie zasobów.|  
|`targetID`|Klucz zasobu. Gdy zasoby są wyszukiwane `targetID` , będą analogiczne do [dyrektywy x:Key](../../xaml-services/x-key-directive.md) zasobu.|  
  
## <a name="remarks"></a>Uwagi  
 Jak pokazano powyżej, użycie rozszerzenia znacznika {`ComponentResourceKey`} zostało znalezione w dwóch miejscach:  
  
- Definicja klucza w słowniku zasobów motywu zgodnie z opisem autora kontrolki.  
  
- Uzyskiwanie dostępu do zasobu motywu z zestawu, gdy retemplating formant, ale chcą używać wartości właściwości, które pochodzą z zasobów udostępnianych przez motywy formantu.  
  
 W przypadku odwołujących się do zasobów składników, które pochodzą z motywów, `{DynamicResource}` zazwyczaj zaleca `{StaticResource}`się użycie zamiast. Ta wartość jest wyświetlana w obszarze użycia. `{DynamicResource}`jest zalecany, ponieważ sam motyw może zostać zmieniony przez użytkownika. Jeśli chcesz, aby zasób składnika był najlepiej zgodny z intencją autora kontrolki do obsługi motywu, należy włączyć także odwołanie do zasobu składnika jako dynamiczne.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Identyfikuje typ, który istnieje w zestawie docelowym, gdzie zasób jest w rzeczywistości zdefiniowany. Może być zdefiniowana i używana niezależnie do znajomości dokładnego miejsca, <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> w którym jest zdefiniowana, ale ostatecznie musi rozpoznać typ za pomocą przywoływanych zestawów. `ComponentResourceKey`  
  
 Typowym zastosowaniem <xref:System.Windows.ComponentResourceKey> programu jest zdefiniowanie kluczy, które są następnie udostępniane jako elementy członkowskie klasy. Do tego użycia należy użyć <xref:System.Windows.ComponentResourceKey> konstruktora klasy, a nie rozszerzenia znaczników. Więcej informacji można znaleźć <xref:System.Windows.ComponentResourceKey>w sekcji "Definiowanie i odwoływanie się do kluczy dla zasobów motywów" w temacie [Omówienie tworzenia kontrolek](../controls/control-authoring-overview.md)tematu.  
  
 W przypadku ustanawiania kluczy i odwoływania się do przywołujących się do nich `ComponentResourceKey` , składnia atrybutu jest często używana dla rozszerzenia znaczników.  
  
 Pokazana składnia Compact opiera się <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> na sygnaturze konstruktora i użyciu parametru pozycyjnego dla rozszerzenia znaczników. Kolejność, w której `targetTypeName` są określone i `targetID` są ważne. Składnia verbose opiera się na <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> konstruktorze bez parametrów, a następnie <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ustawia i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> w sposób analogiczny do prawdziwej składni atrybutu dla elementu obiektu. W pełnej składni kolejność, w jakiej są ustawiane właściwości, nie jest ważna. Relacje i mechanizmy tych dwóch alternatyw (Compact i verbose) są opisane bardziej szczegółowo w tematach [rozszerzeń znaczników tematu i języka XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 Technicznie, wartością dla `targetID` może być dowolny obiekt, nie musi być ciągiem. Jednak najbardziej typowym sposobem użycia w WPF jest wyrównanie `targetID` wartości za pomocą ciągów, które są ciągami i gdzie te ciągi są prawidłowe w gramatycename [XAML](../../xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`może być używany w składni elementu obiektu. W takim przypadku określenie wartości <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> właściwości i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> jest wymagane do prawidłowego zainicjowania rozszerzenia.  
  
 W implementacji czytnika obsługa tego <xref:System.Windows.ComponentResourceKey> rozszerzenia znacznika jest definiowana przez klasę. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
 `ComponentResourceKey`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której procesor rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
