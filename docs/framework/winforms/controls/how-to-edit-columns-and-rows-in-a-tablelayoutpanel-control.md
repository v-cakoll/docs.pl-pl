---
title: 'Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 99ff3286592da0a097835b8f35d687475ca54fb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040295"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Instrukcje: edytowanie rzędów i kolumn w kontrolce TableLayoutPanel

Aby edytować wiersze i kolumny kontrolek, <xref:System.Windows.Forms.TableLayoutPanel> można użyć edytora kolekcji, zwanego oknem dialogowym **kolumny i style wierszy** .

> [!NOTE]
> Jeśli chcesz, aby kontrolka obejmowała wiele wierszy lub kolumn, ustaw `RowSpan` właściwości `ColumnSpan` i dla kontrolki. Aby uzyskać więcej informacji, [zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)użyciu TableLayoutPanel.
>
> Jeśli chcesz wyrównać formant w komórce lub chcesz, aby formant rozciągał się w komórce, użyj <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki. Aby uzyskać więcej informacji, [zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)użyciu TableLayoutPanel.

## <a name="to-edit-rows-and-columns"></a>Aby edytować wiersze i kolumny

1. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel>

2. ![](./media/vs-winformsmttagglyph.gif "") <xref:System.Windows.Forms.TableLayoutPanel> Kliknij symbol tagu inteligentnego kontrolki (inteligentny symbol znacznika VS_WinFormSmtTagGlyph) i wybierz opcję Edytuj wiersze i kolumny, aby otworzyć okno dialogowe **Style kolumn i wierszy** . Możesz również kliknąć prawym przyciskiem <xref:System.Windows.Forms.TableLayoutPanel> myszy formant i wybrać polecenie **Edytuj wiersze i kolumny** z menu skrótów.

3. Aby dodać lub usunąć kolumny, wybierz pozycję **kolumny** w polu listy rozwijanej **Typ elementu członkowskiego** .

4. Aby dodać lub usunąć wiersze, zaznacz opcję **wiersze** w polu listy rozwijanej **Typ elementu członkowskiego** .

5. Kliknij przycisk **Dodaj** , aby dodać wiersz lub kolumnę do końca listy **elementów członkowskich** .

6. Kliknij przycisk **Wstaw** , aby dodać wiersz lub kolumnę przed aktualnie wybranym elementem na liście.

7. Jeśli dodajesz wiersz lub kolumnę, wybierz **Typ rozmiaru** dla nowego wiersza lub kolumny. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SizeType>.

8. Aby usunąć wiersz lub kolumnę, kliknij przycisk **Usuń** , aby usunąć aktualnie wybrany element z listy **elementów członkowskich** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel, kontrolka](tablelayoutpanel-control-windows-forms.md)
