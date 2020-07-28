---
title: Jak wykryć kiedy tekst w TextBox uległ zmianie
description: Dowiedz się, jak używać zdarzenia textchanging do uruchamiania metody za każdym razem, gdy tekst w kontrolce TextBox zmieni się w aplikacji Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166231"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Jak wykryć kiedy tekst w TextBox uległ zmianie

Ten przykład pokazuje jeden ze sposobów, aby użyć <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenia do wykonania metody przy każdej zmianie tekstu w <xref:System.Windows.Controls.TextBox> kontrolce.

W klasie związanej z kodem dla programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , która zawiera <xref:System.Windows.Controls.TextBox> kontrolkę, która ma być monitorowana pod kątem zmian, Wstaw metodę do wywołania za każdym razem, gdy zdarzenie zostanie wyzwolone <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> .  Ta metoda musi mieć sygnaturę zgodną z oczekiwaną przez <xref:System.Windows.Controls.TextChangedEventHandler> delegata.

Procedura obsługi zdarzeń jest wywoływana za każdym razem, gdy zawartość <xref:System.Windows.Controls.TextBox> kontrolki jest zmieniana przez użytkownika lub programowo.

> [!NOTE]
> To zdarzenie jest wyzwalane <xref:System.Windows.Controls.TextBox> , gdy kontrolka jest tworzona i początkowo wypełniana tekstem.

## <a name="example"></a>Przykład

W obszarze, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] który definiuje <xref:System.Windows.Controls.TextBox> kontrolkę, należy określić <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atrybut o wartości zgodnej z nazwą metody programu obsługi zdarzeń.

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>Przykład

W klasie związanej z kodem dla programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , która zawiera <xref:System.Windows.Controls.TextBox> kontrolkę, która ma być monitorowana pod kątem zmian, Wstaw metodę do wywołania za każdym razem, gdy zdarzenie zostanie wyzwolone <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> .  Ta metoda musi mieć sygnaturę zgodną z oczekiwaną przez <xref:System.Windows.Controls.TextChangedEventHandler> delegata.

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

Procedura obsługi zdarzeń jest wywoływana za każdym razem, gdy zawartość <xref:System.Windows.Controls.TextBox> kontrolki jest zmieniana przez użytkownika lub programowo.

> [!NOTE]
> To zdarzenie jest wyzwalane <xref:System.Windows.Controls.TextBox> , gdy kontrolka jest tworzona i początkowo wypełniana tekstem.

Komentarze

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox — Przegląd](textbox-overview.md)
- [RichTextBox — Przegląd](richtextbox-overview.md)
