---
title: 'Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 4473b20eea57088104a51eb1b6c080219223d214
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628647"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Porady: edytowanie rzędów i kolumn w formancie TableLayoutPanel

Aby edytować wiersze i kolumny kontrolek, można użyć edytora kolekcji w kontrolce <xref:System.Windows.Forms.TableLayoutPanel>, nazywanej **kolumną i stylem wierszy** .

> [!NOTE]
> Jeśli chcesz, aby kontrolka obejmowała wiele wierszy lub kolumn, ustaw `RowSpan` i `ColumnSpan` właściwości formantu. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).
>
> Jeśli chcesz wyrównać formant w komórce lub chcesz, aby formant rozciągał się w komórce, użyj właściwości <xref:System.Windows.Forms.Control.Anchor%2A> kontrolki. Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

## <a name="to-edit-rows-and-columns"></a>Aby edytować wiersze i kolumny

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz.

2. Kliknij symbol akcji projektanta <xref:System.Windows.Forms.TableLayoutPanel> kontrolki (![małą czarną strzałkę](./media/designer-actions-glyph.gif)) i wybierz opcję **Edytuj wiersze i kolumny** , aby otworzyć okno dialogowe **Style kolumn i wierszy** . Możesz również kliknąć prawym przyciskiem myszy formant <xref:System.Windows.Forms.TableLayoutPanel> i wybrać polecenie **Edytuj wiersze i kolumny** z menu skrótów.

3. Aby dodać lub usunąć kolumny, wybierz pozycję **kolumny** w polu listy rozwijanej **Typ elementu członkowskiego** .

4. Aby dodać lub usunąć wiersze, zaznacz opcję **wiersze** w polu listy rozwijanej **Typ elementu członkowskiego** .

5. Kliknij przycisk **Dodaj** , aby dodać wiersz lub kolumnę do końca listy **elementów członkowskich** .

6. Kliknij przycisk **Wstaw** , aby dodać wiersz lub kolumnę przed aktualnie wybranym elementem na liście.

7. Jeśli dodajesz wiersz lub kolumnę, wybierz **Typ rozmiaru** dla nowego wiersza lub kolumny. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SizeType>.

8. Aby usunąć wiersz lub kolumnę, kliknij przycisk **Usuń** , aby usunąć aktualnie wybrany element z listy **elementów członkowskich** .

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel, kontrolka](tablelayoutpanel-control-windows-forms.md)
