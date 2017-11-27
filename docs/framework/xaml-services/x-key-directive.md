---
title: "x:Key — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5e2ad03fcb52db1ffdd01849381a392187082991
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xkey-directive"></a>x:Key — dyrektywa
Identyfikuje elementy, które są tworzone i przywoływany w słowniku zdefiniowany w języku XAML. Dodawanie `x:Key` wartość do elementu obiektu XAML jest najczęściej do identyfikacji zasobu w słowniku zasobów, na przykład na platformie WPF <xref:System.Windows.ResourceDictionary>.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>Użycie atrybutu XAML (WPF specyficzne)  
  
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
|`stringKeyValue`|Ciąg tekstowy, można użyć jako klucza. Ciąg tekstowy musi być zgodna z [xamlname — gramatyka](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
|`markupExtensionUsage`|W ramach {} ograniczniki rozszerzenia znaczników użycie rozszerzenia znaczników, która zapewnia obiekt, aby użyć jako klucza. Zobacz uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Key`obsługuje pojęcie słownika zasobów XAML. XAML jako język nie definiuje implementacji słownika zasobów, który jest od lewej do określonych platform interfejsu użytkownika. Aby dowiedzieć się więcej na temat implementowania słowniki zasobów XAML w WPF, zobacz [zasobów XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 W języku XAML 2006 i WPF `x:Key` musi być dostarczona jako atrybut. Można nadal używać kluczy typu, ale wymaga to użycia rozszerzenie znaczników w celu podania wartości typu w formie atrybutu. Jeśli używasz XAML 2009 `x:Key` może być określony jako element, do obsługi jawnie słowników, wyznaczaną przez obiekty mają typ innych niż ciągi bez konieczności pośredniego rozszerzeniem znacznika. Zobacz sekcję "XAML 2009" w tym temacie. W pozostałej części sekcji uwag w szczególności dotyczy implementacji XAML 2006.  
  
 Wartość atrybutu `x:Key` może być dowolny ciąg zdefiniowany w [xamlname — gramatyka](../../../docs/framework/xaml-services/xamlname-grammar.md) lub może być obiektem oceniane za pośrednictwem rozszerzenia znaczników. Na przykład z WPF, zobacz "Notatki dotyczące użytkowania WPF".  
  
 Elementy podrzędne elementu nadrzędnego, który jest <xref:System.Collections.IDictionary> zwykle musi zawierać implementację `x:Key` atrybut, który określa unikatową wartość klucza w ramach tego słownika. Struktury mogą implementować Aliasy właściwości klucza do zastąpienia dla `x:Key` w określonych typach; powinien mieć atrybut typy, które definiują takich właściwości <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Określanie odpowiednikiem kodu `x:Key` jest klucz, który służy do odpowiadającego <xref:System.Collections.IDictionary>. Na przykład `x:Key` jakie jest stosowane w znaczniku zasobów na platformie WPF jest odpowiednikiem wartości `key` parametr <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> po dodaniu zasobu WPF <xref:System.Windows.ResourceDictionary> w kodzie.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Obiekty podrzędne nadrzędny obiekt <xref:System.Collections.IDictionary> wdrażania, takie jak WPF <xref:System.Windows.ResourceDictionary>, zwykle musi zawierać `x:Key` atrybutu i wartości klucza muszą być unikatowe w obrębie tego słownika. Istnieją dwa godnymi uwagi wyjątkami:  
  
-   Niektóre typy WPF zadeklarować niejawne klucz dla słownika użycia. Na przykład <xref:System.Windows.Style> z <xref:System.Windows.Style.TargetType%2A>, lub <xref:System.Windows.DataTemplate> z <xref:System.Windows.DataTemplate.DataType%2A>, mogą znajdować się w <xref:System.Windows.ResourceDictionary> i użyj niejawne klucza.  
  
-   WPF obsługuje pojęcie słownika zasobów scalone. Klucze mogą udostępniać scalonych słownikach i zachowanie klucza udostępnionego można uzyskać dostęp za pomocą <xref:System.Windows.FrameworkContentElement.FindResource%2A>. Aby uzyskać więcej informacji, zobacz [scalić słowniki zasobów](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 W ogólnej WPF XAML wdrożenia i stosowania modelu unikatowości klucza nie jest sprawdzana przez kompilator znaczników XAML. Zamiast tego brakujące lub nieunikatowy `x:Key` wartości powodują błędy analizatora czasu ładowania XAML. Jednak [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] obsługi słowników dla WPF często może zanotować takie błędy w fazie projektowania.  
  
 Należy pamiętać, że w składni pokazano, <xref:System.Windows.ResourceDictionary> obiektu jest niejawnie w sposób procesora WPF XAML tworzy kolekcję, aby wypełnić <xref:System.Windows.FrameworkElement.Resources%2A> kolekcji. A <xref:System.Windows.ResourceDictionary> nie jest zwykle podana jawnie jako element w znaczniku, chociaż może być w niektórych przypadkach, jeśli dla jasności (byłoby elementu obiektu między <xref:System.Windows.FrameworkElement.Resources%2A> wypełniania elementu właściwości i elementów w tym Słownik). Aby uzyskać informacje o tym, dlaczego obiekt kolekcji jest prawie zawsze element niejawne w znaczniku, zobacz [szczegółów w składni języka XAML](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 W implementacji WPF XAML obsługę klucze słownika zasobów jest definiowana za pomocą <xref:System.Windows.ResourceKey> klasy abstrakcyjnej. Jednak procesora WPF XAML tworzy różne typy rozszerzeń podstawowej kluczy oparte na ich użycia. Na przykład klucz dla <xref:System.Windows.DataTemplate> lub dowolnej klasy pochodnej jest obsługiwane oddzielnie i tworzy oddzielny <xref:System.Windows.DataTemplateKey> obiektu.  
  
 Klucze i nazwy używają różnych dyrektywy i elementy języka (`x:Key` i `x:Name`) do podstawowych definicji XAML. Nazwy i klucze są również używane w różnych sytuacjach stosowania tych pojęć i definicji WPF. Aby uzyskać więcej informacji, zobacz [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Jak wspomniano wcześniej, wartość klucza mogą być dostarczane za pomocą rozszerzenia znacznika i może być inna niż wartość ciągu. Przykładowy scenariusz WPF jest wartością `x:Key` może być[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md). Niektóre formanty ujawnia klucz styl tego typu zasobu styl niestandardowy, który wpływa bez całkowicie zastępowania styl części wygląd i zachowanie tego formantu. Przykładem takiego klucza jest <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.  
  
 Funkcja połączony słownik WPF wprowadza dodatkowe zagadnienia dotyczące unikatowości klucza i zachowanie wyszukiwania klucza. Aby uzyskać więcej informacji, zobacz [scalić słowniki zasobów](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 zwalnia ograniczenie który `x:Key` zawsze być udostępniane w formie atrybutu.  
  
 Na platformie WPF można użyć XAML 2009 — funkcje, ale tylko dla języka XAML, który nie jest kompilowany do znaczników. Skompilowany kod znaczników XAML w WPF i BAML formę XAML aktualnie nie obsługują słowa kluczowe języka XAML 2009 i funkcje.  
  
 W obszarze XAML 2009, można określić `x:Key` elementów przy użyciu następującego użycia:  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>Użycie elementu XAML (tylko w języku XAML 2009)  
  
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
|`keyObject`|Element Object dla obiekt, który jest używany jako klucz dla danego `object` w słowniku specjalne.|  
  
-   Kontener/nadrzędne dla tego rodzaju użycie nie jest wyświetlane w tym miejscu. `object`powinien być elementem podrzędnym elementu obiektu, który reprezentuje implementację specjalne słownika. `keyObject`Oczekiwana wartość pola wystąpienia obiektu (lub wartość typu value) odpowiednią jako klucz dla tej implementacji określonego słownika specjalne.  
  
-   WPF nie implementuje słowników, które wymagają użycia. Klucze obiektu jest bardziej ogólne funkcji języka XAML, prawdopodobnie przydatne w przypadku niektórych scenariuszy słownika którym pożądane jest Tworzenie słownika w kodzie XAML. Dla funkcji WPF, takich jak niejawne style, które używają kluczy innych niż ciąg dla zasobów innych technik za ustanawianie lub określenie kluczy istnieje, więc przy użyciu klucza obiektu nie jest konieczne.  
  
-   *keyObject* mogą być również użytkowania rozszerzenie znaczników w formularzu elementu obiektu, a nie wystąpienia obiektu bezpośrednio.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użycia programu Silverlight  
 `x:Key`dla programu Silverlight jest udokumentowany oddzielnie. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka (platformy Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Zobacz też  
 [Zasoby dla języka XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Zasoby i kod](../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Rozszerzenie StaticResource znaczników](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
