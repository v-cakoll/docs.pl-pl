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
ms.openlocfilehash: b00218623add052e135bc5815d615fe7cdf002ee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459958"
---
# <a name="xkey-directive"></a>x:Key — dyrektywa
Jednoznacznie identyfikuje elementy, które są tworzone i przywoływane w słowniku zdefiniowanym przez język XAML. Dodawanie `x:Key` wartość do elementu obiektu XAML jest najpopularniejszym sposobem identyfikowania zasobu w słowniku zasobów, na przykład w <xref:System.Windows.ResourceDictionary>WPF.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Użycie atrybutu języka XAML (specyficzne dla platformy WPF)  
  
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
|`stringKeyValue`|Ciąg tekstowy, który ma być używany jako klucz. Ciąg tekstowy musi być zgodny z [gramatyką XamlName](xamlname-grammar.md).|  
|`markupExtensionUsage`|W ramach ograniczników rozszerzenia znaczników {}, użycie rozszerzenia znaczników, które zapewnia obiekt do użycia jako klucz. Zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Key` obsługuje koncepcję słownika zasobów XAML. XAML jako język nie definiuje implementacji słownika zasobów, która jest pozostała do określonych platform interfejsu użytkownika. Aby dowiedzieć się więcej o sposobie implementacji słowników zasobów XAML w WPF, zobacz [zasoby XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
 W języku XAML 2006 i WPF `x:Key` muszą być podane jako atrybut. Nadal można używać kluczy niebędących ciągami, ale wymaga to użycia rozszerzenia znacznika, aby zapewnić wartość niebędącą ciągiem w formie atrybutu. Jeśli używasz języka XAML 2009, `x:Key` może być określony jako element, aby jawnie obsługiwać słowniki z typami obiektów innymi niż ciągi, bez konieczności pośredniego rozszerzenia znaczników. Zobacz sekcję "XAML 2009" w tym temacie. Pozostała część sekcji uwagi dotyczy implementacji języka XAML 2006.  
  
 Wartość atrybutu `x:Key` może być dowolnego ciągu zdefiniowanego w [gramatycename XAML](xamlname-grammar.md) lub może być obiektem ocenianym za pomocą rozszerzenia znacznika. Zobacz sekcję "uwagi dotyczące użycia WPF", aby zapoznać się z przykładem z platformy WPF.  
  
 Elementy podrzędne elementu nadrzędnego, który jest implementacją <xref:System.Collections.IDictionary>, muszą zazwyczaj zawierać atrybut `x:Key`, który określa unikatową wartość klucza w tym słowniku. Struktury mogą implementować aliasy właściwości klucza, aby zastąpić `x:Key` na określonych typach; typy, które definiują takie właściwości, powinny być przypisane do <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Odpowiednikiem kodu określającego `x:Key` jest klucz, który jest używany dla bazowego <xref:System.Collections.IDictionary>. Na przykład `x:Key`, który jest stosowany w adjustacji dla zasobu w WPF, jest odpowiednikiem wartości parametru `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>, gdy dodasz zasób do środowiska WPF <xref:System.Windows.ResourceDictionary> w kodzie.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Obiekty podrzędne obiektu nadrzędnego, który jest implementacją <xref:System.Collections.IDictionary>, taką jak WPF <xref:System.Windows.ResourceDictionary>, muszą zazwyczaj zawierać atrybut `x:Key`, a wartość klucza musi być unikatowa w ramach tego słownika. Istnieją dwa istotne wyjątki:  
  
- Niektóre typy WPF deklarują klucz niejawny dla użycia słownika. Na przykład <xref:System.Windows.Style> z <xref:System.Windows.Style.TargetType%2A>lub <xref:System.Windows.DataTemplate> z <xref:System.Windows.DataTemplate.DataType%2A>, może znajdować się w <xref:System.Windows.ResourceDictionary> i używać klucza niejawnego.  
  
- WPF obsługuje koncepcję scalonego słownika zasobów. Klucze mogą być współużytkowane przez scalone słowniki, a zachowanie klucza współużytkowanego można uzyskać za pomocą <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../wpf/advanced/merged-resource-dictionaries.md).  
  
 W ogólnej implementacji języka XAML WPF i modelu aplikacji Unikatowość klucza nie jest sprawdzana przez kompilator znaczników XAML. Zamiast tego brakujące lub nieunikatowe wartości `x:Key` powodują błędy analizatora XAML czasu ładowania. Jednak obsługa słowników dla WPF w programie Visual Studio może często zanotować takie błędy w fazie projektowania.  
  
 Należy zauważyć, że w pokazanej składni obiekt <xref:System.Windows.ResourceDictionary> jest niejawny w sposób, w jaki procesor WPF XAML tworzy kolekcję, aby wypełnić kolekcję <xref:System.Windows.FrameworkElement.Resources%2A>. <xref:System.Windows.ResourceDictionary> nie jest zazwyczaj jawnie określona jako element w znaczniku, chociaż może być w niektórych przypadkach, jeśli chcesz dla jasności (być elementem obiektu kolekcji między elementem właściwości <xref:System.Windows.FrameworkElement.Resources%2A> i elementami w ramach tego wypełnienia słownika). Aby uzyskać informacje o tym, dlaczego obiekt kolekcji prawie zawsze jest niejawny element w znaczniku, zobacz [Szczegóły składni XAML](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 W implementacji języka XAML WPF obsługa kluczy słownika zasobów jest definiowana przez klasę abstrakcyjną <xref:System.Windows.ResourceKey>. Jednak procesor WPF XAML produkuje różne podstawowe typy rozszerzeń dla kluczy na podstawie ich użycia. Na przykład klucz dla <xref:System.Windows.DataTemplate> lub dowolnej klasy pochodnej jest obsługiwany oddzielnie i tworzy odrębny obiekt <xref:System.Windows.DataTemplateKey>.  
  
 Klucze i nazwy używają różnych dyrektyw i elementów języka (`x:Key` a `x:Name`) w podstawowej definicji XAML. Klucze i nazwy są również używane w różnych sytuacjach przy użyciu definicji WPF i aplikacji. Aby uzyskać szczegółowe informacje, zobacz [WPF XAML Zakresy nazw WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak wspomniano wcześniej, wartość klucza może być dostarczana za pomocą rozszerzenia znacznika i może być inna niż wartość ciągu. Przykładowy scenariusz WPF polega na tym, że wartość `x:Key` może być [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Niektóre formanty uwidaczniają klucz stylu tego typu dla zasobu stylu niestandardowego, który wpływa na część wyglądu i zachowania tej kontrolki bez całkowitego zastępowania stylu. Przykładem takiego klucza jest <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkcja scalonego słownika WPF zawiera dodatkowe zagadnienia dotyczące unikatowego klucza i zachowania wyszukiwania kluczy. Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 KOD XAML 2009 ogranicza ograniczenie, które `x:Key` zawsze dostępne w formie atrybutu.  
  
 W programie WPF można używać funkcji języka XAML 2009, ale tylko dla języka XAML, który nie jest kompilowany do znaczników. Skompilowane znaczniki XAML dla WPF i forma BAML języka XAML nie obsługują obecnie słów kluczowych i funkcji języka XAML 2009.  
  
 W obszarze XAML 2009 można określić `x:Key` elementów za pomocą następującego użycia:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Użycie elementu XAML (tylko XAML 2009)  
  
```  
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
|`keyObject`|Element obiektu dla obiektu, który jest używany jako klucz dla danego `object` w specjalnym słowniku.|  
  
- Nie pokazano tutaj kontenera/elementu nadrzędnego dla tego rodzaju użycia. `object` powinien być elementem podrzędnym elementu obiektu, który reprezentuje implementację specjalnego słownika. `keyObject` oczekuje się wystąpienia obiektu (lub wartości typu wartości), która jest odpowiednia jako klucz dla danej implementacji wyspecjalizowanego słownika.  
  
- WPF nie implementuje słowników, które wymagają tego użycia. Klucze obiektów to bardziej ogólna funkcja języka XAML, prawdopodobnie przydatna w przypadku niektórych scenariuszy słownika niestandardowego, w których tworzenie słownika w języku XAML jest pożądane. W przypadku funkcji WPF, takich jak niejawne style, które używają kluczy niebędących ciągami dla zasobów, inne techniki służące do ustanawiania lub określania kluczy istnieją, dlatego nie trzeba używać klucza obiektu.  
  
- *obiektem* typu może być również użycie rozszerzenia znacznika w formularzu elementu obiektu, a nie w bezpośrednim wystąpieniu obiektu.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użycia programu Silverlight  
 `x:Key` dla programu Silverlight jest udokumentowany osobno. Aby uzyskać więcej informacji, zobacz [przestrzeń nazw XAML (x:) Funkcje języka (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zasoby i kod](../wpf/advanced/resources-and-code.md)
- [StaticResource, rozszerzenie znaczników](../wpf/advanced/staticresource-markup-extension.md)
