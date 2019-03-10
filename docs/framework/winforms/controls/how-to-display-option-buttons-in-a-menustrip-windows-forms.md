---
title: 'Instrukcje: Wyświetlanie przycisków opcji w formancie MenuStrip (formularze Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: c64dd88915fdd17deee415b4d6c3fd088fbcfbfd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718873"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Instrukcje: Wyświetlanie przycisków opcji w formancie MenuStrip (formularze Windows)
Przyciski opcji, znany także jako przyciski radiowe są podobne do pola wyboru, z tą różnicą, że użytkownicy mogą wybrać tylko jedną na raz. Mimo że domyślnie <xref:System.Windows.Forms.ToolStripMenuItem> klasa nie zapewnia zachowanie przycisku opcji, klasa zapewnia zachowanie pola wyboru, które można dostosować, aby zaimplementować zachowanie przycisku opcji elementów menu w <xref:System.Windows.Forms.MenuStrip> kontroli.  
  
 Gdy <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość elementu menu jest `true`, użytkownicy będą mogli kliknąć element, aby przełączać wyświetlanie znacznik wyboru. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Właściwość wskazuje bieżący stan elementu. Aby zaimplementować zachowanie podstawowe przycisk opcji, należy upewnić się, jeśli element jest wybrany, można skonfigurować ustawienie <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość poprzednio wybranego elementu do `false`.  
  
 W poniższych procedurach opisano sposób implementacji i skorzystać z dodatkowych funkcji w klasie, która dziedziczy <xref:System.Windows.Forms.ToolStripMenuItem> klasy. `ToolStripRadioButtonMenuItem` Klasa zastępuje elementy członkowskie <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> i <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> zachowanie podczas zaznaczania i wygląd przycisków opcji. Ponadto ta klasa zastępuje <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości, które opcje w podmenu są wyłączone, chyba że zaznaczono element nadrzędny.  
  
### <a name="to-implement-option-button-selection-behavior"></a>Aby zaimplementować zachowanie podczas zaznaczania przycisku opcji  
  
1.  Inicjowanie <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość `true` umożliwiające wybór elementu.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metodę, aby wyczyścić zaznaczenie poprzednio wybranego elementu, gdy nowy element jest wybrany.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metodę, aby upewnić się, że kliknięcie pozycji elementu, który został już wybrany nie spowoduje wyczyszczenie zaznaczenia.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a>Aby zmienić wygląd elementów przycisku opcji  
  
1.  Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metodę, aby zastąpić za pomocą przycisku opcji znacznik wyboru domyślnego <xref:System.Windows.Forms.RadioButtonRenderer> klasy.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, i <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> metod w celu śledzenia stanu myszy oraz upewnij się, że <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metoda maluje stan prawidłowy przycisku opcji.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Aby wyłączyć opcje w podmenu, gdy element nadrzędny nie jest zaznaczone.  
  
1.  Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość tak, aby element jest wyłączony, gdy ma ona nadrzędnego elementu zarówno <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> wartość `true` i <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> wartość `false`.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metodę, aby subskrybować <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> zdarzenia nadrzędnego elementu.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  W obsłudze dla elementu nadrzędnego <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> zdarzenia Unieważnij element, aby zaktualizować wyświetlane dane z nowy stan włączony.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu przedstawiono pełną `ToolStripRadioButtonMenuItem` klasy, a <xref:System.Windows.Forms.Form> klasy i `Program` klasę wykazać zachowanie przycisku opcji.  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
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
