---
title: PrintDocument — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928993"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument — Informacje o składniku (Formularze systemu Windows)

Windows Forms składnik [PrintDocument](printdocument-component-windows-forms.md) służy do ustawiania właściwości, które opisują, co należy wydrukować, oraz możliwość drukowania dokumentu w aplikacjach opartych na systemie Windows. Może być używany w połączeniu ze składnikiem [PrintDialog](printdialog-component-windows-forms.md) , aby mieć kontrolę nad wszystkimi aspektami drukowania dokumentów.

## <a name="working-with-the-printdocument-component"></a>Praca ze składnikiem PrintDocument

Dwa główne scenariusze obejmujące <xref:System.Drawing.Printing.PrintDocument> składnik to:

- Proste zadania drukowania, takie jak drukowanie pojedynczego pliku tekstowego. W takim przypadku należy dodać <xref:System.Drawing.Printing.PrintDocument> składnik do formularza systemu Windows, a następnie dodać logikę programowania, która drukuje plik <xref:System.Drawing.Printing.PrintDocument.PrintPage> w programie obsługi zdarzeń. Logika programowania powinna skutkują z <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodą drukowania dokumentu. Ta metoda wysyła <xref:System.Drawing.Graphics> obiekt znajdujący się <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> we właściwości <xref:System.Drawing.Printing.PrintPageEventArgs> klasy do drukarki. Przykład pokazujący sposób drukowania dokumentu tekstowego przy użyciu <xref:System.Drawing.Printing.PrintDocument> składnika można znaleźć w temacie [How to: Drukowanie wielostronicowego pliku tekstowego w Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).

- Bardziej złożone zadania drukowania, takie jak sytuacja, w której chcesz ponownie użyć zapisaną logikę drukowania. <xref:System.Drawing.Printing.PrintDocument> W takim przypadku należy utworzyć nowy składnik ze składnika i przesłonić (zobacz [zastąpienia](../../../visual-basic/language-reference/modifiers/overrides.md) dla Visual Basic lub przesłonięcia dla C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia. [](../../../csharp/language-reference/keywords/override.md)

Po dodaniu go do formularza <xref:System.Drawing.Printing.PrintDocument> składnik pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Obsługa drukowania w formularzach Windows Forms](../advanced/windows-forms-print-support.md)
- [PrintDocument, składnik](printdocument-component-windows-forms.md)
