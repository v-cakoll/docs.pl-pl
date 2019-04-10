---
title: Przechwycenie danych z pisaka
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
ms.openlocfilehash: 5c22c2862ae8b948787fd5e6ca16109aa2f52aef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218774"
---
# <a name="intercepting-input-from-the-stylus"></a>Przechwycenie danych z pisaka
<xref:System.Windows.Input.StylusPlugIns> Architektura zapewnia mechanizm implementowania kontrolę niskiego poziomu nad <xref:System.Windows.Input.Stylus> dane wejściowe i tworzenia cyfrowy atrament <xref:System.Windows.Ink.Stroke> obiektów. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Klasa udostępnia mechanizm do implementowania niestandardowe zachowanie i zastosować je do strumienia danych pochodzących z urządzeń pióra, aby uzyskać optymalną wydajność.  
  
 Ten temat zawiera następujące podsekcje:  
  
-   [Architektura](#Architecture)  
  
-   [Implementowanie dodatków plug-in pióra](#ImplementingStylusPlugins)  
  
-   [Dodawanie wtyczkę z elementem InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
-   [Wniosek](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Stanowi ewolucyjne rozwinięcie funkcji [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) interfejsów API, które są opisane w [dostęp i manipulowanie piórem](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)w [Microsoft Windows XP Tablet PC Edition oprogramowania Zestaw deweloperski 1.7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Każdy <xref:System.Windows.UIElement> ma <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwość, która jest <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Możesz dodać <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do elementu <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości do manipulowania <xref:System.Windows.Input.StylusPoint> dane w postaci, w jakiej są generowane. <xref:System.Windows.Input.StylusPoint> dane składają się z wszystkich właściwości, które są obsługiwane przez Dyskretyzator systemu, w tym <xref:System.Windows.Input.StylusPoint.X%2A> i <xref:System.Windows.Input.StylusPoint.Y%2A> punktów danych, a także <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> danych.  
  
 Twoje <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> obiekty są wstawiane bezpośrednio do strumienia danych pochodzących z <xref:System.Windows.Input.Stylus> urządzenia po dodaniu <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości. Kolejność, w którym dodatków plug-in są dodawane do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji decyduje o kolejności, w którym będą otrzymywać <xref:System.Windows.Input.StylusPoint> danych. Na przykład, jeśli możesz dodać filtr dodatku typu plug-in, który ogranicza dane wejściowe w danym regionie, a następnie dodaj wtyczkę, która rozpoznaje gestów, ponieważ są one zapisywane, wtyczka rozpoznającego gestów otrzyma filtrowane <xref:System.Windows.Input.StylusPoint> danych.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementowanie dodatków plug-in pióra  
 Aby wdrożyć wtyczki, należy wyprowadzić klasę z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Ta klasa jest stosowane o strumienia danych, ponieważ pochodzi z <xref:System.Windows.Input.Stylus>. W tej klasy można zmodyfikować wartości <xref:System.Windows.Input.StylusPoint> danych.  
  
> [!CAUTION]
>  Jeśli <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> zgłasza lub powoduje wyjątek zostanie aplikacji. Należy dokładnie przetestować formantów, które mogą korzystać <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i formantu należy używać tylko, jeśli masz pewność <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nie spowoduje zgłoszenie wyjątku.  
  
 W poniższym przykładzie pokazano wtyczki, który ogranicza możliwość użycia wejście pióra, modyfikując <xref:System.Windows.Input.StylusPoint.X%2A> i <xref:System.Windows.Input.StylusPoint.Y%2A> wartości w <xref:System.Windows.Input.StylusPoint> dane ponieważ pochodzą z <xref:System.Windows.Input.Stylus> urządzenia.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Dodawanie wtyczkę z elementem InkCanvas  
 Najprostszym sposobem użycia niestandardowe wtyczki jest aby implementować klasę, która jest pochodną InkCanvas i dodać go do <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości.  
  
 Poniższy przykład pokazuje niestandardowy <xref:System.Windows.Controls.InkCanvas> która filtruje pisma odręcznego.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Jeśli dodasz `FilterInkCanvas` do aplikacji i uruchom go, można zauważyć pisma odręcznego jest ograniczone do regionu, do czasu, po użytkownik kończy pociągnięcia. Jest to spowodowane <xref:System.Windows.Controls.InkCanvas> ma <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> właściwość, która jest <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i jest już członkiem <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji. Niestandardowy <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> dodanym do <xref:System.Windows.UIElement.StylusPlugIns%2A> odbiera kolekcji <xref:System.Windows.Input.StylusPoint> dane po <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> odbiera dane. W rezultacie <xref:System.Windows.Input.StylusPoint> dane nie będą filtrowane do czasu, po użytkownik wind zakończenie pociągnięcia pióra. Aby filtrować pisma odręcznego, jak użytkownik wprowadzi go, należy wstawić `FilterPlugin` przed <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Poniższy kod C# pokazuje niestandardowy <xref:System.Windows.Controls.InkCanvas> która filtruje pisma odręcznego, zgodnie z jej rysowania.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Wniosek  
 Przez wyprowadzanie własne <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> klasy i wstawiania ich do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> kolekcji, można znacznie zwiększyć zachowanie cyfrowego pisma odręcznego. Masz dostęp do <xref:System.Windows.Input.StylusPoint> dane ponieważ jest generowany, dzięki czemu możesz dostosować <xref:System.Windows.Input.Stylus> danych wejściowych. Ponieważ masz takiego niskiego poziomu dostępu do <xref:System.Windows.Input.StylusPoint> danych, można zaimplementować kolekcji pisma odręcznego i renderowanie z optymalną wydajnością aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowana obsługa atramentu](advanced-ink-handling.md)
- [Uzyskiwania dostępu i manipulowania piórem](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
