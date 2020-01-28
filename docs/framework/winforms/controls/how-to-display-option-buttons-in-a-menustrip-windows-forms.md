---
title: 'Porady: wyświetlanie przycisków opcji w formancie MenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735526"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Porady: wyświetlanie przycisków opcji w formancie MenuStrip (Formularze systemu Windows)

Przyciski opcji, znane także jako przyciski radiowe, są podobne do pól wyboru, z wyjątkiem tego, że użytkownicy mogą wybrać tylko jedną naraz. Chociaż domyślnie Klasa <xref:System.Windows.Forms.ToolStripMenuItem> nie zapewnia zachowania przycisku opcji, klasa zapewnia zachowanie w przypadku pola wyboru, które można dostosować, aby zaimplementować zachowanie przycisku opcji dla elementów menu w kontrolce <xref:System.Windows.Forms.MenuStrip>.

Gdy właściwość <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> elementu menu jest `true`, użytkownicy mogą kliknąć element, aby włączyć wyświetlanie znacznika wyboru. Właściwość <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> wskazuje bieżący stan elementu. Aby zaimplementować podstawowe zachowanie przycisku opcji, należy się upewnić, że po wybraniu elementu właściwość <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> dla poprzednio wybranego elementu ma być `false`.

W poniższych procedurach opisano sposób implementacji tej i dodatkowych funkcji w klasie, która dziedziczy klasę <xref:System.Windows.Forms.ToolStripMenuItem>. Klasa `ToolStripRadioButtonMenuItem` przesłania składowe, takie jak <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> i <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>, aby zapewnić zachowanie wyboru i wygląd przycisków opcji. Ponadto ta klasa przesłania Właściwość <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>, dzięki czemu opcje w podmenu są wyłączone, chyba że jest zaznaczony element nadrzędny.

## <a name="to-implement-option-button-selection-behavior"></a>Aby zaimplementować zachowanie wyboru przycisku opcji

1. Zainicjuj Właściwość <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>, aby `true` w celu włączenia wyboru elementu.

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. Zastąp metodę <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>, aby wyczyścić zaznaczenie poprzednio wybranego elementu po zaznaczeniu nowego elementu.

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. Zastąp metodę <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>, aby upewnić się, że kliknięcie elementu, który został już wybrany, nie spowoduje usunięcia zaznaczenia.

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a>Aby zmodyfikować wygląd elementów przycisku opcji

1. Zastąp metodę <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>, aby zastąpić domyślny znacznik wyboru z przyciskiem opcji za pomocą klasy <xref:System.Windows.Forms.RadioButtonRenderer>.

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. Przesłoń metody <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>i <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A>, aby śledzić stan myszy i upewnić się, że metoda <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> maluje poprawny stan przycisku opcji.

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Aby wyłączyć opcje w podmenu, gdy element nadrzędny nie jest zaznaczony

1. Zastąp Właściwość <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> tak, aby element był wyłączony, gdy ma element nadrzędny z <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> wartością `true` i <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> wartość `false`.

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. Zastąp metodę <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>, aby subskrybować zdarzenie <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> elementu nadrzędnego.

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. W obsłudze zdarzenia <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> elementu nadrzędnego należy unieważnić element w celu zaktualizowania wyświetlania z nowym włączonym stanem.

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a>Przykład

Poniższy przykład kodu zawiera kompletną klasę `ToolStripRadioButtonMenuItem`, a Klasa <xref:System.Windows.Forms.Form> i Klasa `Program` do zademonstrowania zachowania przycisku opcji.

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
- [Instrukcje: implementowanie niestandardowego elementu ToolStripRenderer](how-to-implement-a-custom-toolstriprenderer.md)
