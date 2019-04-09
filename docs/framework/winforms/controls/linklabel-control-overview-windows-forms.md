---
title: LinkLabel — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 541467b0f1285d372e5f6d502d9d8f28c8c6333e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083130"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.LinkLabel> kontrolka zezwala na dodawanie łączy stylu sieci Web do aplikacji Windows Forms. Możesz użyć <xref:System.Windows.Forms.LinkLabel> kontrola wszystko, co umożliwia <xref:System.Windows.Forms.Label> kontrolki; można też określić część tekstu jako link do pliku, folderu lub strony sieci Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Co można zrobić za pomocą kontrolki LinkLabel  
 Oprócz wszystkich właściwości, metody i zdarzenia <xref:System.Windows.Forms.Label> kontroli <xref:System.Windows.Forms.LinkLabel> kontrolka ma właściwości kolory łączy i hiperłączy. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Właściwość ustawia obszar tekstowy, który uaktywnia łącze. <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, I <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> właściwości ustawione kolory łącza. <xref:System.Windows.Forms.LinkLabel.LinkClicked> Zdarzenia określa, co się stanie, gdy tekst łącza jest zaznaczony.  
  
 Najprostsze użycie <xref:System.Windows.Forms.LinkLabel> kontroli jest wyświetlane przy użyciu pojedynczego łącza <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości, ale można również wyświetlić wiele hiperłącza, za pomocą <xref:System.Windows.Forms.LinkLabel.Links%2A> właściwości. <xref:System.Windows.Forms.LinkLabel.Links%2A> Właściwość pozwala na dostęp do kolekcji łączy. Można również określić, że dane w <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> właściwości poszczególnych osób <xref:System.Windows.Forms.LinkLabel.Link> obiektu. Wartość <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> właściwości mogą być używane do przechowywania lokalizację pliku do wyświetlenia lub adres witryny sieci Web.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.LinkLabel>
- [Label, kontrolka — omówienie](label-control-overview-windows-forms.md)
- [Instrukcje: łączenie z obiektem lub stroną sieci Web za pomocą kontrolki LinkLabel formularzy systemu Windows](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Instrukcje: zmienianie wyglądu kontrolki LinkLabel formularzy systemu Windows](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
