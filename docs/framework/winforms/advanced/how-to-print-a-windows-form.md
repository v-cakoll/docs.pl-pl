---
title: 'Instrukcje: Drukowanie formularza systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: 68dbad807e79f16bdc3cbdd3f55c62c3d6c854e9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621307"
---
# <a name="how-to-print-a-windows-form"></a>Instrukcje: Drukowanie formularza systemu Windows
Jako część procesu projektowania zazwyczaj można wydrukować formularza Windows. Poniższy przykład kodu pokazuje jak drukować kopię bieżącego formularza za pomocą <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Jest to przykład kompletny kod, który zawiera `Main` metody.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nie masz uprawnień dostępu do drukarki.  
  
- Brak Brak zainstalowanej drukarki.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby można było uruchomić ten przykład kodu, musi mieć uprawnienia dostępu do drukarki, używanej do komputera.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Printing.PrintDocument>
- [Instrukcje: Renderowanie obrazów za pomocą GDI +](how-to-render-images-with-gdi.md)
- [Instrukcje: Drukowanie grafiki w formularzach Windows Forms](how-to-print-graphics-in-windows-forms.md)
