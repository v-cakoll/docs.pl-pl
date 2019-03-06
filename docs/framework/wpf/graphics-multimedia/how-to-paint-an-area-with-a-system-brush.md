---
title: 'Instrukcje: Maluj obszar pędzlem systemowym'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: 7beaf4370f115a3995c9ca23bb0022bd5b269193
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364115"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a>Instrukcje: Maluj obszar pędzlem systemowym
<xref:System.Windows.SystemColors> Klasy zapewnia dostęp do pędzli systemowych i kolorów, takich jak <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, i <xref:System.Windows.SystemColors.DesktopBrush%2A>. Pędzel system <xref:System.Windows.Media.SolidColorBrush> obiekt, który umożliwia malowanie obszaru za pomocą kolorów określonego systemu. Pędzel systemu zawsze daje wypełnienia kryjącego; Nie można utworzyć gradientu.  
  
 Pędzle systemowe służy jako statyczna lub dynamiczna zasobów. Użyj dynamicznych zasobów, jeśli chcesz, aby pędzla do automatycznej aktualizacji, jeśli użytkownik zmieni pędzla systemu, ponieważ aplikacja jest uruchomiona; w przeciwnym razie użyj zasób statyczny. Klasa SystemColors zawiera szereg statycznej właściwości, które postępuj zgodnie z ograniczeniami konwencji nazewnictwa:  
  
-   *\<SystemColor>* Brush  
  
     Pobiera odwołanie statyczne do <xref:System.Windows.Media.SolidColorBrush> koloru określonego systemu.  
  
-   *\<SystemColor>* BrushKey  
  
     Pobiera dynamiczny odwołanie do <xref:System.Windows.Media.SolidColorBrush> koloru określonego systemu.  
  
-   *\<SystemColor>* Color  
  
     Pobiera odwołanie statyczne do <xref:System.Windows.Media.Color> struktury kolorów określonego systemu.  
  
-   *\<SystemColor>* ColorKey  
  
     Pobiera dynamiczny odwołanie do <xref:System.Windows.Media.Color> struktury kolorów określonego systemu.  
  
 Kolor systemu jest <xref:System.Windows.Media.Color> strukturę, która może służyć do konfigurowania pędzla. Na przykład można utworzyć przy użyciu kolorów systemowych, ustawiając gradientu <xref:System.Windows.Media.GradientStop.Color%2A> właściwości <xref:System.Windows.Media.LinearGradientBrush> ograniczniki gradientu obiektu za pomocą kolorów systemowych. Aby uzyskać przykład, zobacz [Użyj kolorów systemowych w gradiencie](how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dynamicznego systemu odwołanie pędzla do Ustawianie tła przycisku.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 W następnym przykładzie użyto systemu statycznego odwołanie pędzla do Ustawianie tła przycisku.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 Na przykład przedstawiający sposób użycia kolorów systemowych w gradiencie zobacz [Użyj kolorów systemowych w gradiencie](how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="see-also"></a>Zobacz także
- [Używanie kolorów systemowych w gradiencie](how-to-use-system-colors-in-a-gradient.md)
- [Malowanie jednolitymi kolorami i gradientami — przegląd](painting-with-solid-colors-and-gradients-overview.md)
