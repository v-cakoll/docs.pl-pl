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
ms.openlocfilehash: 9837902bf56a402d623adbcf41558dcc568b7105
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745227"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.LinkLabel> Windows Forms pozwala dodawać linki w stylu sieci Web do aplikacji Windows Forms. Można użyć kontrolki <xref:System.Windows.Forms.LinkLabel> dla wszystkich elementów, których można użyć w kontrolce <xref:System.Windows.Forms.Label> dla programu; Możesz również ustawić część tekstu jako link do pliku, folderu lub strony sieci Web.  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>Co możesz zrobić za pomocą kontrolki LinkLabel  
 Oprócz wszystkich właściwości, metod i zdarzeń formantu <xref:System.Windows.Forms.Label> kontrolka <xref:System.Windows.Forms.LinkLabel> ma właściwości dla hiperłączy i kolorów łączy. Właściwość <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> ustawia obszar tekstu, który aktywuje link. Właściwości <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>i <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> ustawiają kolory łącza. Zdarzenie <xref:System.Windows.Forms.LinkLabel.LinkClicked> określa, co dzieje się po wybraniu tekstu linku.  
  
 Najprostszym sposobem użycia formantu <xref:System.Windows.Forms.LinkLabel> jest wyświetlenie jednego linku przy użyciu właściwości <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, ale można również wyświetlić wiele hiperlinków przy użyciu właściwości <xref:System.Windows.Forms.LinkLabel.Links%2A>. Właściwość <xref:System.Windows.Forms.LinkLabel.Links%2A> umożliwia dostęp do kolekcji linków. Możesz również określić dane we właściwości <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> każdego pojedynczego obiektu <xref:System.Windows.Forms.LinkLabel.Link>. Wartość właściwości <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> może służyć do przechowywania lokalizacji pliku do wyświetlenia lub adresu witryny sieci Web.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.LinkLabel>
- [Label, kontrolka — omówienie](label-control-overview-windows-forms.md)
- [Instrukcje: łączenie z obiektem lub stroną internetową za pomocą kontrolki LinkLabel formularzy Windows Forms](link-to-an-object-or-web-page-with-wf-linklabel-control.md)
- [Instrukcje: zmienianie wyglądu kontrolki LinkLabel formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
