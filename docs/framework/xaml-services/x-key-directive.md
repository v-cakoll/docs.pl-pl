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
ms.openlocfilehash: eb9f9cc1dfdb802e340123d0d39e9c9ebaa457f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053749"
---
# <a name="xkey-directive"></a>x:Key — dyrektywa
Jednoznacznie identyfikuje elementy, które są tworzone i przywoływane w słowniku zdefiniowanym przez język XAML. Dodanie wartości do elementu obiektu XAML jest najczęstszym sposobem identyfikowania zasobu w słowniku zasobów, na przykład w WPF <xref:System.Windows.ResourceDictionary>. `x:Key`  
  
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
|`markupExtensionUsage`|W ramach ograniczników {}rozszerzenia znaczników użycie rozszerzenia znacznika zapewnia obiekt do użycia jako klucz. Zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Key`obsługuje koncepcję słownika zasobów XAML. XAML jako język nie definiuje implementacji słownika zasobów, która jest pozostała do określonych platform interfejsu użytkownika. Aby dowiedzieć się więcej o sposobie implementacji słowników zasobów XAML w WPF, zobacz [zasoby XAML](../wpf/advanced/xaml-resources.md).  
  
 W języku XAML 2006 i WPF `x:Key` należy podać jako atrybut. Nadal można używać kluczy niebędących ciągami, ale wymaga to użycia rozszerzenia znacznika, aby zapewnić wartość niebędącą ciągiem w formie atrybutu. Jeśli używasz języka XAML 2009, `x:Key` można go określić jako element, aby jawnie obsługiwać słowniki z typami obiektów innymi niż ciągi bez konieczności pośredniego rozszerzenia znaczników. Zobacz sekcję "XAML 2009" w tym temacie. Pozostała część sekcji uwagi dotyczy implementacji języka XAML 2006.  
  
 Wartość `x:Key` atrybutu może być dowolnego ciągu zdefiniowanego w [gramatycename XAML](xamlname-grammar.md) lub może być obiektem ocenianym za pomocą rozszerzenia znacznika. Zobacz sekcję "uwagi dotyczące użycia WPF", aby zapoznać się z przykładem z platformy WPF.  
  
 Elementy podrzędne elementu nadrzędnego, który jest <xref:System.Collections.IDictionary> implementacją, muszą zazwyczaj `x:Key` zawierać atrybut, który określa unikatową wartość klucza w tym słowniku. Struktury mogą implementować aliasy właściwości klucza do podstawiania dla konkretnych typów; typy, które definiują takie właściwości, powinny <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>być przypisane do `x:Key` .  
  
 Odpowiednikiem kodu określającym `x:Key` jest klucz, który jest używany dla elementu bazowego. <xref:System.Collections.IDictionary> Na przykład, `x:Key` który jest stosowany podczas adiustacji dla zasobu w WPF, jest odpowiednikiem wartości `key` parametru <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> podczas dodawania zasobu do WPF <xref:System.Windows.ResourceDictionary> w kodzie.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Obiekty podrzędne obiektu nadrzędnego, który jest <xref:System.Collections.IDictionary> implementacją, taką jak WPF <xref:System.Windows.ResourceDictionary> `x:Key` , muszą zazwyczaj zawierać atrybut, a wartość klucza musi być unikatowa w obrębie tego słownika. Istnieją dwa istotne wyjątki:  
  
- Niektóre typy WPF deklarują klucz niejawny dla użycia słownika. Na <xref:System.Windows.Style> przykład, <xref:System.Windows.DataTemplate> z <xref:System.Windows.Style.TargetType%2A>, lub z <xref:System.Windows.ResourceDictionary> , może być w i używać klucza niejawnego. <xref:System.Windows.DataTemplate.DataType%2A>  
  
- WPF obsługuje koncepcję scalonego słownika zasobów. Klucze mogą być współużytkowane przez scalone słowniki, a zachowanie klucza współużytkowanego <xref:System.Windows.FrameworkContentElement.FindResource%2A>można uzyskać za pomocą polecenia. Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../wpf/advanced/merged-resource-dictionaries.md).  
  
 W ogólnej implementacji języka XAML WPF i modelu aplikacji Unikatowość klucza nie jest sprawdzana przez kompilator znaczników XAML. Zamiast tego brakujące lub nieunikatowe `x:Key` wartości powodują błędy analizatora XAML czasu ładowania. Jednak obsługa słowników dla WPF w programie Visual Studio może często zanotować takie błędy w fazie projektowania.  
  
 Należy zauważyć, że w pokazanej <xref:System.Windows.ResourceDictionary> składni obiekt jest niejawny w sposobie tworzenia kolekcji <xref:System.Windows.FrameworkElement.Resources%2A> przez procesor WPF XAML. Element nie <xref:System.Windows.FrameworkElement.Resources%2A> jest zwykle dostarczany w sposób jawny w znacznikach, chociaż może być w niektórych przypadkach, jeśli jest chciały do przejrzystości (będzie to element obiektu kolekcji między elementem właściwości i elementami w tym wypełnieniu <xref:System.Windows.ResourceDictionary> słownik). Aby uzyskać informacje o tym, dlaczego obiekt kolekcji prawie zawsze jest niejawny element w znaczniku, zobacz [Szczegóły składni XAML](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 W implementacji języka XAML WPF obsługa kluczy słownika zasobów jest definiowana przez <xref:System.Windows.ResourceKey> klasę abstrakcyjną. Jednak procesor WPF XAML produkuje różne podstawowe typy rozszerzeń dla kluczy na podstawie ich użycia. Na przykład klucz dla <xref:System.Windows.DataTemplate> lub dowolnej klasy pochodnej jest obsługiwany osobno i tworzy oddzielny <xref:System.Windows.DataTemplateKey> obiekt.  
  
 Klucze i nazwy używają różnych dyrektyw i elementów języka (`x:Key` a `x:Name`) w podstawowej definicji XAML. Klucze i nazwy są również używane w różnych sytuacjach przy użyciu definicji WPF i aplikacji. Aby uzyskać szczegółowe informacje, zobacz [WPF XAML Zakresy nazw WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak wspomniano wcześniej, wartość klucza może być dostarczana za pomocą rozszerzenia znacznika i może być inna niż wartość ciągu. Przykładowy scenariusz WPF polega na tym, że wartość `x:Key` może być [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Niektóre formanty uwidaczniają klucz stylu tego typu dla zasobu stylu niestandardowego, który wpływa na część wyglądu i zachowania tej kontrolki bez całkowitego zastępowania stylu. Przykładem takiego klucza jest <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkcja scalonego słownika WPF zawiera dodatkowe zagadnienia dotyczące unikatowego klucza i zachowania wyszukiwania kluczy. Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 Kod XAML 2009 ogranicza ograniczenia, które `x:Key` zawsze są udostępniane w formie atrybutu.  
  
 W programie WPF można używać funkcji języka XAML 2009, ale tylko dla języka XAML, który nie jest kompilowany do znaczników. Skompilowane znaczniki XAML dla WPF i forma BAML języka XAML nie obsługują obecnie słów kluczowych i funkcji języka XAML 2009.  
  
 W obszarze XAML 2009 można określić `x:Key` elementy za pomocą następującego użycia:  
  
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
  
- Nie pokazano tutaj kontenera/elementu nadrzędnego dla tego rodzaju użycia. `object`powinien być elementem podrzędnym elementu obiektu, który reprezentuje implementację wyspecjalizowanego słownika. `keyObject`oczekuje się, że jest to wystąpienie obiektu (lub wartość typu wartości), które jest odpowiednie jako klucz dla danej implementacji wyspecjalizowanego słownika.  
  
- WPF nie implementuje słowników, które wymagają tego użycia. Klucze obiektów to bardziej ogólna funkcja języka XAML, prawdopodobnie przydatna w przypadku niektórych scenariuszy słownika niestandardowego, w których tworzenie słownika w języku XAML jest pożądane. W przypadku funkcji WPF, takich jak niejawne style, które używają kluczy niebędących ciągami dla zasobów, inne techniki służące do ustanawiania lub określania kluczy istnieją, dlatego nie trzeba używać klucza obiektu.  
  
- *obiektem* typu może być również użycie rozszerzenia znacznika w formularzu elementu obiektu, a nie w bezpośrednim wystąpieniu obiektu.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użycia programu Silverlight  
 `x:Key`program Silverlight jest udokumentowany osobno. Aby uzyskać więcej informacji, [Zobacz Przestrzeń nazw XAML (x:) Funkcje języka (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](../wpf/advanced/xaml-resources.md)
- [Zasoby i kod](../wpf/advanced/resources-and-code.md)
- [StaticResource, rozszerzenie znaczników](../wpf/advanced/staticresource-markup-extension.md)
