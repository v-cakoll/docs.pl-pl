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
ms.openlocfilehash: 2547c0aa2f3a14080868c2760fa8999eb99d3d16
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046329"
---
# <a name="intercepting-input-from-the-stylus"></a>Przechwycenie danych z pisaka
Architektura zapewnia mechanizm implementowania kontroli niskiego poziomu nad <xref:System.Windows.Input.Stylus> danymi wejściowymi i tworzeniem obiektów atramentów <xref:System.Windows.Ink.Stroke> cyfrowych. <xref:System.Windows.Input.StylusPlugIns> <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Klasa udostępnia mechanizm umożliwiający wdrożenie zachowania niestandardowego i zastosowanie go do strumienia danych pochodzących z urządzenia pióra w celu uzyskania optymalnej wydajności.  
  
 Ten temat zawiera następujące podsekcje:  
  
- [Architektura](#Architecture)  
  
- [Implementowanie wtyczek pióra](#ImplementingStylusPlugins)  
  
- [Dodawanie wtyczki do InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Podsumowanie](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 Jest to ewolucja interfejsów API [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) , opisana w temacie [Uzyskiwanie dostępu do danych wejściowych pióra i manipulowanie nimi](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409), w [zestawie Microsoft Windows XP Tablet PC Edition Software Development Kit 1,7.](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409) <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>  
  
 Każda <xref:System.Windows.UIElement> z nich <xref:System.Windows.UIElement.StylusPlugIns%2A> ma właściwość, która <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>jest. Można dodać <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości elementu w celu manipulowania <xref:System.Windows.Input.StylusPoint> danymi, które są generowane. <xref:System.Windows.Input.StylusPoint>dane składają się ze wszystkich właściwości obsługiwanych przez dyskretyzatora systemowego, w tym <xref:System.Windows.Input.StylusPoint.X%2A> <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> dane i <xref:System.Windows.Input.StylusPoint.Y%2A> , a także dane.  
  
 Obiekty są wstawiane bezpośrednio do strumienia danych pochodzących <xref:System.Windows.Input.Stylus> z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> urządzenia po dodaniu do <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Kolejność, w jakiej wtyczki są dodawane do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji, wymusza kolejność, w jakiej będą otrzymywać <xref:System.Windows.Input.StylusPoint> dane. Na przykład jeśli dodasz wtyczkę filtru, która ogranicza dane wejściowe do określonego regionu, a następnie dodasz wtyczkę, która rozpoznaje gesty podczas pisania, wtyczka, która rozpoznaje gesty, będzie odbierać filtrowane <xref:System.Windows.Input.StylusPoint> dane.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementowanie wtyczek pióra  
 Aby zaimplementować wtyczkę, należy utworzyć klasę z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Ta klasa jest stosowana o strumieniu danych, z której <xref:System.Windows.Input.Stylus>pochodzą. W tej klasie można modyfikować wartości <xref:System.Windows.Input.StylusPoint> danych.  
  
> [!CAUTION]
> <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Jeśli zgłasza lub powoduje wyjątek, aplikacja zostanie zamknięta. Należy dokładnie przetestować kontrolki korzystające z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> i używać tylko kontrolki, jeśli masz pewność, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> że nie zgłosi wyjątku.  
  
 Poniższy przykład ilustruje wtyczkę, która ogranicza wprowadzanie piórem przez <xref:System.Windows.Input.StylusPoint.X%2A> modyfikację i <xref:System.Windows.Input.StylusPoint.Y%2A> wartości <xref:System.Windows.Input.StylusPoint> danych w postaci, w jakiej pochodzą z <xref:System.Windows.Input.Stylus> urządzenia.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Dodawanie wtyczki do InkCanvas  
 Najprostszym sposobem użycia wtyczki niestandardowej jest zaimplementowanie klasy, która pochodzi od InkCanvas i dodanie jej do <xref:System.Windows.UIElement.StylusPlugIns%2A> właściwości.  
  
 Poniższy przykład ilustruje niestandardowe <xref:System.Windows.Controls.InkCanvas> , które filtrują atrament.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Jeśli dodasz `FilterInkCanvas` do aplikacji i uruchomisz ją, zobaczysz, że atrament nie jest ograniczony do regionu, dopóki użytkownik nie ukończy pociągnięć. Dzieje się tak, <xref:System.Windows.Controls.InkCanvas> ponieważ <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> ma <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> właściwość, która jest i jest już elementem członkowskim <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekcji. Niestandardowy <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> dodany <xref:System.Windows.Input.StylusPoint> do kolekcji otrzymuje dane po <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> odebraniu danych. <xref:System.Windows.UIElement.StylusPlugIns%2A> W związku z tym <xref:System.Windows.Input.StylusPoint> dane nie będą filtrowane, dopóki użytkownik nie wykryje pióra, aby zakończyć pociągnięcie. Aby odfiltrować atrament w miarę jego rysowania, należy wstawić `FilterPlugin` element <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>przed.  
  
 Poniższy C# kod ilustruje niestandardowe <xref:System.Windows.Controls.InkCanvas> , które filtrują atrament w trakcie rysowania.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Wniosek  
 Dzięki wykorzystaniu własnych <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> klas i wstawieniu ich do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> kolekcji można znacznie ulepszyć zachowanie cyfrowego atramentu. Masz dostęp do <xref:System.Windows.Input.StylusPoint> danych w miarę ich generowania, co pozwala na <xref:System.Windows.Input.Stylus> dostosowanie danych wejściowych. Ponieważ masz taki dostęp do <xref:System.Windows.Input.StylusPoint> danych na niskim poziomie, możesz zaimplementować zbieranie i renderowanie farbą z optymalną wydajnością aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowana obsługa pisma odręcznego](advanced-ink-handling.md)
- [Uzyskiwanie dostępu do danych wejściowych pióra i manipulowanie nimi](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
