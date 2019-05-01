---
title: PrintDocument — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a3f08aa4bd5b63769cef35dbea2209d5d83261be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012623"
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument — Informacje o składniku (Formularze systemu Windows)
Formularze Windows [PrintDocument](printdocument-component-windows-forms.md) składnik jest używany do ustawiania właściwości, które opisują, jakie do drukowania i możliwość drukowania dokumentu w aplikacji systemu Windows. Mogą być używane w połączeniu z [PrintDialog](printdialog-component-windows-forms.md) składnik, aby mieć kontrolę nad wszystkimi aspektami drukowanie dokumentów.  
  
## <a name="working-with-the-printdocument-component"></a>Praca z PrintDocument — składnik  
 Dwa główne scenariusze, które obejmują <xref:System.Drawing.Printing.PrintDocument> składnik to:  
  
- Proste zadania drukowania, takich jak drukowanie plik tekstowy indywidualnych. W takim przypadku należy dodać <xref:System.Drawing.Printing.PrintDocument> składnika do formularza Windows, a następnie dodaj logikę programistyczną, które inicjuje drukowanie do pliku w <xref:System.Drawing.Printing.PrintDocument.PrintPage> programu obsługi zdarzeń. Logikę programistyczną powinien kulminacyjny z <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda spowoduje wydrukowanie dokumentu. Ta metoda wysyła <xref:System.Drawing.Graphics> zawartego w obiektu <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy do drukarki. Na przykład, który pokazuje, jak drukowanie dokumentu tekstowego przy użyciu <xref:System.Drawing.Printing.PrintDocument> składników, zobacz [jak: Podglądu wydruku w formularzach Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).  
  
- Bardziej złożone zadania drukowania, takich jak sytuacji, w których warto ponowne wykorzystanie logiki drukowania, które zostały napisane. W takim przypadku będzie pochodzić z nowym składnikiem <xref:System.Drawing.Printing.PrintDocument> składnika i zastąpienie (zobacz [zastępuje](~/docs/visual-basic/language-reference/modifiers/overrides.md) dla języka Visual Basic lub [zastąpienia](~/docs/csharp/language-reference/keywords/override.md) dla C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.  
  
 Gdy zostanie dodany do formularza, <xref:System.Drawing.Printing.PrintDocument> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Obsługa drukowania w formularzach Windows Forms](../advanced/windows-forms-print-support.md)
- [PrintDocument, składnik](printdocument-component-windows-forms.md)
