---
title: 'Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039701"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel
Kontrolki w <xref:System.Windows.Forms.TableLayoutPanel> kontrolce mogą obejmować sąsiadujące wiersze i kolumny.

## <a name="to-span-columns-and-rows"></a>Aby rozpiętie kolumn i wierszy

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel>

2. Przeciągnij kontrolkę z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> lewej górnej komórki formantu. <xref:System.Windows.Forms.Button>

3. Ustaw właściwość **ColumnSpan**kontrolki na 2 <xref:System.Windows.Forms.Button> . Należy zauważyć, <xref:System.Windows.Forms.Button> że formant obejmuje pierwszą i drugą kolumnę.

4. Ustaw właściwość **RowSpan**kontrolki na 2 <xref:System.Windows.Forms.Button> . Należy zauważyć, <xref:System.Windows.Forms.Button> że formant obejmuje pierwszy i drugi wiersz.

5. Ustaw właściwość **ColumnSpan**kontrolki na 1 <xref:System.Windows.Forms.Button> . Należy zauważyć, <xref:System.Windows.Forms.Button> że formant jest przenoszony do pierwszej kolumny i rozciąga się na pierwszy i drugi wiersz.

## <a name="see-also"></a>Zobacz także

- [TableLayoutPanel, kontrolka](tablelayoutpanel-control-windows-forms.md)
