---
title: 'Instrukcje: wyłączanie przycisków w kolumnie przycisków w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: b8bb503186e41c682b0685e4c9c4bf0bb3adcbe8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967397"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Instrukcje: wyłączanie przycisków w kolumnie przycisków w kontrolce DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Formant<xref:System.Windows.Forms.DataGridViewButtonCell> zawiera klasę służącą do wyświetlania komórek z interfejsem użytkownika (UI), takim jak przycisk. Jednak program <xref:System.Windows.Forms.DataGridViewButtonCell> nie umożliwia wyłączenia wyglądu przycisku wyświetlanego w komórce.  
  
 Poniższy przykład kodu demonstruje sposób dostosowywania <xref:System.Windows.Forms.DataGridViewButtonCell> klasy do wyświetlania przycisków, które mogą być wyświetlane jako wyłączone. W przykładzie zdefiniowano nowy typ `DataGridViewDisableButtonCell`komórki, który pochodzi od. <xref:System.Windows.Forms.DataGridViewButtonCell> Ten typ komórki zawiera nową `Enabled` właściwość, którą można `false` ustawić, aby narysować przycisk wyłączony w komórce. W przykładzie zdefiniowano również nowy typ `DataGridViewDisableButtonColumn`kolumny, który wyświetla `DataGridViewDisableButtonCell` obiekty. Aby pokazać tę nową komórkę i typ kolumny, bieżąca <xref:System.Windows.Forms.DataGridViewCheckBoxCell> wartość każdego w obiekcie nadrzędnym <xref:System.Windows.Forms.DataGridView> określa, `DataGridViewDisableButtonCell` czy `Enabled` właściwość w tym samym wierszu jest `true` lub `false`.  
  
> [!NOTE]
> Gdy pochodzą z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodajesz nowe właściwości do klasy pochodnej, pamiętaj, aby zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas klonowania operacji. Należy również wywołać `Clone` metodę klasy bazowej, aby właściwości klasy bazowej były kopiowane do nowej komórki lub kolumny.  
  
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
