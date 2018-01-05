---
title: "Porady: obsługa zdarzenia ContextMenuOpening"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eec8646a48f94fb9ffdcad14849416732618a06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>Porady: obsługa zdarzenia ContextMenuOpening
<xref:System.Windows.FrameworkElement.ContextMenuOpening> Zdarzeń mogą być obsługiwane w aplikacji albo dostosować istniejący przed menu kontekstu do wyświetlania lub pominąć menu, które w przeciwnym razie będzie wyświetlana przez ustawienie <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwości `true` w danych zdarzenia. Typowe przyczyny ustawienie <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true` zdarzeń danych ma zastąpić menu całkowicie nową <xref:System.Windows.Controls.ContextMenu> obiektów, co wymaga czasami anulowanie operacji i uruchomienie nowej Otwórz. Podczas pisania obsług dla <xref:System.Windows.FrameworkElement.ContextMenuOpening> zdarzenia, należy zwrócić uwagę problemy dotyczące synchronizacji między <xref:System.Windows.Controls.ContextMenu> kontroli i usługi, która jest odpowiedzialna za otwierania i ogólnie pozycjonowanie menu kontekstowe dla formantów. W tym temacie przedstawiono niektóre techniki kodu dla różnych menu kontekstowe otwierania scenariuszy i przedstawiono w przypadku, gdy problem chronometrażu wejścia play.  
  
 Istnieje kilka scenariuszy obsługi <xref:System.Windows.FrameworkElement.ContextMenuOpening> zdarzeń:  
  
-   Dostosowywanie elementów menu przed wyświetlania.  
  
-   Wymiana całego menu przed wyświetlania.  
  
-   Całkowicie pomijanie dowolnego istniejącego menu kontekstowego i wyświetlanie nie menu kontekstowego.  
  
## <a name="example"></a>Przykład  
  
## <a name="adjusting-the-menu-items-before-display"></a>Dostosowywanie elementów Menu przed wyświetlania  
 Dostosowywanie istniejących elementów menu jest dość proste i prawdopodobnie najbardziej typowym scenariuszem. Możesz zrobić to w celu dodania lub odjęcia opcje menu kontekstowego w odpowiedzi na bieżące informacje o stanie w aplikacji lub informacje określonym stanie, które są dostępne jako właściwość obiektu, w którym wymagany jest menu kontekstowego.  
  
 Ogólne technika jest uzyskać źródło zdarzenia, czyli określonego formantu, klikniętej i pobrać <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwości z niego. Zazwyczaj chcesz sprawdzić <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji, aby zobaczyć, jakie elementy menu kontekstowego już istnieje w menu i dodać lub usunąć odpowiednie nowych <xref:System.Windows.Controls.MenuItem> elementy do lub z kolekcji.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>Wymiana całego Menu przed wyświetlania  
 Alternatywne scenariusz jest, jeśli chcesz zamienić menu kontekstowe całego. Oczywiście również umożliwiają zmianę o poprzednim kodzie usunięcia każdego elementu istniejącego menu kontekstowe i dodać nowe, począwszy od elementu zero. Ale jest bardziej intuicyjne podejście do zastępowania wszystkie elementy w menu kontekstowym, aby utworzyć nową <xref:System.Windows.Controls.ContextMenu>, należy umieścić w nim elementów, a następnie ustaw <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> właściwości formantu, który ma być nowe <xref:System.Windows.Controls.ContextMenu>.  
  
 Poniżej znajduje się kod obsługi prostego do zastępowania <xref:System.Windows.Controls.ContextMenu>. Kod odwołuje się do niestandardowego `BuildMenu` metodę, która jest oddzielona się, ponieważ jest ona wywoływana więcej niż jeden z programów obsługi przykład.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 Jednak jeśli używasz tego stylu obsługi dla <xref:System.Windows.FrameworkElement.ContextMenuOpening>, potencjalnie może narazić błąd synchronizacji, jeśli obiektu, w których konfigurujesz <xref:System.Windows.Controls.ContextMenu> nie ma istniejących menu kontekstowego. Po kliknięciu formantu, <xref:System.Windows.FrameworkElement.ContextMenuOpening> jest uruchamiany nawet wtedy, gdy istniejące <xref:System.Windows.Controls.ContextMenu> jest pusta lub ma wartość null. W tym przypadku niezależnie od nowego <xref:System.Windows.Controls.ContextMenu> ustawiony w źródle element za późno dociera do wyświetlenia. Ponadto jeśli użytkownik kliknij prawym przyciskiem myszy na drugim, tym razem nowej <xref:System.Windows.Controls.ContextMenu> pojawia się, wartość jest zerowa, a Twoje obsługi prawidłowo zastąpi i wyświetlić menu, gdy program obsługi jest uruchamiany po raz drugi. Sugeruje to dwa możliwe obejścia:  
  
1.  Upewnić się, że <xref:System.Windows.FrameworkElement.ContextMenuOpening> uchwyty są zawsze uruchamiane z formantami, które mają co najmniej symbol zastępczy <xref:System.Windows.Controls.ContextMenu> dostępne, które mają zostać zastąpione przez kod obsługi. W takim przypadku można nadal używać programu obsługi w poprzednim przykładzie, ale zwykle można przypisać symbol zastępczy <xref:System.Windows.Controls.ContextMenu> w znaczniku początkowej:  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  Przyjęto założenie, że początkowe <xref:System.Windows.Controls.ContextMenu> wartość może być null, oparte na logikę wstępne. Można albo wyboru <xref:System.Windows.Controls.ContextMenu> do wartości null, lub Użyj flagi w kodzie, aby sprawdzić, czy został programu obsługi Uruchom co najmniej raz. Ponieważ zakłada, że <xref:System.Windows.Controls.ContextMenu> jest o być wyświetlane, programu obsługi, a następnie ustawia <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true` w danych zdarzenia. Aby <xref:System.Windows.Controls.ContextMenuService> jest odpowiedzialny za wyświetlanie menu kontekstowego, `true` wartość <xref:System.Windows.RoutedEventArgs.Handled%2A> zdarzeń danych reprezentuje żądanie, aby anulować wyświetlanie menu kontekstowe / sterowania kombinacja, który wywołał zdarzenie.  
  
 Teraz, gdy menu kontekstowe potencjalnie podejrzanego zostały pominięte, następnym krokiem jest Podaj nową nazwę, a następnie wyświetla go. Ustawienie nowego jedną jest zasadniczo taki sam jak poprzednią procedurę obsługi: należy utworzyć nowy <xref:System.Windows.Controls.ContextMenu> i ustaw źródło kontroli <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> właściwości z nią. Dodatkowego kroku jest, że możesz teraz wymusić wyświetlanie menu kontekstowego ponieważ pominięto przy pierwszej próbie. Aby wymusić wyświetlania, należy ustawić <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType> właściwości `true` w ramach programu obsługi. Należy zachować ostrożność to zrobisz, ponieważ otwarcie menu kontekstowego w obsłudze zgłasza <xref:System.Windows.FrameworkElement.ContextMenuOpening> zdarzenia ponownie. Jeśli ponownie programu obsługi, staje się on nieograniczonej cyklicznego. Dlatego należy zawsze sprawdzić `null` lub Użyj flagi, jeśli możesz otworzyć z poziomu menu kontekstowe <xref:System.Windows.FrameworkElement.ContextMenuOpening> obsługi zdarzeń.  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>Pomijanie dowolnego istniejącego Menu kontekstowego i wyświetlanie nie Menu kontekstowe  
 Końcowe scenariuszu pisanie programu obsługi, które pomijają menu całkowicie, jest rzadko. Jeśli dany formant nie może wyświetlić menu kontekstowe, metodami prawdopodobnie bardziej odpowiednie do zapewnienia to niż przez tylko wtedy, gdy użytkownik zażąda go z pominięciem menu. Ale jeśli chcesz użyć programu obsługi do pomijania menu kontekstowe i nie wyświetlaj nic, a następnie po prostu należy ustawić programu obsługi <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true` w danych zdarzenia. <xref:System.Windows.Controls.ContextMenuService> Jest odpowiedzialny za wyświetlanie menu kontekstowego będzie sprawdzać dane zdarzenia zdarzenia pojawiającego się w formancie. Jeśli zdarzenie zostało oznaczone <xref:System.Windows.RoutedEventArgs.Handled%2A> dowolnym wzdłuż trasy, następnie akcji Otwórz menu kontekstu, który zainicjował zdarzenia jest pomijane.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>  
 [Przegląd elementów podstawowych](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [ContextMenu — przegląd](../../../../docs/framework/wpf/controls/contextmenu-overview.md)
