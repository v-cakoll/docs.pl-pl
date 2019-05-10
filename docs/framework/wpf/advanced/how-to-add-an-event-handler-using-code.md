---
title: 'Instrukcje: Dodawanie obsługi zdarzeń z użyciem kodu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 32e3926bb4c519b7be14a26484603d6d4ea88b6a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665793"
---
# <a name="how-to-add-an-event-handler-using-code"></a>Instrukcje: Dodawanie obsługi zdarzeń z użyciem kodu
W tym przykładzie przedstawiono sposób dodawania programu obsługi zdarzeń do elementu przy użyciu kodu.  
  
 Jeśli chcesz dodać program obsługi zdarzeń do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementu, a na stronie znaczników, który zawiera element został już załadowany, należy dodać program obsługi przy użyciu kodu. Alternatywnie jeśli są tworzone w górę drzewa elementów, aplikacji całkowicie przy użyciu kodu i nie deklarując wszelkie elementy przy użyciu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], można wywołać konkretnych metod, aby dodać procedury obsługi zdarzeń do drzewa element skonstruowany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dodaje nowy <xref:System.Windows.Controls.Button> do istniejącej strony, który jest wstępnie zdefiniowany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Plik związany z kodem implementuje metodę programu obsługi zdarzeń i dodaje tę metodę jako nowy program obsługi zdarzeń na <xref:System.Windows.Controls.Button>.  
  
 C# Przykładzie użyto `+=` operatora, aby przypisać program obsługi zdarzenia. Jest to ten sam operator, który jest używany do przypisywania obsługi w [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] model obsługi zdarzeń. Microsoft Visual Basic nie obsługuje tego operatora jako środek Dodawanie obsługi zdarzeń. Zamiast tego wymaga jednej z dwóch technik:  
  
- Użyj <xref:System.Windows.UIElement.AddHandler%2A> metoda wraz z `AddressOf` operatora, aby odwoływać się do wdrożenia programu obsługi zdarzeń.  
  
- Użyj `Handles` — słowo kluczowe w definicji procedury obsługi zdarzeń. Ta technika nie jest wyświetlany w tym miejscu; zobacz [Visual Basic i obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  Dodawanie obsługi zdarzeń w początkowo przeanalizowany [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony jest znacznie prostsza. W elemencie obiektu, którym chcesz dodać program obsługi zdarzeń należy dodać atrybut, który jest zgodna z nazwą zdarzenia, które mają być obsługiwane. Następnie określ wartość tego atrybutu jako nazwę metody obsługi zdarzeń, które zdefiniowane w pliku związanym z kodem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strony. Aby uzyskać więcej informacji, zobacz [Przegląd XAML (WPF)](xaml-overview-wpf.md) lub [Przegląd zdarzeń kierowane](routed-events-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Tematy z instrukcjami](events-how-to-topics.md)
