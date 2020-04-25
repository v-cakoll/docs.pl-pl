---
title: ColorConvertedBitmap — Rozszerzenie znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: a5b491723a036c1b1fd0bb61736e6f2ee53fbcd3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141226"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap — Rozszerzenie znaczników
Umożliwia określenie źródła mapy bitowej, które nie ma osadzonego profilu. Konteksty koloru/profile są określane przez identyfikator URI, ponieważ jest to identyfikator URI źródła obrazu.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" ... />
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`imageSource`|Identyfikator URI nieprofilowanej mapy bitowej.|  
|`sourceIIC`|Identyfikator URI konfiguracji profilu źródłowego.|  
|`destinationIIC`|Identyfikator URI konfiguracji profilu docelowego|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie znacznika służy do wypełnienia powiązanego zestawu wartości właściwości źródła obrazu, takich jak <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. `ColorConvertedBitmap`(or `ColorConvertedBitmapExtension`) nie można użyć w składni elementu właściwości, ponieważ wartości można ustawić tylko jako wartości w konstruktorze początkowym, który jest ciągiem następującym po identyfikatorze rozszerzenia.  
  
 `ColorConvertedBitmap`jest rozszerzeniem znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której procesor rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Przegląd Obrazowanie](../graphics-multimedia/imaging-overview.md)
