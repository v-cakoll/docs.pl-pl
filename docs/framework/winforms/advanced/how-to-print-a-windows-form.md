---
title: 'Porady: drukowanie formularza systemu Windows'
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
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c50b1f47d207334160ed12674ee8efb1390fb84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-a-windows-form"></a>Porady: drukowanie formularza systemu Windows
W ramach procesu tworzenia zwykle można wydrukować kopię formularza systemu Windows. Poniższy przykładowy kod przedstawia sposób wydrukować kopię bieżącego formularza za pomocą <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 To jest przykład kompletny kod, który zawiera `Main` metody.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nie masz uprawnień dostępu do drukarki.  
  
-   Nie została zainstalowana drukarka.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby można było uruchomić ten przykład kodu, musi mieć uprawnienia dostępu do drukarki, używanej do komputera.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Instrukcje: renderowanie obrazów za pomocą GDI+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [Instrukcje: drukowanie grafiki w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
