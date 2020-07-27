---
title: Style i szablony menu
description: Dowiedz się więcej na temat stylów i szablonów dla Windows Presentation Foundation kontrolki menu. Zmodyfikuj ControlTemplate, aby nadać formantowi unikatowy wygląd.
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 5187e4a479609686e39e043808931141ca52078c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164551"
---
# <a name="menu-styles-and-templates"></a>Style i szablony menu
W tym temacie opisano style i szablony dla <xref:System.Windows.Controls.Menu> kontrolki. Można zmienić wartość domyślną, <xref:System.Windows.Controls.ControlTemplate> aby dać formantowi unikatowy wygląd. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="menu-parts"></a>Części menu  
 <xref:System.Windows.Controls.Menu>Kontrolka nie ma żadnych nazwanych części.  
  
 Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate> dla elementu <xref:System.Windows.Controls.Menu> , szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w obrębie <xref:System.Windows.Controls.ScrollViewer> . ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element w <xref:System.Windows.Controls.Menu> ; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer> , należy podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter` .  
  
## <a name="menu-states"></a>Stany menu  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.Menu> kontrolki.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości to `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość ma `true` fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość ma `true` kontrolkę, która nie ma fokusu.|  
  
## <a name="menuitem-parts"></a>Elementy MenuItem  
 W poniższej tabeli wymieniono nazwane części <xref:System.Windows.Controls.Menu> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Obszar podmenu.|  
  
 Podczas tworzenia <xref:System.Windows.Controls.ControlTemplate> dla elementu <xref:System.Windows.Controls.MenuItem> , szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w obrębie <xref:System.Windows.Controls.ScrollViewer> . ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element w <xref:System.Windows.Controls.MenuItem> ; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym <xref:System.Windows.Controls.ScrollViewer> , należy podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter` .  
  
## <a name="menuitem-states"></a>Stany MenuItem  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.MenuItem> kontrolki.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> dołączonej właściwości to `false` .|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość ma `true` fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>Dołączona właściwość ma `true` kontrolkę, która nie ma fokusu.|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>Przykład menu i MenuItem ControlTemplate  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Menu> kontrolki.  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 Poniższy przykład pokazuje, jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.MenuItem> kontrolki.  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 Poniższy przykład definiuje `MenuScrollViewer` , który jest używany w poprzednim przykładzie.  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 W <xref:System.Windows.Controls.ControlTemplate> przykładach użyto co najmniej jednego z poniższych zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony formantu](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie formantu](control-customization.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Tworzenie szablonu dla kontrolki](../../../desktop-wpf/themes/how-to-create-apply-template.md)
