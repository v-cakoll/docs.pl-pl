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
ms.openlocfilehash: 17cf42a9d6d94d6ea12399561af5647df3b4d8c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181915"
---
# <a name="intercepting-input-from-the-stylus"></a>Przechwycenie danych z pisaka
Architektura <xref:System.Windows.Input.StylusPlugIns> zapewnia mechanizm implementacji niskiego <xref:System.Windows.Input.Stylus> poziomu kontroli nad wejściem <xref:System.Windows.Ink.Stroke> i tworzenia obiektów atramentu cyfrowego. Klasa <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> zapewnia mechanizm do zaimplementowania zachowania niestandardowego i zastosować go do strumienia danych pochodzących z urządzenia pióra dla optymalnej wydajności.  
  
 Ten temat zawiera następujące podsekcje:  
  
- [Architektura](#Architecture)  
  
- [Implementowanie wtyczek rysika](#ImplementingStylusPlugins)  
  
- [Dodawanie wtyczki do urządzenia InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Podsumowanie](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Architektura  
 Jest <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> to ewolucja interfejsów API [StylusInput,](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) opisane w [uzyskiwaniu dostępu i manipulowania pen input](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).  
  
 Każdy <xref:System.Windows.UIElement> ma <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwość, <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>która jest . Można dodać <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a do właściwości <xref:System.Windows.UIElement.StylusPlugIns%2A> elementu do <xref:System.Windows.Input.StylusPoint> manipulowania danymi, jak jest generowany. <xref:System.Windows.Input.StylusPoint>dane składają się ze wszystkich właściwości obsługiwanych przez <xref:System.Windows.Input.StylusPoint.X%2A> digitizer systemu, w tym danych i <xref:System.Windows.Input.StylusPoint.Y%2A> punktów, a także <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> danych.  
  
 Obiekty <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> są wstawiane bezpośrednio do strumienia <xref:System.Windows.Input.Stylus> danych pochodzących <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> z <xref:System.Windows.UIElement.StylusPlugIns%2A> urządzenia po dodaniu do właściwości. Kolejność, w jakiej wtyczki są <xref:System.Windows.UIElement.StylusPlugIns%2A> dodawane do kolekcji, <xref:System.Windows.Input.StylusPoint> decyduje o kolejności, w jakiej będą odbierać dane. Na przykład jeśli dodasz wtyczkę filtru, która ogranicza dane wejściowe do określonego regionu, a następnie dodasz wtyczkę, która rozpoznaje gesty <xref:System.Windows.Input.StylusPoint> podczas ich pisania, wtyczka rozpoznana gesty otrzyma filtrowane dane.  
  
<a name="ImplementingStylusPlugins"></a>
## <a name="implementing-stylus-plug-ins"></a>Implementowanie wtyczek rysika  
 Aby zaimplementować wtyczkę, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>należy wyprowadzić klasę z . Ta klasa jest stosowana o strumień danych, jak <xref:System.Windows.Input.Stylus>pochodzi z . W tej klasie można zmodyfikować <xref:System.Windows.Input.StylusPoint> wartości danych.  
  
> [!CAUTION]
> Jeśli <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> zgłasza lub powoduje wyjątek, aplikacja zostanie zamknięta. Należy dokładnie przetestować formanty, które zużywają <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> używać tylko formantu, jeśli masz pewność, że nie będzie zgłaszać wyjątek.  
  
 W poniższym przykładzie pokazano wtyczkę, która ogranicza dane <xref:System.Windows.Input.StylusPoint.X%2A> wejściowe pisaka, modyfikując wartości i <xref:System.Windows.Input.StylusPoint.Y%2A> wartości w <xref:System.Windows.Input.StylusPoint> danych, które pochodzą z <xref:System.Windows.Input.Stylus> urządzenia.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Dodawanie wtyczki do urządzenia InkCanvas  
 Najprostszym sposobem użycia niestandardowej wtyczki jest zaimplementowanie klasy, która wywodzi <xref:System.Windows.UIElement.StylusPlugIns%2A> się z InkCanvas i dodać ją do właściwości.  
  
 W poniższym przykładzie <xref:System.Windows.Controls.InkCanvas> pokazano niestandardowe, które filtruje atrament.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Jeśli dodasz `FilterInkCanvas` do aplikacji i uruchomisz ją, można zauważyć, że atrament nie jest ograniczony do regionu, dopóki użytkownik nie zakończy obrysu. Jest to <xref:System.Windows.Controls.InkCanvas> spowodowane <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> ma właściwość, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> która jest i <xref:System.Windows.UIElement.StylusPlugIns%2A> jest już członkiem kolekcji. Niestandardowe <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> dodane do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji <xref:System.Windows.Input.StylusPoint> odbiera <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> dane po otrzymaniu danych. W rezultacie <xref:System.Windows.Input.StylusPoint> dane nie zostaną odfiltrowane, dopóki użytkownik nie podniesie pióra, aby zakończyć obrys. Aby filtrować atrament podczas losowania go przez `FilterPlugin` użytkownika, należy wstawić przed <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Poniższy kod Języka C# <xref:System.Windows.Controls.InkCanvas> demonstruje niestandardowe, które filtruje atrament, jak jest rysowany.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Podsumowanie  
 Poprzez wyprowadzanie <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> własnych klas i <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> wstawianie ich do kolekcji, można znacznie poprawić zachowanie atramentu cyfrowego. Masz dostęp do <xref:System.Windows.Input.StylusPoint> danych, jak to jest generowane, co <xref:System.Windows.Input.Stylus> daje możliwość dostosowania danych wejściowych. Ponieważ masz taki niski poziom <xref:System.Windows.Input.StylusPoint> dostępu do danych, można zaimplementować zbieranie i renderowanie pisma odurzającego z optymalną wydajnością dla aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowana obsługa atramentu](advanced-ink-handling.md)
- [Uzyskiwanie dostępu do danych wejściowych pióra i manipulowanie nimi](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
