---
title: "Jak malować obszar pędzlem systemowym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 355df3718d90768cdfa8bc9780c44c19eb4bf9bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a>Jak malować obszar pędzlem systemowym
<xref:System.Windows.SystemColors> Klasy zapewnia dostęp do systemu pędzle i kolory, takich jak <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, i <xref:System.Windows.SystemColors.DesktopBrush%2A>. Pędzel systemu <xref:System.Windows.Media.SolidColorBrush> obiekt, który umożliwia malowanie obszar kolorem określonego systemu. Pędzel systemu zawsze daje wypełnieniem; Nie można użyć do Tworzenie gradientu.  
  
 Pędzle system służy jako statyczne lub dynamiczne zasobów. Użyj zasobu dynamicznego pędzla do automatycznej aktualizacji, jeśli użytkownik zmieni pędzla systemu, ponieważ aplikacja jest uruchomiona; w przeciwnym razie użyj statycznych zasobów. Klasa SystemColors zawiera szereg statycznej właściwości, które strict konwencją nazewnictwa:  
  
-   *\<SystemColor >*pędzla  
  
     Pobiera statyczny odwołanie do <xref:System.Windows.Media.SolidColorBrush> koloru określonego systemu.  
  
-   *\<SystemColor >*BrushKey  
  
     Pobiera dynamiczny odwołanie do <xref:System.Windows.Media.SolidColorBrush> koloru określonego systemu.  
  
-   *\<SystemColor >*kolorów  
  
     Pobiera statyczny odwołanie do <xref:System.Windows.Media.Color> struktury kolorów określonego systemu.  
  
-   *\<SystemColor >*ColorKey  
  
     Pobiera dynamiczny odwołanie do <xref:System.Windows.Media.Color> struktury kolorów określonego systemu.  
  
 Jest kolorem systemowym <xref:System.Windows.Media.Color> struktury, który może służyć do konfigurowania pędzla. Na przykład można utworzyć przy użyciu kolorów systemu przez ustawienie gradientu <xref:System.Windows.Media.GradientStop.Color%2A> właściwości <xref:System.Windows.Media.LinearGradientBrush> obiektu gradientu kolorów systemu. Na przykład zobacz [kolorów systemu używany w gradiencie](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto odwołania pędzla dynamicznego systemu można ustawić tło przycisku.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 W następnym przykładzie użyto odwołania pędzla systemu statycznego można ustawić tło przycisku.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 Na przykład przedstawiający sposób użycia kolorem systemowym w gradiencie zobacz [Użyj kolorów systemu w gradiencie](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kolory System używany w gradiencie](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [Malowanie pełnych kolorów i gradientów — omówienie](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
