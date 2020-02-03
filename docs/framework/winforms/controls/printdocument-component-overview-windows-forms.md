---
title: PrintDocument — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728541"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument — Informacje o składniku (Formularze systemu Windows)

Windows Forms składnik [PrintDocument](printdocument-component-windows-forms.md) służy do ustawiania właściwości, które opisują, co należy wydrukować, oraz możliwość drukowania dokumentu w aplikacjach opartych na systemie Windows. Może być używany w połączeniu ze składnikiem [PrintDialog](printdialog-component-windows-forms.md) , aby mieć kontrolę nad wszystkimi aspektami drukowania dokumentów.

## <a name="working-with-the-printdocument-component"></a>Praca ze składnikiem PrintDocument

Dwa główne scenariusze obejmujące składnik <xref:System.Drawing.Printing.PrintDocument> są następujące:

- Proste zadania drukowania, takie jak drukowanie pojedynczego pliku tekstowego. W takim przypadku należy dodać składnik <xref:System.Drawing.Printing.PrintDocument> do formularza systemu Windows, a następnie dodać logikę programowania, która drukuje plik w programie obsługi zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage>. Logika programowania powinna skutkują z metodą <xref:System.Drawing.Printing.PrintDocument.Print%2A>, aby wydrukować dokument. Ta metoda wysyła <xref:System.Drawing.Graphics> obiektu znajdującego się we właściwości <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> klasy <xref:System.Drawing.Printing.PrintPageEventArgs> do drukarki. Przykład pokazujący sposób drukowania dokumentu tekstowego przy użyciu składnika <xref:System.Drawing.Printing.PrintDocument>, zobacz [How to: Print a wielostronicowy plik tekstowy w Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).

- Bardziej złożone zadania drukowania, takie jak sytuacja, w której chcesz ponownie użyć zapisaną logikę drukowania. W takim przypadku należy utworzyć nowy składnik ze składnika <xref:System.Drawing.Printing.PrintDocument> i przesłonić (zobacz [zastąpienia](../../../visual-basic/language-reference/modifiers/overrides.md) dla Visual Basic lub [przesłonięcia](../../../csharp/language-reference/keywords/override.md) dla C#) zdarzenia <xref:System.Drawing.Printing.PrintDocument.PrintPage>.

Po dodaniu do formularza składnik <xref:System.Drawing.Printing.PrintDocument> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Obsługa drukowania w formularzach Windows Forms](../advanced/windows-forms-print-support.md)
- [PrintDocument, składnik](printdocument-component-windows-forms.md)
