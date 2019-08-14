---
title: 'Instrukcje: Wyświetlanie przycisków opcji w elemencie MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 94d683369edd6583ad8b01c2ce3f393567a5ed75
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971928"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Instrukcje: Wyświetlanie przycisków opcji w elemencie MenuStrip (Windows Forms)

Przyciski opcji, znane także jako przyciski radiowe, są podobne do pól wyboru, z wyjątkiem tego, że użytkownicy mogą wybrać tylko jedną naraz. Mimo że domyślnie <xref:System.Windows.Forms.ToolStripMenuItem> Klasa nie zapewnia zachowania przycisku opcji, klasa zapewnia zachowanie w przypadku pola wyboru, które można dostosować, aby zaimplementować zachowanie przycisku opcji dla elementów menu <xref:System.Windows.Forms.MenuStrip> w kontrolce.

Gdy właściwość elementu menu jest `true`, użytkownicy mogą kliknąć element, aby włączyć wyświetlanie znacznika wyboru. <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Właściwość wskazuje bieżący stan elementu. Aby zaimplementować podstawowe zachowanie przycisku opcji, należy się upewnić, że po wybraniu elementu <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość dla poprzednio wybranego elementu zostanie ustawiona na `false`wartość.

Poniższe procedury opisują sposób wdrażania tej i dodatkowych funkcji w klasie, która dziedziczy <xref:System.Windows.Forms.ToolStripMenuItem> klasę. Klasa przesłania składowe, takie <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> jak <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> i, aby zapewnić zachowanie wyboru i wygląd przycisków opcji. `ToolStripRadioButtonMenuItem` Ponadto ta klasa przesłania <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość, dzięki czemu opcje w podmenu są wyłączone, chyba że element nadrzędny jest zaznaczony.

## <a name="to-implement-option-button-selection-behavior"></a>Aby zaimplementować zachowanie wyboru przycisku opcji

1. `true` Zainicjuj <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość, aby włączyć wybór elementu.

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metodę, aby wyczyścić zaznaczenie poprzednio wybranego elementu po zaznaczeniu nowego elementu.

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metodę, aby upewnić się, że kliknięcie elementu, który został już wybrany, nie spowoduje usunięcia zaznaczenia.

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>Aby zmodyfikować wygląd elementów przycisku opcji

1. Zastąp <xref:System.Windows.Forms.RadioButtonRenderer> metodę, aby zastąpić domyślny znacznik wyboru z przyciskiem opcji za pomocą klasy. <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A> Zastąp<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>metody ,,<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> i ,<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> aby śledzić stan myszy i upewnij się, że metoda maluje poprawny stan przycisku opcji. <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Aby wyłączyć opcje w podmenu, gdy element nadrzędny nie jest zaznaczony

1. `false` <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> `true` <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> Zastąp Właściwośćtak,abyelementbyłwyłączony,gdymaelementnadrzędnyzjednocześniewartościąiwartością.<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metodę, aby subskrybować zdarzenie elementu nadrzędnego.

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. W programie obsługi zdarzenia elementu <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> nadrzędnego Unieważnij element w celu zaktualizowania wyświetlania przy użyciu nowego włączonego stanu.

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>Przykład

Poniższy przykład kodu zawiera kompletną `ToolStripRadioButtonMenuItem` klasę <xref:System.Windows.Forms.Form> oraz klasę i `Program` klasę, aby pokazać zachowanie przycisku opcji.

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [MenuStrip, kontrolka](menustrip-control-windows-forms.md)
- [Instrukcje: Implementowanie niestandardowego elementu ToolStripRenderer](how-to-implement-a-custom-toolstriprenderer.md)
