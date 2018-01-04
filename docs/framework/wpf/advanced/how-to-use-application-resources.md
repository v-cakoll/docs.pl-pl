---
title: "Jak użyć zasobów aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bac1fa1576e684a4b10f00310c08e4e7101a5df0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-application-resources"></a>Jak użyć zasobów aplikacji
Ten przykład przedstawia sposób użycia zasobów aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono plik definicji aplikacji. Plik definicji aplikacji definiuje sekcji zasobów (wartość <xref:System.Windows.Application.Resources%2A> właściwości). Przez wszystkie strony, które są częścią aplikacji są dostępne zasoby zdefiniowane na poziomie aplikacji. W takim przypadku zasób jest zadeklarowane stylu. Ponieważ pełną stylu, który zawiera szablon formantu może być długi, w tym przykładzie pomija kontroli szablonu, który jest definiowany w <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> metoda ustawiająca właściwości stylu.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 W poniższym przykładzie przedstawiono [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony, który odwołuje się do zasobu poziomie aplikacji, zdefiniowanego w poprzednim przykładzie. Zasób jest wywoływany przy użyciu [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) , który określa klucz unikatowy zasób do żądanego zasobu. Żaden zasób z kluczem "GelButton" znajduje się w bieżącej strony, dlatego zakres wyszukiwania zasobów dla żądanego zasobu nadal poza bieżącą stronę i do określonych zasobów na poziomie aplikacji.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Zarządzanie aplikacjami — omówienie](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
