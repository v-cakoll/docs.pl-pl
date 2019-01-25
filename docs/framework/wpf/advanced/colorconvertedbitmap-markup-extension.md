---
title: ColorConvertedBitmap — Rozszerzenie znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 4f71b90fa00d1aaee0ec5ad43e5a19be03c79c50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647650"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap — Rozszerzenie znaczników
Zapewnia sposób określania źródła mapy bitowej, który nie ma profilu osadzonego. Kolor kontekstów / profile są określone przez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], ponieważ jest źródło obrazu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`imageSource`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Dla nieprofilowanych mapy bitowej.|  
|`sourceIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Źródła konfiguracji profilu.|  
|`destinationIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Konfiguracji profil docelowy|  
  
## <a name="remarks"></a>Uwagi  
 Tego rozszerzenia znacznika jest przeznaczona do wypełnienia powiązany zestaw wartości właściwości źródło obrazu, takich jak <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. `ColorConvertedBitmap` (lub `ColorConvertedBitmapExtension`) nie można używać w składni elementu właściwości, ponieważ wartość można ustawić tylko jako wartości na początkowej konstruktora, który jest ciągiem następujące identyfikator rozszerzenia.  
  
 `ColorConvertedBitmap` jest rozszerzeniem znacznika. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Użyj {i} znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą którego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora rozpoznaje, że rozszerzenie znacznika musi wykonać przetwarzanie atrybutu. Aby uzyskać więcej informacji, zobacz [rozszerzenia znacznikowania i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [Obrazowanie — przegląd](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
