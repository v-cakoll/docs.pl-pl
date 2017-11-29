---
title: Przechwycenie danych z pisaka
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 611a2d2de56025e2f1b5add6106294834586f9af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="intercepting-input-from-the-stylus"></a>Przechwycenie danych z pisaka
<xref:System.Windows.Input.StylusPlugIns> Architektura udostępnia mechanizm dla implementacji kontrolę niskiego poziomu nad <xref:System.Windows.Input.Stylus> dane wejściowe i tworzenia elektroniczne pismo odręczne <xref:System.Windows.Ink.Stroke> obiektów. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Klasa udostępnia mechanizm do implementowania niestandardowych zachowania i zastosować je w strumieniu danych przesyłanych przez pióro urządzenie pod kątem uzyskania optymalnej wydajności.  
  
 Ten temat zawiera następujące podsekcje:  
  
-   [Architektura](#Architecture)  
  
-   [Implementowanie wtyczek pióra](#ImplementingStylusPlugins)  
  
-   [Dodawanie użytkownika wtyczki do InkCanvas.](#AddingYourPluginToAnInkCanvas)  
  
-   [Zawierania](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Jest rozwoju [StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) interfejsów API, które są opisane w [dostęp i manipulowanie piórem](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)w [Microsoft Windows XP Tablet PC Edition oprogramowania Zestaw deweloperski 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Każdy <xref:System.Windows.UIElement> ma <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwość, która jest <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Możesz dodać <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do elementu <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości do manipulowania <xref:System.Windows.Input.StylusPoint> danych, ponieważ jest generowany. <xref:System.Windows.Input.StylusPoint>dane zawierają wszystkie właściwości, które są obsługiwane przez system dyskretyzatora, w tym <xref:System.Windows.Input.StylusPoint.X%2A> i <xref:System.Windows.Input.StylusPoint.Y%2A> punktu danych, a także <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> danych.  
  
 Twoje <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> obiekty są wstawiane bezpośrednio w strumieniu danych przesyłanych przez <xref:System.Windows.Input.Stylus> urządzenia podczas dodawania <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości. Kolejność, w którym dodatki plug-in są dodawane do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji określa kolejność, w którym zostanie wyświetlony <xref:System.Windows.Input.StylusPoint> danych. Na przykład, jeśli można dodać filtr wtyczki ograniczającej danych wejściowych do określonego regionu, a następnie dodaj wtyczki, które rozpoznaje gesty, ponieważ są one zapisywane, wtyczka rozpoznającego gestów zostanie wyświetlony filtrowane <xref:System.Windows.Input.StylusPoint> danych.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementowanie wtyczek pióra  
 Aby zaimplementować wtyczki, klasa wyprowadzona z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Ta klasa jest stosowane o strumienia danych, ponieważ pochodzi z <xref:System.Windows.Input.Stylus>. W tej klasy można zmodyfikować wartości <xref:System.Windows.Input.StylusPoint> danych.  
  
> [!CAUTION]
>  Jeśli <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> zgłasza lub powoduje zgłoszenie wyjątku zostanie aplikacji. Należy dokładnie przetestować formanty używające <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i formantu należy używać tylko, jeśli masz pewność <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nie spowoduje zgłoszenie wyjątku.  
  
 W poniższym przykładzie pokazano wtyczka, która ogranicza wprowadzania danych piórem modyfikując <xref:System.Windows.Input.StylusPoint.X%2A> i <xref:System.Windows.Input.StylusPoint.Y%2A> wartości w <xref:System.Windows.Input.StylusPoint> pochodzą dane w postaci, w jakiej <xref:System.Windows.Input.Stylus> urządzenia.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Dodawanie użytkownika wtyczki do InkCanvas.  
 Najprostszym sposobem użycia niestandardowe wtyczka jest implementacja klasy, która jest pochodną InkCanvas i dodać go do <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości.  
  
 W poniższym przykładzie pokazano niestandardowego <xref:System.Windows.Controls.InkCanvas> który filtry pismo odręczne.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Jeśli dodasz `FilterInkCanvas` do aplikacji i uruchom ją, można zauważyć, że pismo odręczne nie jest ograniczone do regionu do, zakończone pociągnięcia przez użytkownika. Jest to spowodowane <xref:System.Windows.Controls.InkCanvas> ma <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> właściwość, która jest <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i jest już członkiem <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji. Niestandardowa <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> zostanie dodany do <xref:System.Windows.UIElement.StylusPlugIns%2A> odbiera kolekcji <xref:System.Windows.Input.StylusPoint> danych po <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> odbiera dane. W związku z tym <xref:System.Windows.Input.StylusPoint> danych nie będą filtrowane do czasu, po użytkownika wind pióra do końca linii. Aby filtrować pismo odręczne, jak użytkownik wprowadzi go, należy wstawić `FilterPlugin` przed <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Poniższy kod C# przedstawia niestandardowego <xref:System.Windows.Controls.InkCanvas> który filtry pismo odręczne podczas wprowadzania.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Wniosek  
 Przez wyprowadzanie własne <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> klasy i wstawianie ich do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> kolekcji, mogą znacznie zwiększyć zachowanie odręcznego cyfrowego. Masz dostęp do <xref:System.Windows.Input.StylusPoint> danych, ponieważ jest generowany, umożliwiając dostosować <xref:System.Windows.Input.Stylus> wejściowego. Ponieważ taki dostęp niskiego poziomu do <xref:System.Windows.Input.StylusPoint> danych, można zaimplementować odręczne kolekcji i renderowania z optymalną wydajnością aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zaawansowanych odręcznego](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Uzyskiwanie dostępu i operowanie nimi piórem](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
