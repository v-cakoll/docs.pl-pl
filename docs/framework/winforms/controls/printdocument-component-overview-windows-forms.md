---
title: PrintDocument — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: b02133321624d27b9c1e8faae9cac1b4fe8f76c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows [PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) składnika jest używane do definiowania właściwości, które opisują wydruku i możliwość drukowania dokumentów w aplikacjach opartych na systemie Windows. Mogą być używane w połączeniu z [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) składnik, aby mieć możliwość kontrolowania wszystkich aspektów drukowanie dokumentów.  
  
## <a name="working-with-the-printdocument-component"></a>Praca z PrintDocument — składnik  
 Dwa główne scenariusze, które obejmują <xref:System.Drawing.Printing.PrintDocument> składnika są:  
  
-   Proste zadania drukowania, takie jak drukowania pliku tekstowego indywidualnych. W takim przypadku należy dodać <xref:System.Drawing.Printing.PrintDocument> składnik do formularza systemu Windows, następnie dodanie logiki programowania, która wyświetla plik w <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzeń. Logika programowania powinien kulminacyjny z <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodę, aby wydrukować dokument. Ta metoda wysyła <xref:System.Drawing.Graphics> obiektów zawartych w <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy do drukarki. Przykład pokazujący sposób drukowanie dokumentu tekstu przy użyciu <xref:System.Drawing.Printing.PrintDocument> składników, zobacz [porady: drukowanie wielu stron pliku tekstowego w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).  
  
-   Bardziej złożone zadania drukowania, takie jak sytuacji, w którym można ponowne wykorzystanie logiki drukowania, które zostały zapisane. W takim przypadku może pochodzić z nowego składnika <xref:System.Drawing.Printing.PrintDocument> składnika i zastąpienie (zobacz [zastępuje](~/docs/visual-basic/language-reference/modifiers/overrides.md) w języku Visual Basic lub [zastąpienia](~/docs/csharp/language-reference/keywords/override.md) dla C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.  
  
 Gdy jest ona dodawana do formularza, <xref:System.Drawing.Printing.PrintDocument> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Obsługa drukowania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [PrintDocument, składnik](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
