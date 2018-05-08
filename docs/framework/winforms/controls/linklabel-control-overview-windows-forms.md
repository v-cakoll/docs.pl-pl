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
ms.openlocfilehash: 40326a9055ff51efae5f4c64744d0966870c6f6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.LinkLabel> sterowanie umożliwia dodawanie łączy stylu sieci Web do aplikacji formularzy systemu Windows. Można użyć <xref:System.Windows.Forms.LinkLabel> kontroli dla wszystko, co umożliwia <xref:System.Windows.Forms.Label> sterować dla; można też określić część tekstu jako łącze do pliku, folderu lub strony sieci Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Co można zrobić za pomocą formantu LinkLabel  
 Oprócz tych właściwości, metod i zdarzeń <xref:System.Windows.Forms.Label> kontroli, <xref:System.Windows.Forms.LinkLabel> formant ma właściwości hiperłącza i kolory łączy. <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Właściwość ustawia obszar tekst, który uaktywnia łącze. <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, I <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> właściwości ustawione kolory łącza. <xref:System.Windows.Forms.LinkLabel.LinkClicked> Zdarzeń określa, co się stanie w przypadku wybrania tekst łącza.  
  
 Najprostsza stosowania <xref:System.Windows.Forms.LinkLabel> formant jest do wyświetlenia przy użyciu jednego łącza <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości, ale można również wyświetlić wiele hiperłącza, za pomocą <xref:System.Windows.Forms.LinkLabel.Links%2A> właściwości. <xref:System.Windows.Forms.LinkLabel.Links%2A> Właściwość umożliwia dostęp do kolekcji łączy. Można również określić, że dane w <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> właściwości poszczególnych <xref:System.Windows.Forms.LinkLabel.Link> obiektu. Wartość <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> właściwości może służyć do przechowywania lokalizację pliku do wyświetlania lub adres witryny sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.LinkLabel>  
 [Label, kontrolka — omówienie](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Instrukcje: łączenie z obiektem lub stroną internetową za pomocą kontrolki LinkLabel formularzy Windows Forms](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [Instrukcje: zmienianie wyglądu kontrolki LinkLabel formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
