---
title: "ColorConvertedBitmap — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f1946ec2a5b607d9fce350da0676092d6e0407a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap — Rozszerzenie znaczników
Zapewnia możliwość określenia źródła mapy bitowej, który nie ma profilu osadzonego. Konteksty kolorów / profile są określane przez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], ponieważ źródło obrazu jest [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`imageSource`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Nonprofiled mapy bitowej.|  
|`sourceIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Źródło profilu konfiguracji.|  
|`destinationIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Miejsce docelowe profilu konfiguracji|  
  
## <a name="remarks"></a>Uwagi  
 Tego rozszerzenia znacznika jest przeznaczony do wypełnienia powiązany zestaw wartości właściwości źródło obrazu, takich jak <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. `ColorConvertedBitmap`(lub `ColorConvertedBitmapExtension`) nie można używać w składni elementu właściwości, ponieważ wartości można ustawić tylko jako wartości na początkowej konstruktora, który jest ciągiem następującego identyfikatora rozszerzenia.  
  
 `ColorConvertedBitmap`to rozszerzenie znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w ich składni atrybutu Konwencji za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Omówienie tworzenia obrazu](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
