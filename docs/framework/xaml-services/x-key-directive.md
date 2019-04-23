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
ms.openlocfilehash: 6ac878f24de594f8557ded8b0c3356217021b035
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223722"
---
# <a name="xkey-directive"></a>x:Key — dyrektywa
Jednoznacznie identyfikuje elementy, które są tworzone i wspominane w słowniku zdefiniowanym w języku XAML. Dodawanie `x:Key` wartość do elementu obiektu XAML jest najczęstszym sposobem identyfikacji zasobu w słowniku zasobów, na przykład w programie WPF <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Użycie atrybutu XAML (charakterystyczne dla WPF)  
  
```  
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
|`stringKeyValue`|Ciąg tekstowy używany jako klucz. Ciąg tekstowy, musi być zgodna z [xamlname — gramatyka](xamlname-grammar.md).|  
|`markupExtensionUsage`|W ramach ograniczniki rozszerzenie znaczników {}, użycie rozszerzenia znaczników, który zawiera obiekt ma być używany jako klucz. Zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Key` obsługuje pojęcia słownika zasobów XAML. XAML jako język nie definiuje implementacji słownika zasobów, która pozostała do określonych platform tworzenia interfejsu użytkownika. Aby dowiedzieć się więcej na temat sposobu implementacji słowników zasobów XAML w WPF, zobacz [zasoby XAML](../wpf/advanced/xaml-resources.md).  
  
 W XAML 2006 i środowisku WPF `x:Key` musi zostać podana jako atrybut. Możesz nadal używać kluczy typu nonstring, ale wymaga to użycia rozszerzenia znaczników w celu zapewnienia wartości typu nonstring w formie atrybutu. Jeśli używasz XAML 2009 r. `x:Key` może być określony jako element, do obsługi jawnej słowników zaszyfrowanych przez typy obiektów inne niż ciągi bez konieczności pośrednika rozszerzenia znaczników. Zobacz sekcję "XAML 2009", w tym temacie. Pozostała część sekcji Uwagi dotyczy w szczególności implementacji XAML 2006.  
  
 Wartość atrybutu `x:Key` może być dowolnym ciągiem zdefiniowanym w [xamlname — gramatyka](xamlname-grammar.md) lub obiektem ocenianym poprzez rozszerzenie znaczników. Na przykład z WPF, zobacz "Uwagi dotyczące użycia WPF".  
  
 Elementy podrzędne elementu nadrzędnego, który jest <xref:System.Collections.IDictionary> implementacji muszą zazwyczaj zawierać `x:Key` atrybut, który określa unikalną wartość kluczową w ramach tego słownika. Środowiska mogą implementować Aliasy właściwości klucza do podstawienia w `x:Key` w określonych typach; typy, które definiują takie właściwości, powinny mieć atrybut <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Odpowiednikiem kodu dla określania `x:Key` jest klucz, który jest używany dla poniższych <xref:System.Collections.IDictionary>. Na przykład `x:Key` zastosowany w znaczniku dla zasobu w technologii WPF jest równoważny wartości `key` parametru <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> podczas dodawania zasobu do WPF <xref:System.Windows.ResourceDictionary> w kodzie.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użytkowania WPF  
 Obiekty podrzędne elementu nadrzędnego obiektu, to znaczy <xref:System.Collections.IDictionary> implementacji, takich jak WPF <xref:System.Windows.ResourceDictionary>, muszą zazwyczaj zawierać `x:Key` atrybut i wartości klucza muszą być unikatowe w ramach tego słownika. Istnieją dwa znaczące wyjątki:  
  
-   Niektóre typy WPF deklarują niejawny klucz do użycia słownika. Na przykład <xref:System.Windows.Style> z <xref:System.Windows.Style.TargetType%2A>, lub <xref:System.Windows.DataTemplate> z <xref:System.Windows.DataTemplate.DataType%2A>, mogą znajdować się w <xref:System.Windows.ResourceDictionary> i używać klucza niejawnego.  
  
-   WPF obsługuje pojęcie słownika scalonych zasobów. Klucze mogą być współużytkowane między scalonymi słownikami, a zachowania klucza udostępnionego można uzyskać dostęp za pomocą <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../wpf/advanced/merged-resource-dictionaries.md).  
  
 W ogólnym WPF XAML implementacji i aplikacji modelu unikatowość klucza nie jest sprawdzana przez kompilator znaczników XAML. Zamiast tego brakujące lub nieunikatowe `x:Key` wartości powodują błędy analizatora składni XAML czas ładowania. Jednak program Visual Studio Obsługa słowników WPF często może wychwycić takie błędy w fazie projektowania.  
  
 Należy pamiętać, że w składni przedstawionej <xref:System.Windows.ResourceDictionary> obiektu jest niejawny w jak procesor XAML w WPF generuje kolekcję, aby wypełnić <xref:System.Windows.FrameworkElement.Resources%2A> kolekcji. A <xref:System.Windows.ResourceDictionary> jest nie zazwyczaj wyraźnie oznaczony jako element adiustacji, chociaż może być w niektórych przypadkach dla jasności (będzie to element kolekcji obiektów między <xref:System.Windows.FrameworkElement.Resources%2A> element właściwości i elementy w tym wypełnienia Słownik). Aby dowiedzieć się, jak Dlaczego obiekt kolekcji prawie zawsze jest niejawnym elementem w znacznikach, zobacz [składnia XAML w szczegółów](../wpf/advanced/xaml-syntax-in-detail.md).  
  
 W implementacji XAML w WPF obsługa dla kluczy słownika zasobu jest definiowany przez <xref:System.Windows.ResourceKey> klasy abstrakcyjnej. Jednak procesor XAML w WPF produkuje różne podstawowe typy rozszerzeń dla kluczy, w oparciu o ich użycia. Na przykład klucz dla <xref:System.Windows.DataTemplate> lub dowolnej klasy pochodnej jest obsługiwany osobno i tworzy oddzielny <xref:System.Windows.DataTemplateKey> obiektu.  
  
 Klucze i nazwy używają różnych dyrektyw i elementów języka (`x:Key` a `x:Name`) do podstawowych definicji XAML. Klucze i nazwy są również używane w różnych sytuacjach przez definicje środowiska WPF i zastosowania tych koncepcji. Aby uzyskać więcej informacji, zobacz [zakresy WPF XAML nazw](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak wspomniano wcześniej, wartość klucza mogą być dostarczane za pośrednictwem rozszerzenia adiustacji i może być inna niż wartość ciągu. Przykładowy scenariusz WPF jest wartością `x:Key` może być [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md). Niektóre formanty zmieniają klucz stylu tego typu zasobu styl niestandardowy, który wpływa częściowo na wygląd i zachowanie tego formantu, bez zastępowania całego stylu. Przykładem takiego klucza jest <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkcja scalonych słowników WPF wprowadza dodatkowe zagadnienia dotyczące kluczowej unikatowości i kluczowego zachowania wyszukiwania. Aby uzyskać więcej informacji, zobacz [scalone słowniki zasobów](../wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 zwalnia ograniczenie, `x:Key` zawsze ma być dostarczane w formie atrybutu.  
  
 W środowisku WPF można użyć funkcji XAML 2009, ale tylko dla XAML, która nie jest kompilowana do znaczników. XAML kompilowana do znaczników dla platformy WPF i formularz BAML XAML aktualnie nie obsługują tych funkcji i słowa kluczowe XAML 2009.  
  
 W obszarze XAML 2009, można określić `x:Key` elementów za pomocą następującego użycia:  
  
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
|`keyObject`|Element obiektu dla obiektu, który jest używany jako klucz dla danego `object` w słowniku specjalistycznym.|  
  
-   Kontener/element nadrzędny tego rodzaju wykorzystania nie jest wyświetlane w tym miejscu. `object` powinien być elementem podrzędnym elementu obiekt, który reprezentuje implementację słownika specjalistycznego. `keyObject` oczekuje się wystąpienia obiektu (lub wartością typu wartości) które jest właściwe jako klucz dla tej określonej implementacji słownika specjalistycznego.  
  
-   WPF nie implementuje słowników, które wymagają tego użycia. Klucze obiektów to bardziej ogólna funkcja języka XAML, ewentualnie przydatna w niektórych scenariuszach słowników niestandardowych, gdzie jest pożądane tworzenie słownika w XAML. W przypadku funkcji środowiska WPF takich jak niejawna style, które używają kluczy niebędących ciągami dla zasobów inne techniki dla ustanowienia lub określania kluczy istnieją, więc używanie klucza obiektu nie jest konieczne.  
  
-   *keyObject* może być również użyciem rozszerzenia znaczników w formularzu elementów obiektu, a nie bezpośrednim wystąpieniem obiektu.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użytkowania Silverlight  
 `x:Key` dla programu Silverlight jest opisane osobno. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](../wpf/advanced/xaml-resources.md)
- [Zasoby i kod](../wpf/advanced/resources-and-code.md)
- [StaticResource, rozszerzenie znaczników](../wpf/advanced/staticresource-markup-extension.md)
