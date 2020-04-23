---
title: x:Key — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: c05f98932ceceeb1530b34a09b1923f2af1378b5
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071501"
---
# <a name="xkey-directive"></a>x:Key — dyrektywa
Jednoznacznie identyfikuje elementy, które są tworzone i odwołuje się do słownika zdefiniowane xaml. Dodawanie `x:Key` wartości do elementu obiektu XAML jest najczęstszym sposobem identyfikowania zasobu w słowniku zasobów, na przykład w WPF <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Użycie atrybutu XAML (specyficzne dla WPF)  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`stringKeyValue`|Ciąg tekstowy do użycia jako klucz. Ciąg tekstowy musi być zgodny z [gramatyką XamlName](xamlname-grammar.md).|  
|`markupExtensionUsage`|W obrębie ograniczników {}rozszerzeń znaczników użycie rozszerzenia znaczników, które zapewnia obiekt do użycia jako klucz. Zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Key`obsługuje koncepcję słownika zasobów XAML. XAML jako język nie definiuje implementacji słownika zasobów, który jest pozostawiony do określonych struktur interfejsu użytkownika. Aby dowiedzieć się więcej o tym, jak słowniki zasobów XAML są implementowane w WPF, zobacz [Zasoby XAML](../fundamentals/xaml-resources-define.md).  
  
 W XAML 2006 i `x:Key` WPF, muszą być dostarczane jako atrybut. Nadal można używać kluczy innych niż sznurek, ale wymaga to użycia rozszerzenia znaczników w celu zapewnienia wartości nonstring w formularzu atrybutu. Jeśli używasz XAML 2009, `x:Key` można określić jako element, jawnie obsługiwać słowniki wpisane przez typy obiektów innych niż ciągi bez konieczności pośredniego rozszerzenia znaczników. Zobacz sekcję "XAML 2009" w tym temacie. Pozostała część sekcji Uwagi ma zastosowanie w szczególności do implementacji XAML 2006.  
  
 Wartość atrybutu `x:Key` może być dowolny ciąg zdefiniowany w [XamlName Gramatyka](xamlname-grammar.md) lub może być obiektem oceniane przez rozszerzenie znaczników. Zobacz "Uwagi dotyczące użycia WPF" na przykład z WPF.  
  
 Elementy podrzędne elementu nadrzędnego, który jest <xref:System.Collections.IDictionary> `x:Key` implementacją, zazwyczaj muszą zawierać atrybut, który określa unikatową wartość klucza w tym słowniku. Struktury mogą implementować właściwości klucza aliasów do zastąpienia `x:Key` na określonych typach; typy definiujące takie właściwości <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>powinny być przypisane do .  
  
 Kod równoważny z `x:Key` określeniem jest kluczem <xref:System.Collections.IDictionary>używanym dla bazowego . Na przykład, `x:Key` który jest stosowany w znacznikach dla zasobu w WPF jest odpowiednikiem wartości `key` parametru <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> po dodaniu zasobu do WPF <xref:System.Windows.ResourceDictionary> w kodzie.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Obiekty podrzędne obiektu nadrzędnego, który jest implementacją, <xref:System.Collections.IDictionary> takich jak WPF <xref:System.Windows.ResourceDictionary>, zazwyczaj musi zawierać `x:Key` atrybut, a wartość klucza musi być unikatowa w tym słowniku. Istnieją dwa istotne wyjątki:  
  
- Niektóre typy WPF deklarują klucz niejawny do użycia słownika. Na przykład <xref:System.Windows.Style> a <xref:System.Windows.Style.TargetType%2A>z , <xref:System.Windows.DataTemplate> lub <xref:System.Windows.DataTemplate.DataType%2A>z , <xref:System.Windows.ResourceDictionary> może być w a i używać klucza niejawnego.  
  
- WPF WPF obsługuje koncepcji słownika scalonych zasobów. Klucze mogą być współużytkowane między scalonymi słownikami, a zachowanie klucza udostępnionego jest dostępne za pomocą programu <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Aby uzyskać więcej informacji, zobacz [Scalone słowniki zasobów](../../framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 W ogólnej implementacji I modelu aplikacji WPF XAML unikatowość klucza nie jest sprawdzana przez kompilator znaczników XAML. Zamiast tego brakujące lub `x:Key` nonunique wartości powodują błędy analizatora XAML w czasie ładowania. Jednak visual studio obsługi słowników dla WPF często można zauważyć takie błędy w fazie projektowania.  
  
 Należy zauważyć, że w składni pokazano <xref:System.Windows.ResourceDictionary> obiekt jest niejawny w jaki procesor WPF XAML tworzy kolekcję do wypełniania <xref:System.Windows.FrameworkElement.Resources%2A> kolekcji. A <xref:System.Windows.ResourceDictionary> zazwyczaj nie jest jawnie dostarczane jako element w znacznikach, chociaż może to być w niektórych przypadkach, jeśli chcesz dla jasności (będzie to element obiektu kolekcji między elementem <xref:System.Windows.FrameworkElement.Resources%2A> właściwości i elementów w tym wypełnić słownika). Aby uzyskać informacje o tym, dlaczego obiekt kolekcji jest prawie zawsze elementem niejawnym w [znacznikach, zobacz Składnia XAML w szczegółach](../../framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 W WPF XAML implementacji obsługi kluczy słownika <xref:System.Windows.ResourceKey> zasobów jest zdefiniowany przez klasę abstrakcyjną. Jednak procesor WPF XAML produkuje różne podstawowe typy rozszerzeń dla kluczy na podstawie ich użycia. Na przykład klucz dla <xref:System.Windows.DataTemplate> lub dowolnej klasy pochodnej jest obsługiwany oddzielnie <xref:System.Windows.DataTemplateKey> i tworzy odrębny obiekt.  
  
 Klucze i nazwy używają różnych`x:Key` dyrektyw `x:Name`i elementów języka (w porównaniu) w podstawowej definicji XAML. Klucze i nazwy są również używane w różnych sytuacjach przez Definicję WPF I zastosowanie tych pojęć. Aby uzyskać szczegółowe informacje, zobacz [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak wspomniano wcześniej, wartość klucza mogą być dostarczane za pośrednictwem rozszerzenia znaczników i może być inny niż wartość ciągu. Przykładowy scenariusz WPF jest, `x:Key` że wartość może być [ComponentResourceKey](../../framework/wpf/advanced/componentresourcekey-markup-extension.md). Niektóre formanty uwidaczniają klucz stylu tego typu dla zasobu stylu niestandardowego, który wpływa na część wyglądu i zachowania tego formantu bez całkowitego zastępowania stylu. Przykładem takiego klucza <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>jest .  
  
 Funkcja scalonego słownika WPF wprowadza dodatkowe zagadnienia dotyczące unikatowości klucza i zachowania wyszukiwania klucza. Aby uzyskać więcej informacji, zobacz [Scalone słowniki zasobów](../../framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 rozluźnia `x:Key` ograniczenie, które zawsze są dostarczane w formie atrybutu.  
  
 W WPF WPF można użyć funkcji XAML 2009, ale tylko dla XAML, który nie jest skompilowany znaczników. Markup-skompilowany XAML dla WPF i BAML formie XAML obecnie nie obsługują XAML 2009 słów kluczowych i funkcji.  
  
 W obszarze XAML 2009 `x:Key` można określić elementy za pomocą następującego użycia:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Użycie elementu XAML (tylko XAML 2009)  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`keyObject`|Element obiektu dla obiektu, który jest używany `object` jako klucz dla danego w słowniku specjalistycznym.|  
  
- Kontener/element nadrzędny dla tego rodzaju użytkowania nie jest wyświetlany w tym miejscu. `object`oczekuje się, że będzie elementem podrzędnym elementu obiektu, który reprezentuje implementację słownika specjalistycznego. `keyObject`oczekuje się, że będzie wystąpienie obiektu (lub wartość typu wartości), który jest odpowiedni jako klucz dla tej implementacji słownika określonego wyspecjalizowanego.  
  
- WPF WPF nie implementuje słowników, które wymagają tego użycia. Klucze obiektów jest bardziej ogólną cechą języka XAML, prawdopodobnie przydatne dla niektórych scenariuszy słownika niestandardowego, gdzie tworzenie słownika w języku XAML jest pożądane. Dla WPF funkcje, takie jak niejawne style, które używają kluczy bez ciągu dla zasobów, istnieją inne techniki ustanawiania lub określania kluczy, więc przy użyciu klucza obiektu nie jest konieczne.  
  
- `keyObject`może być również użycie rozszerzenia znaczników w postaci elementu obiektu, a nie bezpośrednie wystąpienie obiektu.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użycia programu Silverlight  
 `x:Key`dla programu Silverlight jest dokumentowany oddzielnie. Aby uzyskać więcej informacji, zobacz [obszar nazw XAML (x:) Funkcje językowe (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Zobacz też

- [Zasoby XAML](../fundamentals/xaml-resources-define.md)
- [Zasoby i kod](../../framework/wpf/advanced/resources-and-code.md)
- [StaticResource — Rozszerzenie znaczników](../../framework/wpf/advanced/staticresource-markup-extension.md)
