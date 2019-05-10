---
title: 'Instrukcje: Obsługa zdarzenia ContextMenuOpening'
ms.date: 03/30/2017
helpviewer_keywords:
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
ms.openlocfilehash: b3d0f5c77ebf8527e4854d4edf12d6fa8a4b5f0c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614628"
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>Instrukcje: Obsługa zdarzenia ContextMenuOpening
<xref:System.Windows.FrameworkElement.ContextMenuOpening> Zdarzenia mogą być obsługiwane w aplikacji albo dostosować istniejący przed menu kontekstowe do wyświetlania lub Pomiń menu, które w przeciwnym razie będzie można wyświetlić, ustawiając <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwości `true` danych zdarzenia. Typową przyczyną ustawienia <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true` zdarzeń danych ma zastąpić menu całkowicie nową <xref:System.Windows.Controls.ContextMenu> obiektu, co czasami wymaga anuluje operację i uruchomienie nowej open. Jeśli podczas pisania procedur obsługi dla <xref:System.Windows.FrameworkElement.ContextMenuOpening> zdarzeń, powinno być znane problemy dotyczące synchronizacji między <xref:System.Windows.Controls.ContextMenu> kontroli i usługi, która jest odpowiedzialna za otwarcie i ogólnie rzecz biorąc pozycjonowanie menu kontekstowe dla formantów. W tym temacie pokazano niektóre z technik kodu dla różnych menu kontekstowe, otwierając scenariuszy i ilustruje przypadek, gdzie błąd synchronizacji jest dostarczany do gry.  
  
 Istnieje kilka scenariuszy obsługi <xref:System.Windows.FrameworkElement.ContextMenuOpening> zdarzeń:  
  
- Dostosowywanie elementów menu, zanim ekran.  
  
- Wymiana całego menu przed wyświetlania.  
  
- Całkowicie pomijanie dowolnego istniejącego menu kontekstowego i wyświetlanie nie menu kontekstowego.  
  
## <a name="example"></a>Przykład  
  
## <a name="adjusting-the-menu-items-before-display"></a>Dostosowywanie elementów Menu, zanim ekran  
 Dostosowując istniejące elementy menu jest dość proste i prawdopodobnie najbardziej typowym scenariuszem. Być może w tym w celu dodania lub odjęcia opcje menu kontekstowego w odpowiedzi na bieżące informacje o stanie w aplikacji lub informacje o stanie określonej, która jest dostępna jako właściwość obiektu, w którym wymagany jest menu kontekstowego.  
  
 Ogólne techniką jest źródło zdarzenia, czyli określonego formantu, który został kliknięty prawym przyciskiem myszy oraz <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwości z niego. Zazwyczaj chcesz sprawdzić <xref:System.Windows.Controls.ItemsControl.Items%2A> kolekcji, aby zobaczyć, jakie elementy menu kontekstowego już istnieje w tym celu w menu i dodać lub usunąć odpowiednie nowe <xref:System.Windows.Controls.MenuItem> elementy do lub z kolekcji.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>Zastępowanie całe Menu przed wyświetlania  
 Alternatywny scenariusz polega na tym, jeśli chcesz zamienić menu kontekstowe całego. Odmiana dla poprzedniego kodu, oczywiście można również służy do usuwania każdy element istniejącego menu kontekstowe i dodawać nowe, począwszy od elementu zero. Ale bardziej intuicyjne podejście do zastępowania wszystkich elementów w menu kontekstowym do tworzenia nowego <xref:System.Windows.Controls.ContextMenu>, należy umieścić w nim elementy, a następnie ustaw <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> właściwości formantu, który ma być nowym <xref:System.Windows.Controls.ContextMenu>.  
  
 Poniżej przedstawiono kod obsługi proste do zastępowania <xref:System.Windows.Controls.ContextMenu>. Kod odwołuje się do niestandardowego `BuildMenu` metody, która jest oddzielona się, ponieważ jest ona wywoływana więcej niż jeden z elementów obsługi przykład.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 Jednak jeśli używasz tego stylu Obsługa <xref:System.Windows.FrameworkElement.ContextMenuOpening>, potencjalnie może narazić błąd synchronizacji, jeśli obiekt, w której przeprowadzasz <xref:System.Windows.Controls.ContextMenu> nie ma istniejących menu kontekstowego. Gdy użytkownik kliknie prawym przyciskiem myszy formant, <xref:System.Windows.FrameworkElement.ContextMenuOpening> jest zgłaszany nawet wtedy, gdy istniejące <xref:System.Windows.Controls.ContextMenu> jest pusty lub ma wartość null. W tym przypadku niezależnie od nowych <xref:System.Windows.Controls.ContextMenu> ustawiony na "source" element za późno dociera do wyświetlenia. Ponadto jeśli użytkownik stanie się kliknij prawym przyciskiem myszy po raz drugi, tym razem nowej <xref:System.Windows.Controls.ContextMenu> pojawi się wartość zerowa i programu obsługi Zastąp prawidłowo i wyświetlić menu, gdy program obsługi jest uruchamiany po raz drugi. Sugeruje to dwa możliwe obejścia:  
  
1. Upewnij się, że <xref:System.Windows.FrameworkElement.ContextMenuOpening> obsługi zawsze uruchamiać formantów, które mają co najmniej jeden symbol zastępczy <xref:System.Windows.Controls.ContextMenu> dostępne, które mają zostać zastąpione przez kod procedury obsługi. W takim przypadku można nadal używać programu obsługi w poprzednim przykładzie, ale zazwyczaj chcesz przypisać symbol zastępczy <xref:System.Windows.Controls.ContextMenu> w początkowej znaczników:  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2. Przyjęto założenie, że początkowy <xref:System.Windows.Controls.ContextMenu> może mieć wartości null, oparte na logikę wstępnego. Można wykonać następujące akcje zaznacz <xref:System.Windows.Controls.ContextMenu> o wartości null lub Użyj flagi w kodzie, aby sprawdzić, czy programu obsługi zostało uruchomione co najmniej raz. Ponieważ założył, że <xref:System.Windows.Controls.ContextMenu> dotyczy, aby można wyświetlić programu obsługi, a następnie ustawia <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true` danych zdarzenia. Aby <xref:System.Windows.Controls.ContextMenuService> jest odpowiedzialny za wyświetlanie menu kontekstowego, `true` wartość <xref:System.Windows.RoutedEventArgs.Handled%2A> w zdarzeniu dane reprezentują żądanie, aby anulować wyświetlanie menu kontekstowe / kontrolować kombinację, który spowodował zdarzenie.  
  
 Teraz, gdy zostały pominięte menu kontekstowe potencjalnie podejrzane, następnym krokiem jest podać nową nazwę, a następnie wyświetla je. Ustawienie nowego jeden jest zasadniczo taki sam jak poprzedniej procedury obsługi: możesz tworzyć nowe <xref:System.Windows.Controls.ContextMenu> i ustaw źródło kontroli <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> właściwości z nią. Dodatkowy krok jest, możesz teraz wymusić wyświetlanie menu kontekstowego, ponieważ pominięte przy pierwszej próbie. Aby wymusić wyświetlania, należy ustawić <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType> właściwości `true` w ramach programu obsługi. Uważaj, gdy to zrobisz, ponieważ otwarcie menu kontekstowego w procedurze obsługi zgłasza <xref:System.Windows.FrameworkElement.ContextMenuOpening> ponownie zdarzenia. Należy ponownie wprowadzić programu obsługi, staje się nieskończenie cykliczne. Dlatego należy zawsze sprawdzić `null` albo użyj flagi, otwórz menu kontekstowe z poziomu <xref:System.Windows.FrameworkElement.ContextMenuOpening> programu obsługi zdarzeń.  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>Pomijanie dowolnego istniejącego Menu kontekstowego i wyświetlanie nie Menu kontekstowe  
 Końcowe scenariusz, pisanie programu obsługi, które pomijają menu całkowicie, jest mało prawdopodobna. Jeśli danego formantu nie powinien wyświetlić menu kontekstowe, są prawdopodobnie bardziej odpowiednie sposoby zapewnienia to niż przez tylko wtedy, gdy użytkownik zażąda go z pominięciem menu. Ale jeśli chcesz użyć programu obsługi do pominięcia menu kontekstowe i Pokaż nothing, a następnie programu obsługi należy po prostu ustaw <xref:System.Windows.RoutedEventArgs.Handled%2A> do `true` danych zdarzenia. <xref:System.Windows.Controls.ContextMenuService> , Odpowiada za wyświetlanie menu kontekstowego będzie sprawdzać dane zdarzenia, które zdarzenia pojawiającego się na formancie. Jeśli zdarzenie zostało oznaczone <xref:System.Windows.RoutedEventArgs.Handled%2A> gdziekolwiek wzdłuż trasy, następnie akcji Otwórz menu kontekstowe, który zainicjował zdarzenie jest pomijane.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>
- [Przegląd elementów podstawowych](base-elements-overview.md)
- [ContextMenu — przegląd](../controls/contextmenu-overview.md)
