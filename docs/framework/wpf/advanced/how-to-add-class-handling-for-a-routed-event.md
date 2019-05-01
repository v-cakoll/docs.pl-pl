---
title: 'Instrukcje: Dodawanie obsługi klasy dla zdarzenia trasowanego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 7b897954cbdab461dc0305c6290e67c1af5282c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777042"
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>Instrukcje: Dodawanie obsługi klasy dla zdarzenia trasowanego
Zdarzenia trasowane mogą być obsługiwane przez funkcje obsługi klas lub wystąpień obsługi na dowolny węzeł w trasie. Funkcje obsługi klas są wywoływane najpierw i może służyć przez implementacje klasy do pomijania zdarzenia z obsługi wystąpienia lub wprowadzenia innych zdarzeń zachowań określonych zdarzeń, które są własnością klas bazowych. W tym przykładzie przedstawiono dwie techniki ściśle powiązanych implementacji funkcje obsługi klas.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto klasy niestandardowej na podstawie <xref:System.Windows.Controls.Canvas> panelu. Podstawowe założenia aplikacji jest, że klasy niestandardowej wprowadza zachowań na jego elementy podrzędne, w tym przechwytywaniu klikniętego dowolnego przycisku myszy po lewej stronie i oznaczanie ich obsługę, zanim zostanie wywołana klasa elementu podrzędnego lub dowolnej obsługi wystąpienia na nim.  
  
 <xref:System.Windows.UIElement> Klasa udostępnia metodę wirtualną, która umożliwia obsługę na klasy <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> zdarzenia, po prostu zastępowanie zdarzenia. Jest to najprostszy sposób implementacji klasy obsługi, jeśli metoda wirtualna znajduje się gdzieś w swojej klasie hierarchii. Poniższy kod przedstawia <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementację w "MyEditContainer", która jest pochodną <xref:System.Windows.Controls.Canvas>. Implementacja oznacza zdarzenia jako obsługiwane w argumentach, a następnie dodanie kodu, aby zapewnić podstawowe widocznych zmian elementu źródłowego.  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 Jeśli wirtualny nie jest dostępny na klasach bazowych, lub dla tej konkretnej metody, klasy obsługi można dodać bezpośrednio przy użyciu metody narzędzie <xref:System.Windows.EventManager> klasy <xref:System.Windows.EventManager.RegisterClassHandler%2A>. Ta metoda powinna być wywoływana tylko w statyczne inicjowanie klas, które dodajesz Obsługa klasy. Ten przykład dodaje innego programu obsługi dla <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , a w tym przypadku zarejestrowanych klasy niestandardowej klasy. Korzystając z elementów wirtualnych, zarejestrowanych klasy jest naprawdę <xref:System.Windows.UIElement> klasy bazowej. W przypadkach, w której klasy podstawowe, jak i podklasy zarejestrować klasy obsługi są wywoływane najpierw obsługi podklasę. Zachowanie w aplikacji będzie, że najpierw ten program obsługi będzie przedstawiała jej okno komunikatu, a następnie zostaną pokazane zmianę wizualną metody wirtualnej programu obsługi.  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.EventManager>
- [Oznaczanie zdarzeń trasowanych jako obsłużonych oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md)
- [Obsługa zdarzenia trasowanego](how-to-handle-a-routed-event.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
