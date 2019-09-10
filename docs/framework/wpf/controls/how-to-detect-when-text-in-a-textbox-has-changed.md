---
title: 'Instrukcje: Wykrywanie momentu zmiany tekstu w kontrolce TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855624"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Instrukcje: Wykrywanie momentu zmiany tekstu w kontrolce TextBox

Ten przykład pokazuje jeden ze sposobów, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> aby użyć zdarzenia do wykonania metody przy każdej zmianie tekstu <xref:System.Windows.Controls.TextBox> w kontrolce.

W klasie związanej z kodem dla programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , która <xref:System.Windows.Controls.TextBox> zawiera kontrolkę, która ma być monitorowana pod kątem zmian, Wstaw <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> metodę do wywołania za każdym razem, gdy zdarzenie zostanie wyzwolone.  Ta metoda musi mieć sygnaturę zgodną z oczekiwaną przez <xref:System.Windows.Controls.TextChangedEventHandler> delegata.

Procedura obsługi zdarzeń jest wywoływana za każdym razem, gdy <xref:System.Windows.Controls.TextBox> zawartość kontrolki jest zmieniana przez użytkownika lub programowo.

> [!NOTE]
> To zdarzenie jest wyzwalane <xref:System.Windows.Controls.TextBox> , gdy kontrolka jest tworzona i początkowo wypełniana tekstem.

## <a name="example"></a>Przykład

W obszarze [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , który <xref:System.Windows.Controls.TextBox> definiuje kontrolkę, należy <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> określić atrybut o wartości zgodnej z nazwą metody programu obsługi zdarzeń.

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>Przykład

W klasie związanej z kodem dla programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , która <xref:System.Windows.Controls.TextBox> zawiera kontrolkę, która ma być monitorowana pod kątem zmian, Wstaw <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> metodę do wywołania za każdym razem, gdy zdarzenie zostanie wyzwolone.  Ta metoda musi mieć sygnaturę zgodną z oczekiwaną przez <xref:System.Windows.Controls.TextChangedEventHandler> delegata.

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

Procedura obsługi zdarzeń jest wywoływana za każdym razem, gdy <xref:System.Windows.Controls.TextBox> zawartość kontrolki jest zmieniana przez użytkownika lub programowo.

> [!NOTE]
> To zdarzenie jest wyzwalane <xref:System.Windows.Controls.TextBox> , gdy kontrolka jest tworzona i początkowo wypełniana tekstem.

Komentarze

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
