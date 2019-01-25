---
title: 'Instrukcje: Użyj zasobów aplikacji'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: acd172448ebdefd6395feec6ad50e1c9491d9e27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733600"
---
# <a name="how-to-use-application-resources"></a>Instrukcje: Użyj zasobów aplikacji
W tym przykładzie pokazano, jak korzystać z zasobów aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje plik definicji aplikacji. Plik definicji aplikacji definiuje sekcję zasobów (wartość <xref:System.Windows.Application.Resources%2A> właściwości). Zasoby zdefiniowane na poziomie aplikacji jest możliwy przez wszystkich stron, które są częścią aplikacji. W tym przypadku zasób jest zadeklarowana stylu. Ponieważ pełną stylu, który zawiera szablon kontrolki może być długi, w tym przykładzie pomija szablonu kontrolki, która jest zdefiniowana w <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> metoda ustawiająca właściwości stylu.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 W poniższym przykładzie przedstawiono [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony, który odwołuje się do zasobu dodatku poziomu aplikacji, zdefiniowanego w poprzednim przykładzie. Zasób jest wywoływany przy użyciu [staticresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) , który określa klucz unikatowy zasób dla żądanego zasobu. Żaden zasób z kluczem "GelButton" znajduje się na bieżącej stronie, aby zakres wyszukiwania zasobów dla żądanego zasobu kontynuuje poza bieżącą stronę i do określonych zasobów na poziomie aplikacji.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Zobacz także
- [Zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)
- [Zarządzanie aplikacjami — omówienie](../../../../docs/framework/wpf/app-development/application-management-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
