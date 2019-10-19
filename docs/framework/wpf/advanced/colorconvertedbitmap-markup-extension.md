---
title: ColorConvertedBitmap — Rozszerzenie znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 7d14ddc6276b9dd7baee12e267e8af1250bc11ab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582770"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap — Rozszerzenie znaczników
Umożliwia określenie źródła mapy bitowej, które nie ma osadzonego profilu. Konteksty koloru/profile są określane przez identyfikator URI, ponieważ jest to identyfikator URI źródła obrazu.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`imageSource`|Identyfikator URI nieprofilowanej mapy bitowej.|  
|`sourceIIC`|Identyfikator URI konfiguracji profilu źródłowego.|  
|`destinationIIC`|Identyfikator URI konfiguracji profilu docelowego|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie znacznika służy do wypełnienia powiązanego zestawu wartości właściwości źródła obrazu, takich jak <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. nie można użyć `ColorConvertedBitmap` (lub `ColorConvertedBitmapExtension`) w składni elementu właściwości, ponieważ wartości można ustawić tylko jako wartości w konstruktorze początkowym, który jest ciągiem następującym po identyfikatorze rozszerzenia.  
  
 `ColorConvertedBitmap` to rozszerzenie znaczników. Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach. Wszystkie rozszerzenia znaczników w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używają znaków {i} w ich składni atrybutów, która jest konwencją, za pomocą której procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybut. Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Obrazowanie — przegląd](../graphics-multimedia/imaging-overview.md)
