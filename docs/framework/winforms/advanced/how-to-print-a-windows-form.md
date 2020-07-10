---
title: 'Porady: drukowanie formularza systemu Windows'
description: Dowiedz się, jak programowo wydrukować kopię bieżącego formularza systemu Windows przy użyciu metody CopyFromScreen.
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
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174695"
---
# <a name="how-to-print-a-windows-form"></a>Porady: drukowanie formularza systemu Windows
W ramach procesu tworzenia zwykle warto wydrukować kopię formularza systemu Windows. Poniższy przykład kodu pokazuje, jak wydrukować kopię bieżącego formularza przy użyciu <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nie masz uprawnień dostępu do drukarki.  
  
- Nie ma zainstalowanej drukarki.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby można było uruchomić ten przykład kodu, musisz mieć uprawnienia dostępu do drukarki używanej na komputerze.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Drawing.Printing.PrintDocument>
- [Instrukcje: renderowanie obrazów za pomocą GDI+](how-to-render-images-with-gdi.md)
- [Instrukcje: drukowanie grafiki w formularzach Windows Forms](how-to-print-graphics-in-windows-forms.md)
