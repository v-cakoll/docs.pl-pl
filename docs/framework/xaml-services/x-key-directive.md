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
ms.openlocfilehash: 4ffd7a2922c7f3ba35ccb9ac7ce29a6a00cd99af
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837210"
---
# <a name="xkey-directive"></a>x:Key — dyrektywa
Jednoznacznie identyfikuje elementy, które są tworzone i wspominane w słowniku zdefiniowanym w języku XAML. Dodawanie wartości `x:Key` do elementu obiektu języka XAML jest najczęstszym sposobem identyfikacji zasobu w słowniku zasobów, na przykład w programie WPF <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Użycie atrybutu języka XAML (charakterystyczne dla WPF)  
  
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
|`stringKeyValue`|Ciąg tekstowy używany jako klucz. Ciąg tekstowy musi być zgodny z [gramatyką XamlName](xamlname-grammar.md).|  
|`markupExtensionUsage`|W ramach ograniczników rozszerzenia znaczników {}, użycie rozszerzenia znaczników, które zapewnia obiekt do użycia jako klucz. Zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Key` obsługuje pojęcia słownika zasobów języka XAML. XAML jako język nie definiuje implementacji słownika zasobów, zajmują się tym szczególne szablony interfejsu użytkownika. Aby dowiedzieć się więcej o sposobie implementacji słowników zasobów XAML w WPF, zobacz [zasoby XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 W języku XAML 2006 i WPF `x:Key` muszą być podane jako atrybut. Nadal możesz używać kluczy typu nonstring, ale wymaga to użycia rozszerzenia znaczników w celu zapewnienia wartości typu nonstring w formie atrybutu. Jeśli używasz języka XAML 2009, `x:Key` może być określony jako element, aby jawnie obsługiwać słowniki z typami obiektów innymi niż ciągi, bez konieczności pośredniego rozszerzenia znaczników. Zobacz sekcję "XAML 2009" w tym temacie. Pozostała część sekcji uwagi dotyczy implementacji języka XAML 2006.  
  
 Wartość atrybutu `x:Key` może być dowolnego ciągu zdefiniowanego w [gramatycename XAML](xamlname-grammar.md) lub może być obiektem ocenianym za pomocą rozszerzenia znacznika. Zobacz "Uwagi dotyczące użycia WPF" aby zapoznać się z przykładem z WPF.  
  
 Elementy podrzędne elementu nadrzędnego, który jest implementacją <xref:System.Collections.IDictionary>, muszą zazwyczaj zawierać atrybut `x:Key`, który określa unikalną wartość kluczową w ramach tego słownika. Środowiska mogą implementować aliasy właściwości klucza do podstawienia w obiekcie `x:Key` w określonych typach; typy, które definiują takie właściwości, powinny mieć atrybut <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Odpowiednikiem kodu dla określania `x:Key` jest klucz, który jest używany dla poniższych <xref:System.Collections.IDictionary>. Na przykład obiekt `x:Key` zastosowany w znaczniku dla zasobu w technologii WPF jest równoważny wartości parametru `key` obiektu <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> podczas dodawania zasobu do obiektu <xref:System.Windows.ResourceDictionary> technologii WPF w kodzie.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Obiekty podrzędne obiektu nadrzędnego, który jest implementacją <xref:System.Collections.IDictionary>, takie jak <xref:System.Windows.ResourceDictionary> WPF, muszą zazwyczaj zawierać atrybut `x:Key`, a wartość kluczowa musi być unikatowa w ramach tego słownika. Istnieją dwa znaczące wyjątki:  
  
- Niektóre typy WPF deklarują niejawny klucz do użycia słownika. Na przykład obiekt <xref:System.Windows.Style> z atrybutem <xref:System.Windows.Style.TargetType%2A> lub obiekt <xref:System.Windows.DataTemplate> z atrybutem <xref:System.Windows.DataTemplate.DataType%2A> może być w obiekcie <xref:System.Windows.ResourceDictionary> i używać klucza niejawnego.  
  
- WPF obsługuje pojęcie słownika scalonych zasobów. Klucze mogą być współużytkowane między scalonymi słownikami, a do zachowania klucza udostępnionego można uzyskać dostęp za pomocą funkcji <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../wpf/advanced/merged-resource-dictionaries.md).  
  
 W ogólnym modelu implementacji i aplikacji dla języka XAML w środowisku WPF unikatowość klucza nie jest sprawdzana przez kompilator znaczników języka XAML. Zamiast tego brakujące lub nieunikatowe wartości `x:Key` powodują błędy analizatora składni języka XAML podczas ładowania. Jednak obsługa słowników dla WPF w programie Visual Studio może często zanotować takie błędy w fazie projektowania.  
  
 Należy zauważyć, że w składni przedstawionej obiekt <xref:System.Windows.ResourceDictionary> obiektu jest niejawny w tym, w jak procesor języka XAML w środowisku WPF generuje kolekcję, aby wypełnić kolekcję <xref:System.Windows.FrameworkElement.Resources%2A>. <xref:System.Windows.ResourceDictionary> nie jest zazwyczaj wyraźnie oznaczony jako element adiustacji, chociaż może być — w niektórych przypadkach dla jasności (będzie to element kolekcji obiektów między elementem właściwości <xref:System.Windows.FrameworkElement.Resources%2A> i elementami do wypełnienia w tym słowniku). Aby uzyskać informacje o tym, dlaczego obiekt kolekcji prawie zawsze jest niejawny element w znaczniku, zobacz [Szczegóły składni XAML](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 W implementacji języka XAML w środowisku WPF obsługa dla kluczy słownika zasobu jest określona w klasie abstrakcyjnej <xref:System.Windows.ResourceKey>. Jednak procesor języka XAML w środowisku WPF produkuje różne podstawowe typy rozszerzeń dla kluczy w oparciu o ich zastosowania. Na przykład klucz dla klasy <xref:System.Windows.DataTemplate> lub dowolnej klasy pochodnej jest obsługiwany osobno i tworzy oddzielny obiekt <xref:System.Windows.DataTemplateKey>.  
  
 Klucze i nazwy używają różnych dyrektyw i elementów języka (`x:Key` a `x:Name`) w podstawowej definicji języka XAML. Klucze i nazwy są również używane w różnych sytuacjach przez definicje środowiska WPF i zastosowania tych koncepcji. Aby uzyskać szczegółowe informacje, zobacz [WPF XAML Zakresy nazw WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak wspomniano wcześniej, wartość klucza może być dostarczana za pośrednictwem rozszerzenia adiustacji i może być czymś innym niż wartość ciągu. Przykładowy scenariusz WPF polega na tym, że wartość `x:Key` może być [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Niektóre formanty zmieniają klucz stylu tego typu zasobu na styl niestandardowy, który wpływa częściowo na wygląd i zachowanie tego formantu, bez zastępowania całego stylu. Przykładem takiego klucza jest <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkcja scalonych słowników WPF wprowadza dodatkowe zagadnienia dotyczące kluczowej unikatowości i kluczowego zachowania wyszukiwania. Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 KOD XAML 2009 ogranicza ograniczenie, które `x:Key` zawsze dostępne w formie atrybutu.  
  
 W programie WPF można używać funkcji języka XAML 2009, ale tylko dla języka XAML, który nie jest kompilowany do znaczników. Skompilowane znaczniki XAML dla WPF i forma BAML języka XAML nie obsługują obecnie słów kluczowych i funkcji języka XAML 2009.  
  
 W obszarze XAML 2009 można określić `x:Key` elementów za pomocą następującego użycia:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Użycie elementu języka XAML (tylko XAML 2009)  
  
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
|`keyObject`|Element obiektu dla obiektu, który jest używany jako klucz dla danego elementu `object` w słowniku specjalistycznym.|  
  
- Kontener/element nadrzędny dla tego rodzaju wykorzystania nie jest tu ukazywany. Oczekuje się, że element `object` będzie elementem podrzędnym elementu obiekt, który reprezentuje implementację słownika specjalistycznego. Oczekuje się, że obiekt `keyObject` będzie wystąpieniem obiektu (lub wartością typu wartości), które jest właściwe jako klucz dla tej określonej implementacji słownika specjalistycznego.  
  
- WPF nie implementuje słowników, które wymagają tego użycia. Klucze obiektów to bardziej ogólna funkcja języka XAML, ewentualnie przydatna w niektórych scenariuszach słowników niestandardowych, gdzie jest pożądane tworzenie słownika w języku XAML. W przypadku funkcji środowiska WPF takich jak niejawna style, które używają kluczy niebędących ciągami dla zasobów, inne techniki dla ustanowienia lub określania kluczy istnieją, więc używanie klucza obiektu nie jest konieczne.  
  
- *obiektem* typu może być również użycie rozszerzenia znacznika w formularzu elementu obiektu, a nie w bezpośrednim wystąpieniu obiektu.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użytkowania Silverlight  
 `x:Key` dla Silverlight jest opisane osobno. Aby uzyskać więcej informacji, zobacz [przestrzeń nazw XAML (x:) Funkcje języka (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zasoby i kod](../wpf/advanced/resources-and-code.md)
- [StaticResource, rozszerzenie znaczników](../wpf/advanced/staticresource-markup-extension.md)
