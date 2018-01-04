---
title: "Porady: wyświetlanie przycisków opcji w formancie MenuStrip (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0de3b8596bc06c79f391141ef85fec65ac343d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a>Porady: wyświetlanie przycisków opcji w formancie MenuStrip (Formularze systemu Windows)
Przyciski opcji, znanej także jako przyciski radiowe, są podobne do pola wyboru z wyjątkiem tego, czy użytkownicy mogą wybrać tylko jeden z nich. Mimo że domyślnie <xref:System.Windows.Forms.ToolStripMenuItem> klasa nie zapewnia zachowanie przycisk opcji, klasa zapewnia zachowanie pola wyboru, które można dostosować, aby zaimplementować zachowanie przycisk opcji dla elementów menu w <xref:System.Windows.Forms.MenuStrip> formantu.  
  
 Gdy <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość elementu menu jest `true`, użytkownicy mogą kliknąć element, aby przełączyć wyświetlanie znacznik wyboru. <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Właściwość wskazuje bieżący stan elementu. Aby zaimplementować podstawowe opcję zachowania, należy upewnić się, gdy element jest zaznaczony, ustawienie <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość poprzednio wybranego elementu do `false`.  
  
 W poniższych procedurach opisano, jak i dodatkowe funkcje w klasie, która dziedziczy <xref:System.Windows.Forms.ToolStripMenuItem> klasy. `ToolStripRadioButtonMenuItem` Klasa zastępuje elementy członkowskie <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> i <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> zaznaczenia działanie i wygląd przycisków opcji. Ponadto ta klasa zastępuje <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości, które opcje w podmenu są wyłączone, chyba że zaznaczono element nadrzędny.  
  
### <a name="to-implement-option-button-selection-behavior"></a>Aby zaimplementować przycisk opcji Zaznaczenie zachowanie  
  
1.  Inicjowanie <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwości `true` umożliwia wybór elementu.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metody, aby wyczyścić zaznaczenie poprzednio zaznaczony element w przypadku wybrania nowego elementu.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metody, aby upewnić się, klikając elementu, który został już wybrany nie spowoduje wyczyszczenie zaznaczenia.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a>Aby zmodyfikować wygląd elementów przycisk opcji  
  
1.  Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metodę, aby zastąpić znacznik wyboru domyślny przycisk opcji przy użyciu <xref:System.Windows.Forms.RadioButtonRenderer> klasy.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, i <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> metody do śledzenia stanu myszy i upewnij się, że <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metody rysują stanu poprawne przycisk opcji.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a>Wyłączenie opcji w podmenu, gdy element nadrzędny nie jest zaznaczona.  
  
1.  Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości, aby element jest wyłączony, gdy ma element nadrzędny zarówno <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> wartość `true` i <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> wartość `false`.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metody do subskrybowania <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> zdarzenia nadrzędnego elementu.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  W obsłudze dla elementu nadrzędnego <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> zdarzenia unieważnienie element, aby zaktualizować wyświetlane dane z nowy stan włączony.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu przedstawiono pełną `ToolStripRadioButtonMenuItem` klasy, a <xref:System.Windows.Forms.Form> klasy i `Program` klasy, aby zademonstrować zachowanie przycisk opcji.  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [MenuStrip, kontrolka](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [Instrukcje: implementowanie niestandardowego elementu ToolStripRenderer](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)
