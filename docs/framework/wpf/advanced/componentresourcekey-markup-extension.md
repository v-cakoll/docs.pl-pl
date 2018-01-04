---
title: "ComponentResourceKey — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4bfaee35ba9f8cf60deb01c52a142433d08021c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey — Rozszerzenie znaczników
Definiuje i odwołuje się do kluczy dla zasobów, które są ładowane z zewnętrznych zestawów. Dzięki temu wyszukiwania zasobów określić typ docelowy w zestawie, a nie słownika jawne zasobów w zestawie lub klasy.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Użycie atrybutu XAML (klucz Ustawienia, compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Użycie atrybutu XAML (ustawienie klucza, verbose)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Użycie atrybutu XAML (żądania zasobów, compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Użycie atrybutu XAML (żądania zasobów, verbose)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`targetTypeName`|Nazwa publicznego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] typu, który jest zdefiniowany w zestawie zasobów.|  
|`targetID`|Klucz zasobu. Gdy zasoby są wyszukiwane, `targetID` jest odpowiednikiem [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) zasobu.|  
  
## <a name="remarks"></a>Uwagi  
 Jak pokazano powyżej, użycia {`ComponentResourceKey`} użycie rozszerzenia znaczników znajduje się w dwóch miejscach:  
  
-   Definicja klucz w słowniku zasobów motywu, określone przez autora formantu.  
  
-   Dostęp do zasobów motyw z zestawu, jeżeli są retemplating formantu, ale chcesz użyć wartości właściwości, które pochodzą z zasobów udostępnianych przez motywy formantu.  
  
 Dla odwołania do składnika zasoby, które pochodzą z kompozycje, ogólnie zalecane jest używanie `{DynamicResource}` zamiast `{StaticResource}`. Przedstawiono to w użyciach. `{DynamicResource}`jest zalecane, ponieważ można zmienić motyw się przez użytkownika. Chcąc zasobów składnika, najlepiej pasujący zamiar autora sterowania do obsługi motywu, należy włączyć składnik zasobów odwołania do dynamicznej można również.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Określa typ, który istnieje w zestawie docelowym, których zasób faktycznie jest zdefiniowana. A `ComponentResourceKey` mogą być definiowane i używane niezależnie od wiedząc dokładnie gdzie <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> jest określony, ale ostatecznie musi rozpoznać typu za pomocą zestawów występujących w odwołaniach.  
  
 Użycie wspólnych <xref:System.Windows.ComponentResourceKey> jest określenie kluczy, które następnie są dostępne jako elementy członkowskie klasy. W przypadku użycia, możesz używać <xref:System.Windows.ComponentResourceKey> konstruktora klasy, nie rozszerzenia znaczników. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.ComponentResourceKey>, lub w części "Definiowanie i odwołuje się do kluczy dla motywu zasoby" tematu [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Dla zarówno ustanawiania kluczy i odwołuje się do zasobów z kluczem, składnia atrybutu jest najczęściej używana w `ComponentResourceKey` — rozszerzenie znaczników.  
  
 Zależy od zwięzłą składnią pokazano <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> sygnatury konstruktora i korzystaniu z parametrów pozycyjnych rozszerzenia znacznika. Kolejność `targetTypeName` i `targetID` podano jest ważna. Pełna składnia polega na <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Konstruktor domyślny, a następnie ustawia <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> w taki sposób, który jest odpowiednikiem Składnia atrybutu wartość true w elemencie obiektu. W Pełna składnia kolejność, w którym są ustawione właściwości nie jest ważna. Relacja i mechanizmów tych dwóch alternatyw (compact i pełne) jest opisany bardziej szczegółowo w temacie [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Z technicznego punktu widzenia wartość `targetID` może być dowolny obiekt, ale nie musi być ciągiem. Jednak najbardziej typowe obciążenie na platformie WPF jest, aby były wyrównane `targetID` wartości z formularzami ciągów, które są i gdzie tych ciągów są prawidłowe w [xamlname — gramatyka](../../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`można w składni elementu obiekt. W takim przypadku określającą wartość oba <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> i <xref:System.Windows.ComponentResourceKey.ResourceId%2A> właściwości jest wymagana, aby poprawnie zainicjować rozszerzenia.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji czytnika obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.ComponentResourceKey> klasy.  
  
 `ComponentResourceKey`to rozszerzenie znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w ich składni atrybutu Konwencji za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Tworzenie kontrolek — omówienie](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
