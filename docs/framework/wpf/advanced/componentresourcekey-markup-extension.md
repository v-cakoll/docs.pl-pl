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
ms.openlocfilehash: a593839447742ed91d22a397d29b2455ce7a3b2d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627410"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey — Rozszerzenie znaczników
Definiuje i odwołuje się do kluczy dla zasobów, które zostały załadowane z zewnętrznych zestawów. Dzięki temu wyszukiwania zasobów określić typ docelowy w zestawie, a nie słownika zasobów jawne, w zestawie lub klasy.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Użycie atrybutu XAML (ustawienie kluczem compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Użycie atrybutu XAML (ustawienie wartości klucza, pełne)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Użycie atrybutu XAML (żądania zasobu, compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Użycie atrybutu XAML (żądania zasobów, pełny)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`targetTypeName`|Nazwa publicznego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] typ, który jest zdefiniowany w zestawie zasobów.|  
|`targetID`|Klucz dla zasobu. Gdy zasoby są wyszukiwane, `targetID` będzie odpowiednikiem [x: Key — dyrektywa](../../xaml-services/x-key-directive.md) zasobu.|  
  
## <a name="remarks"></a>Uwagi  
 Jak widać w powyższym użyciach {`ComponentResourceKey`} użycie rozszerzenia znaczników znajduje się w dwóch miejscach:  
  
- Definicja klucza w ciągu słownika zasobów motywu, zgodnie z informacjami od autora kontroli.  
  
- Podczas dostępu do zasobów motyw z zestawu, są retemplating kontrolki ale chcesz użyć wartości właściwości, które pochodzą z zasobów udostępnianych przez motywy formantu.  
  
 Do odwoływania się do składnika zasobów, które pochodzą z motywów, ogólnie zaleca się używanie `{DynamicResource}` zamiast `{StaticResource}`. Jest to pokazane w użyciach. `{DynamicResource}` jest zalecane, ponieważ sam motyw mogą być zmieniane przez użytkownika. Jeśli chcesz, aby zasób składnika, który najlepiej pasuje do intencji Autor sterowania do obsługi motywu, należy włączyć użytkownikowi składnika zasobów się być dynamiczna również.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Identyfikuje typ, który znajduje się w zestaw docelowy, w którym zasób jest faktycznie zdefiniowany. A `ComponentResourceKey` zdefiniowane i używane niezależnie od dokładnie, wiedząc, gdzie <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> jest zdefiniowany, ale ostatecznie musi rozpoznać typu przy użyciu zestawów odwołania.  
  
 Wspólne użycie dla <xref:System.Windows.ComponentResourceKey> polega na zdefiniowaniu klucze, które następnie są dostępne jako elementy członkowskie klasy. Dla tego użycia, możesz użyć <xref:System.Windows.ComponentResourceKey> konstruktora klasy, nie rozszerzenie znaczników. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.ComponentResourceKey>, lub Definiowanie i odwoływanie się do kluczy dla motywu sekcję "Zasoby tego tematu" [omówienie tworzenia kontrolek](../controls/control-authoring-overview.md).  
  
 Dla zasobów Zróżnicuj ustanawiania kluczy i odwoływanie się do składni atrybutów jest najczęściej używana w `ComponentResourceKey` — rozszerzenie znaczników.  
  
 Zwarta składnia pokazano opiera się na <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> sygnatury konstruktora i parametr pozycyjne użycie rozszerzenia znaczników. Kolejność, w której `targetTypeName` i `targetID` otrzymują jest ważne. Pełna składnia opiera się na <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Konstruktor domyślny, a następnie ustawia <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> w sposób analogiczny do składni atrybutu wartość true w elemencie obiektu. Pełne składnię kolejność, w którym są ustawione właściwości nie jest ważna. Relacja i mechanizmy te dwa warianty (compact i pełne) jest opisany bardziej szczegółowo w temacie [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Technicznie rzecz biorąc, wartość `targetID` może być dowolnego obiektu, ale nie musi być ciągiem. Najbardziej typowe obciążenie na platformie WPF jest jednak aby wyrównać `targetID` wartość za pomocą formularzy, które są ciągami i gdzie takie parametry są prawidłowe w [xamlname — gramatyka](../../xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey` może służyć w składni obiektów. W tym przypadku, określając wartość obu <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> właściwości jest wymagana, aby poprawnie zainicjować rozszerzenia.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji czytnika obsługi dla tego rozszerzenia znacznika jest definiowana przez <xref:System.Windows.ComponentResourceKey> klasy.  
  
 `ComponentResourceKey` jest rozszerzeniem znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
