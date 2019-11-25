---
title: Jak powiązać właściwości dwóch formantów
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: d38c473b8c4d3f71f1e3decd4f66be248665c57b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974816"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Jak powiązać właściwości dwóch formantów

Ten przykład pokazuje, jak powiązać Właściwość jednego wystąpienia kontrolki z inną przy użyciu właściwości <xref:System.Windows.Data.Binding.ElementName%2A>.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak powiązać Właściwość <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Canvas> z właściwością [SelectedItem. Content](xref:System.Windows.Controls.ContentControl.Content%2A) <xref:System.Windows.Controls.ComboBox>:

[!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]

Gdy ten przykład jest renderowany, wygląda następująco:

![Zrzut ekranu przedstawiający pole kombi z wybraną wartością zielony i zieloną kwadratową.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> Właściwość Target powiązania (w tym przykładzie właściwość <xref:System.Windows.Controls.Panel.Background%2A>) musi być właściwością zależności. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).

## <a name="see-also"></a>Zobacz także

- [Określanie obiektu źródłowego powiązania](how-to-specify-the-binding-source.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
