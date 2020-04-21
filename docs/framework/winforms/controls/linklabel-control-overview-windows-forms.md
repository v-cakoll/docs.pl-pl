---
title: LinkLabel, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 3e8607644c858ae804e384c974b5e81c1786c6a1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739520"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel — Informacje o formancie [Formularze systemu Windows]
Formant <xref:System.Windows.Forms.LinkLabel> Formularze systemu Windows umożliwia dodawanie łączy w stylu sieci Web do aplikacji Windows Forms. Można użyć <xref:System.Windows.Forms.LinkLabel> formantu dla wszystkiego, <xref:System.Windows.Forms.Label> dla czego można użyć formantu; Można również ustawić część tekstu jako łącze do pliku, folderu lub strony sieci Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Co można zrobić z LinkLabel Control  
 Oprócz wszystkich właściwości, metod i zdarzeń <xref:System.Windows.Forms.Label> formantu, <xref:System.Windows.Forms.LinkLabel> formant ma właściwości hiperłącza i kolorów łączy. Właściwość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> ustawia obszar tekstu, który aktywuje łącze. Właściwości <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> i właściwości ustawiają kolory łącza. Zdarzenie <xref:System.Windows.Forms.LinkLabel.LinkClicked> określa, co się stanie, gdy tekst łącza jest zaznaczony.  
  
 Najprostszym zastosowaniem <xref:System.Windows.Forms.LinkLabel> formantu jest wyświetlanie pojedynczego łącza za pomocą <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> właściwości, ale <xref:System.Windows.Forms.LinkLabel.Links%2A> można również wyświetlić wiele hiperłączy przy użyciu właściwości. Właściwość <xref:System.Windows.Forms.LinkLabel.Links%2A> umożliwia dostęp do kolekcji łączy. Można również określić <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> dane we <xref:System.Windows.Forms.LinkLabel.Link> właściwości każdego obiektu. Wartość <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> właściwości może służyć do przechowywania lokalizacji pliku do wyświetlenia lub adresu witryny sieci Web.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.LinkLabel>
- [Label — Informacje o formancie](label-control-overview-windows-forms.md)
- [Instrukcje: łączenie z obiektem lub stroną internetową za pomocą kontrolki LinkLabel formularzy Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Porady: zmienianie wyglądu formantu LinkLabel formularzy systemu Windows](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
