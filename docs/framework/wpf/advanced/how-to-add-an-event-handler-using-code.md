---
title: Jak dodać obsługę zdarzeń z użyciem kodu
description: Użyj tego przykładu, aby dowiedzieć się, jak dodać program obsługi zdarzeń do elementu w Windows Presentation Foundation przy użyciu kodu, zamiast deklarowania go przy użyciu języka XAML.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: b36969f7a65ccbf6c9d03b22767d9eacdc177ad1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166368"
---
# <a name="how-to-add-an-event-handler-using-code"></a>Jak dodać obsługę zdarzeń z użyciem kodu
Ten przykład pokazuje, jak dodać program obsługi zdarzeń do elementu przy użyciu kodu.  
  
 Jeśli chcesz dodać program obsługi zdarzeń do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementu, a strona znaczników, która zawiera element, jest już załadowana, należy dodać procedurę obsługi przy użyciu kodu. Alternatywnie, jeśli tworzysz drzewo elementów dla aplikacji całkowicie przy użyciu kodu i nie deklaruje żadnych elementów przy użyciu, można [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wywołać konkretne metody, aby dodać obsługę zdarzeń do drzewa skonstruowane elementy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dodaje nową <xref:System.Windows.Controls.Button> do istniejącej strony, która jest początkowo zdefiniowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Plik związany z kodem implementuje metodę obsługi zdarzeń, a następnie dodaje tę metodę jako nowy program obsługi zdarzeń na <xref:System.Windows.Controls.Button> .  
  
 W przykładzie w języku C# `+=` za pomocą operatora można przypisać do zdarzenia procedurę obsługi. Jest to ten sam operator, który jest używany do przypisania procedury obsługi w modelu obsługi zdarzeń środowiska uruchomieniowego języka wspólnego (CLR). Firma Microsoft Visual Basic nie obsługuje tego operatora jako metody dodawania obsługi zdarzeń. Zamiast tego wymaga jednej z dwóch technik:  
  
- Użyj <xref:System.Windows.UIElement.AddHandler%2A> metody wraz z `AddressOf` operatorem, aby odwołać się do implementacji programu obsługi zdarzeń.  
  
- Użyj `Handles` słowa kluczowego jako części definicji programu obsługi zdarzeń. Ta technika nie jest tu pokazana. Zobacz [Visual Basic i obsługa zdarzeń WPF](visual-basic-and-wpf-event-handling.md).  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> Dodawanie programu obsługi zdarzeń na pierwszej przeanalizowanej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stronie jest znacznie prostsze. W elemencie obiektu, do którego chcesz dodać procedurę obsługi zdarzeń, Dodaj atrybut, który pasuje do nazwy zdarzenia, które chcesz obsłużyć. Następnie określ wartość tego atrybutu jako nazwę metody obsługi zdarzeń zdefiniowanej w pliku związanym z kodem na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stronie. Aby uzyskać więcej informacji, zobacz [Omówienie języka XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) lub [zdarzenia kierowane — Omówienie](routed-events-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
- [— Tematy porad](events-how-to-topics.md)
