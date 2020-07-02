---
title: 'Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel'
description: Dowiedz się, w jaki sposób używać okna dialogowego kolumny i stylów wierszy do edytowania wierszy i kolumn kontrolek Windows Forms.
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619354"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel

<xref:System.Windows.Forms.TableLayoutPanel>Aby edytować wiersze i kolumny kontrolek, można użyć edytora kolekcji, zwanego oknem dialogowym **kolumny i style wierszy** .

> [!NOTE]
> Jeśli chcesz, aby kontrolka obejmowała wiele wierszy lub kolumn, ustaw `RowSpan` `ColumnSpan` właściwości i dla kontrolki. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).
>
> Jeśli chcesz wyrównać formant w komórce lub chcesz, aby formant rozciągał się w komórce, użyj właściwości kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> . Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

## <a name="to-edit-rows-and-columns"></a>Aby edytować wiersze i kolumny

1. Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę z **przybornika** do formularza.

2. Kliknij <xref:System.Windows.Forms.TableLayoutPanel> symbol akcji projektanta kontrolki ( ![ Mała czarna strzałka ](./media/designer-actions-glyph.gif) ) i wybierz opcję **Edytuj wiersze i kolumny** , aby otworzyć okno dialogowe **Style kolumn i wierszy** . Możesz również kliknąć prawym przyciskiem myszy <xref:System.Windows.Forms.TableLayoutPanel> formant i wybrać polecenie **Edytuj wiersze i kolumny** z menu skrótów.

3. Aby dodać lub usunąć kolumny, wybierz pozycję **kolumny** w polu listy rozwijanej **Typ elementu członkowskiego** .

4. Aby dodać lub usunąć wiersze, zaznacz opcję **wiersze** w polu listy rozwijanej **Typ elementu członkowskiego** .

5. Kliknij przycisk **Dodaj** , aby dodać wiersz lub kolumnę do końca listy **elementów członkowskich** .

6. Kliknij przycisk **Wstaw** , aby dodać wiersz lub kolumnę przed aktualnie wybranym elementem na liście.

7. Jeśli dodajesz wiersz lub kolumnę, wybierz **Typ rozmiaru** dla nowego wiersza lub kolumny. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SizeType>.

8. Aby usunąć wiersz lub kolumnę, kliknij przycisk **Usuń** , aby usunąć aktualnie wybrany element z listy **elementów członkowskich** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel — formant](tablelayoutpanel-control-windows-forms.md)
