---
title: Jak użyć zasobów aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460270"
---
# <a name="how-to-use-application-resources"></a>Jak użyć zasobów aplikacji
Ten przykład pokazuje, jak używać zasobów aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia plik definicji aplikacji. Plik definicji aplikacji definiuje sekcję zasobów (wartość właściwości <xref:System.Windows.Application.Resources%2A>). Do zasobów zdefiniowanych na poziomie aplikacji mogą być dostępne wszystkie inne strony, które są częścią aplikacji. W takim przypadku zasób jest zadeklarowanym stylem. Ponieważ pełny styl, który zawiera szablon kontrolki może być długi, ten przykład pomija szablon formantu, który jest zdefiniowany w <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> właściwości setter stylu.  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 W poniższym przykładzie przedstawiono stronę [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], która odwołuje się do zasobu na poziomie aplikacji, który został zdefiniowany w poprzednim przykładzie. Zasób jest przywoływany przy użyciu [rozszerzenia znacznika StaticResource](staticresource-markup-extension.md) , które określa unikatowy klucz zasobu dla żądanego zasobu. Na bieżącej stronie nie znaleziono żadnego zasobu z kluczem "GelButton", więc zakres wyszukiwania zasobów dla żądanego zasobu będzie przekroczyć bieżącą stronę i zdefiniowane zasoby na poziomie aplikacji.  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>Zobacz także

- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zarządzanie aplikacjami — omówienie](../app-development/application-management-overview.md)
- [Tematy z instrukcjami](resources-how-to-topics.md)
