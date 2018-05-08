---
title: Jak dodać obsługę klasy dla zdarzenia trasowanego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 85c3491c9035d807b4c654659a8641121bb5709f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>Jak dodać obsługę klasy dla zdarzenia trasowanego
Kierowane zdarzenia mogą być obsługiwane przez programy obsługi klasy lub wystąpienia obsługi na dowolny węzeł w trasie. Klasy obsługi są wywoływane najpierw i implementacji klasy można pominąć zdarzenia z obsługi wystąpienia lub wprowadzenie innych zachowań określonych zdarzeń na zdarzenia, które należą do klasy podstawowej. W tym przykładzie przedstawiono dwie metody ściśle związanych wykonawczych obsługę klas.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto niestandardowej klasy na podstawie <xref:System.Windows.Controls.Canvas> panelu. Podstawowe lokalnych aplikacji jest, że niestandardowej klasy wprowadza zachowań na jego elementy podrzędne, w tym przechwytywaniu klikniętego dowolnego przycisku myszy po lewej stronie i oznaczania ich obsługę, zanim zostanie wywołany klasa elementu podrzędnego lub dowolnego obsługi wystąpienia na nim.  
  
 <xref:System.Windows.UIElement> Klasa opisuje metodę wirtualnego umożliwia klasy obsługi na <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> zdarzenia przez zastąpienie po prostu zdarzenia. Jest to najprostszy sposób do zaimplementowania klasy obsługi, jeśli metoda wirtualna jest dostępna w hierarchii swojej klasy. Poniższy kod przedstawia <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementacja "MyEditContainer", która jest pochodną <xref:System.Windows.Controls.Canvas>. Implementacja oznacza zdarzenia, jako obsługiwane w argumentach, a następnie dodanie kodu umożliwiają elementu źródła podstawowe widocznych zmian.  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 Jeśli wirtualnego nie jest dostępne dla klas podstawowych lub dla określonej metody, klasy obsługi można dodać bezpośrednio za pomocą metody narzędzie <xref:System.Windows.EventManager> klasy <xref:System.Windows.EventManager.RegisterClassHandler%2A>. Ta metoda powinna być wywoływana tylko w statyczne zainicjowanie klasy, które dodajesz klasy obsługi. W tym przykładzie dodaje innego programu obsługi dla <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , i w takim przypadku zarejestrowanych klasy niestandardowej klasy. Z kolei, korzystając z elementów wirtualnych, zarejestrowanych klasy to naprawdę <xref:System.Windows.UIElement> klasy podstawowej. W przypadkach, gdy klasy podstawowe, jak i podklasy zarejestrować klasy obsługi najpierw są wywoływane programy obsługi podklasy. Zachowanie w aplikacji będą najpierw ten program obsługi może wyświetlić jego pola wiadomości, a następnie zostaną pokazane visual zmiany w obsłudze metody wirtualnej.  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.EventManager>  
 [Oznaczanie zdarzeń trasowanych jako obsłużonych oraz obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Obsługa zdarzenia trasowanego](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
