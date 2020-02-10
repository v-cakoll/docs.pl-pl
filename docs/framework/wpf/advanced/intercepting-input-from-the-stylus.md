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
ms.openlocfilehash: 7629843730a82584e94448ceac1ea574906876c9
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095141"
---
# <a name="intercepting-input-from-the-stylus"></a>Przechwycenie danych z pisaka
Architektura <xref:System.Windows.Input.StylusPlugIns> zapewnia mechanizm implementowania kontroli niskiego poziomu na <xref:System.Windows.Input.Stylus> danych wejściowych i tworzenia cyfrowych obiektów <xref:System.Windows.Ink.Stroke> Ink. Klasa <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> udostępnia mechanizm umożliwiający wdrożenie zachowania niestandardowego i zastosowanie go do strumienia danych pochodzących z urządzenia pióra w celu uzyskania optymalnej wydajności.  
  
 Ten temat zawiera następujące podsekcje:  
  
- [Architektura](#Architecture)  
  
- [Implementowanie wtyczek pióra](#ImplementingStylusPlugins)  
  
- [Dodawanie wtyczki do InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Podsumowanie](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> to ewolucja interfejsów API [StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) , opisana w temacie [Uzyskiwanie dostępu do danych wejściowych pióra i manipulowanie nimi](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).  
  
 Każda <xref:System.Windows.UIElement> ma właściwość <xref:System.Windows.UIElement.StylusPlugIns%2A>, która jest <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Można dodać <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do właściwości <xref:System.Windows.UIElement.StylusPlugIns%2A> elementu, aby manipulować danymi <xref:System.Windows.Input.StylusPoint> w miarę ich generowania. <xref:System.Windows.Input.StylusPoint> dane składają się ze wszystkich właściwości obsługiwanych przez dyskretyzatora systemu cyfrowego, w tym dane <xref:System.Windows.Input.StylusPoint.X%2A> i <xref:System.Windows.Input.StylusPoint.Y%2A> punktów, a także dane <xref:System.Windows.Input.StylusPoint.PressureFactor%2A>.  
  
 Obiekty <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> są wstawiane bezpośrednio do strumienia danych pochodzących z urządzenia <xref:System.Windows.Input.Stylus> po dodaniu <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do właściwości <xref:System.Windows.UIElement.StylusPlugIns%2A>. Kolejność, w jakiej wtyczki są dodawane do kolekcji <xref:System.Windows.UIElement.StylusPlugIns%2A>, wymusza kolejność, w jakiej będą otrzymywać <xref:System.Windows.Input.StylusPoint> dane. Na przykład jeśli dodasz wtyczkę filtru, która ogranicza dane wejściowe do określonego regionu, a następnie dodasz wtyczkę, która rozpoznaje gesty podczas pisania, wtyczka, która rozpoznaje gesty, otrzyma filtrowane <xref:System.Windows.Input.StylusPoint> dane.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementowanie wtyczek pióra  
 Aby zaimplementować wtyczkę, należy utworzyć klasę z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Ta klasa jest stosowana o strumieniu danych, w jakiej się znajduje w <xref:System.Windows.Input.Stylus>. W tej klasie można modyfikować wartości <xref:System.Windows.Input.StylusPoint> danych.  
  
> [!CAUTION]
> Jeśli <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> zgłasza lub powoduje wyjątek, aplikacja zostanie zamknięta. Należy dokładnie przetestować kontrolki, które zużywają <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i korzystać z kontrolki tylko wtedy, gdy masz pewność, że <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nie zgłosi wyjątku.  
  
 Poniższy przykład ilustruje wtyczkę, która ogranicza wprowadzanie piórem przez modyfikację wartości <xref:System.Windows.Input.StylusPoint.X%2A> i <xref:System.Windows.Input.StylusPoint.Y%2A> w <xref:System.Windows.Input.StylusPoint> danych, jak pochodzą one z urządzenia <xref:System.Windows.Input.Stylus>.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Dodawanie wtyczki do InkCanvas  
 Najprostszym sposobem użycia wtyczki niestandardowej jest zaimplementowanie klasy, która pochodzi od InkCanvas i dodanie jej do właściwości <xref:System.Windows.UIElement.StylusPlugIns%2A>.  
  
 Poniższy przykład ilustruje niestandardowy <xref:System.Windows.Controls.InkCanvas>, który filtruje atrament.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Jeśli dodasz `FilterInkCanvas` do aplikacji i uruchomisz ją, zobaczysz, że atrament nie jest ograniczony do regionu, dopóki użytkownik nie ukończy pociągnięć. Dzieje się tak, ponieważ <xref:System.Windows.Controls.InkCanvas> ma właściwość <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>, która jest <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i jest już elementem członkowskim kolekcji <xref:System.Windows.UIElement.StylusPlugIns%2A>. Niestandardowa <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> dodana do kolekcji <xref:System.Windows.UIElement.StylusPlugIns%2A> otrzymuje <xref:System.Windows.Input.StylusPoint> dane po <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> odbiera dane. W związku z tym dane <xref:System.Windows.Input.StylusPoint> nie będą filtrowane do momentu, gdy użytkownik wykryje pióro, aby zakończyć pociągnięcie. Aby odfiltrować atrament podczas jego rysowania, należy wstawić `FilterPlugin` przed <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Poniższy C# kod ilustruje niestandardowy <xref:System.Windows.Controls.InkCanvas>, który filtruje atrament w trakcie rysowania.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Podsumowanie  
 Dzięki wykorzystaniu własnych klas <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i wstawieniu ich do kolekcji <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> można znacznie ulepszyć zachowanie cyfrowego atramentu. Masz dostęp do danych <xref:System.Windows.Input.StylusPoint> w miarę ich generowania, co daje możliwość dostosowania <xref:System.Windows.Input.Stylus> danych wejściowych. Ponieważ masz taki dostęp do danych <xref:System.Windows.Input.StylusPoint>, można zaimplementować zbieranie i renderowanie farbą z optymalną wydajnością aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowana obsługa pisma odręcznego](advanced-ink-handling.md)
- [Uzyskiwanie dostępu do danych wejściowych pióra i manipulowanie nimi](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
