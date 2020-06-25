---
title: 'Porady: wyświetlanie godziny za pomocą formantu DateTimePicker'
description: Dowiedz się, jak używać formantu DateTimePicker Windows Forms, aby umożliwić użytkownikom wybranie daty i godziny oraz wyświetlanie daty i godziny w określonym formacie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: ab584367a189d05e567bb57d386c6bf629201102
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325584"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a>Porady: wyświetlanie godziny za pomocą formantu DateTimePicker
Jeśli chcesz, aby aplikacja umożliwiała użytkownikom wybranie daty i godziny oraz wyświetlenie daty i godziny w określonym formacie, użyj <xref:System.Windows.Forms.DateTimePicker> kontrolki. Poniższa procedura pokazuje, jak używać <xref:System.Windows.Forms.DateTimePicker> kontrolki do wyświetlania czasu.  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a>Aby wyświetlić czas z kontrolką DateTimePicker  
  
1. Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> Właściwość na<xref:System.Windows.Forms.DateTimePickerFormat.Time>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. Ustaw <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> Właściwość na <xref:System.Windows.Forms.DateTimePicker> `true` .  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć element <xref:System.Windows.Forms.DateTimePicker> , który umożliwia użytkownikom wybranie tylko czasu.  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz też

- [DateTimePicker, kontrolka](datetimepicker-control-windows-forms.md)
