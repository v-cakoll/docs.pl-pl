---
title: Jak utworzyć siatkę złożoną
description: Przykład o tym, jak można użyć formantu siatki, aby utworzyć układ, który wygląda jak kalendarza miesięcznego.
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: e2356113457e8c9a6737132e9779e49c05a23d77
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199984"
---
# <a name="how-to-create-a-complex-grid"></a>Jak utworzyć siatkę złożoną

W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.Grid> formantu, aby utworzyć układ, który wygląda jak kalendarza miesięcznego.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano osiem wierszy i kolumn osiem przy użyciu <xref:System.Windows.Controls.RowDefinition> i <xref:System.Windows.Controls.ColumnDefinition> klasy. Używa ona <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> dołączonych właściwości, wraz z <xref:System.Windows.Shapes.Rectangle> elementy, które wypełnienia tła różnych kolumn i wierszy. Ten projekt jest możliwe, ponieważ więcej niż jeden element może znajdować się w każdej komórki w <xref:System.Windows.Controls.Grid>, główna różnica między <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Documents.Table>.

W przykładzie użyto pionowy gradientów do <xref:System.Windows.Shapes.Shape.Fill%2A> kolumny i wiersze do poprawy wizualnej prezentacji i czytelności kalendarza. Różne <xref:System.Windows.Controls.TextBlock> elementy reprezentują dat i dni tygodnia. <xref:System.Windows.Controls.TextBlock> elementy są pozycjonowane absolutnie w komórkach ich za pomocą <xref:System.Windows.FrameworkElement.Margin%2A> właściwości i właściwości wyrównanie, które są zdefiniowane w stylu dla aplikacji.

[!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]

Na poniższej ilustracji przedstawiono wynikowy formant kalendarza można dostosowywać:

![Zrzut ekranu przedstawiający wynikowy formant](./media/how-to-create-a-complex-grid/wpf-manual-calendar.png)

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Grid?displayProperty=nameWithType>
- <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>
- [Malowanie jednolitymi kolorami i gradientami — przegląd](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Panele — omówienie](panels-overview.md)
- [Przegląd tabeli](../advanced/table-overview.md)