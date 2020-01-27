---
title: Wyłączanie przycisków w kolumnie przycisków w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 691781a43005d66e13029ab8110eb7f9daacc35f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745951"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Porady: wyłączanie przycisków w kolumnie przycisków w formancie DataGridView formularzy systemu Windows
Formant <xref:System.Windows.Forms.DataGridView> zawiera klasę <xref:System.Windows.Forms.DataGridViewButtonCell> do wyświetlania komórek z interfejsem użytkownika (UI), takim jak przycisk. Jednak <xref:System.Windows.Forms.DataGridViewButtonCell> nie zapewnia sposobu wyłączania wyglądu przycisku wyświetlanego w komórce.  
  
 Poniższy przykład kodu demonstruje sposób dostosowywania klasy <xref:System.Windows.Forms.DataGridViewButtonCell> do wyświetlania przycisków, które mogą być wyłączane. W przykładzie zdefiniowano nowy typ komórki, `DataGridViewDisableButtonCell`, który pochodzi z <xref:System.Windows.Forms.DataGridViewButtonCell>. Ten typ komórki udostępnia nową właściwość `Enabled`, która może być ustawiona na `false` do rysowania wyłączonego przycisku w komórce. W przykładzie zdefiniowano również nowy typ kolumny, `DataGridViewDisableButtonColumn`, która wyświetla `DataGridViewDisableButtonCell` obiekty. Aby pokazać tę nową komórkę i typ kolumny, bieżąca wartość każdego <xref:System.Windows.Forms.DataGridViewCheckBoxCell> w <xref:System.Windows.Forms.DataGridView> nadrzędnym określa, czy właściwość `Enabled` `DataGridViewDisableButtonCell` w tym samym wierszu jest `true`, czy `false`.  
  
> [!NOTE]
> Gdy dziedziczysz z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodasz nowe właściwości do klasy pochodnej, pamiętaj, aby zastąpić metodę `Clone`, aby skopiować nowe właściwości podczas klonowania operacji. Należy również wywołać metodę `Clone` klasy bazowej, aby właściwości klasy bazowej były kopiowane do nowej komórki lub kolumny.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing, system. Windows. Forms i system. Windows. Forms. VisualStyles.  
  
## <a name="see-also"></a>Zobacz także

- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
