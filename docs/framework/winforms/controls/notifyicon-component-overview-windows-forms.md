---
title: NotifyIcon, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 587bf514db853f1122ed16abc05a195985c5ce8d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742125"
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon — Informacje o składniku (Formularze systemu Windows)

Składnik <xref:System.Windows.Forms.NotifyIcon> Windows Forms jest zazwyczaj używany do wyświetlania ikon procesów, które są uruchamiane w tle i nie wyświetlają przez wiele czasu interfejsu użytkownika. Przykładem będzie program ochrony przed wirusami, do którego można uzyskać dostęp, klikając ikonę w obszarze powiadomień o stanie na pasku zadań.

## <a name="key-properties-of-notifyicons"></a>Właściwości klucza NotifyIcons

Każdy składnik <xref:System.Windows.Forms.NotifyIcon> Wyświetla pojedynczą ikonę w obszarze stan. Jeśli masz trzy procesy w tle i chcesz wyświetlić ikonę dla każdej z nich, musisz dodać trzy składniki <xref:System.Windows.Forms.NotifyIcon> do formularza. Właściwości klucza składnika <xref:System.Windows.Forms.NotifyIcon> są <xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. Właściwość <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ustawia ikonę wyświetlaną w obszarze stan. Aby ikona była wyświetlana, właściwość <xref:System.Windows.Forms.NotifyIcon.Visible%2A> musi mieć wartość `true`.

## <a name="notifyicons-options"></a>Opcje NotifyIcons

Można kojarzyć porady dymkowe, menu skrótów i etykietki narzędzi z <xref:System.Windows.Forms.NotifyIcon>, aby pomóc użytkownikowi.

Możesz wyświetlić wskazówki dotyczące <xref:System.Windows.Forms.NotifyIcon>, wywołując metodę <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A>, określając czas, w którym ma być wyświetlana etykietka dymka. Możesz również określić tekst, ikonę i tytuł etykietki dymek odpowiednio <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> i <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>. składniki <xref:System.Windows.Forms.NotifyIcon> mogą także mieć skojarzone etykietki narzędzi i menu skrótów. Aby uzyskać więcej informacji, zobacz Omówienie [składnika ToolTip](tooltip-component-overview-windows-forms.md) i [składnik zestawienia](contextmenu-component-overview-windows-forms.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.NotifyIcon>
- [NotifyIcon, składnik](notifyicon-component-windows-forms.md)
