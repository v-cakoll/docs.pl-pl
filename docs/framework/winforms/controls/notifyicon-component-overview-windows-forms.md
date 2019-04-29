---
title: NotifyIcon — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 430d869265b9add34c6de617a178aa27af6218f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627866"
---
# <a name="notifyicon-component-overview-windows-forms"></a>NotifyIcon — Informacje o składniku (Formularze systemu Windows)

Formularze Windows <xref:System.Windows.Forms.NotifyIcon> składnik jest zazwyczaj używany do wyświetlanie ikon dla procesów, które są uruchomione w tle i nie są wyświetlane użytkownikowi interfejs większość czasu. Przykładem może być program ochrony przed wirusami, który jest możliwy, klikając ikonę w obszarze stanu powiadomień paska zadań.

## <a name="key-properties-of-notifyicons"></a>Właściwości klucza obiektu NotifyIcons

Każdy <xref:System.Windows.Forms.NotifyIcon> składnik Wyświetla pojedynczą ikonę w obszarze stanu. Jeśli masz trzy procesy w tle i chcesz wyświetlić ikonę dla każdego, należy dodać trzy <xref:System.Windows.Forms.NotifyIcon> składników do formularza. Właściwości klucza obiektu <xref:System.Windows.Forms.NotifyIcon> składnik to <xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. <xref:System.Windows.Forms.NotifyIcon.Icon%2A> Właściwość ustawia ikonę, która jest wyświetlana w obszarze stanu. Aby pojawia się ikona <xref:System.Windows.Forms.NotifyIcon.Visible%2A> właściwość musi być równa `true`.

## <a name="notifyicons-options"></a>Opcje NotifyIcons

Możesz skojarzyć dymek porad, menu skrótów i etykietki narzędzi z <xref:System.Windows.Forms.NotifyIcon> ułatwiają użytkownika.

Możesz wyświetlić dymek porady dotyczące <xref:System.Windows.Forms.NotifyIcon> przez wywołanie metody <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> metody, określając zakres czasu ma dymku do wyświetlenia. Można również określić tekst, ikona i tytuł dymku z <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> i <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, odpowiednio. <xref:System.Windows.Forms.NotifyIcon> składniki mogą także mieć skojarzone etykietki narzędzi i menu skrótów. Aby uzyskać więcej informacji, zobacz [— informacje o składniku ToolTip](tooltip-component-overview-windows-forms.md) i [— informacje o składniku ContextMenu](contextmenu-component-overview-windows-forms.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.NotifyIcon>
- [NotifyIcon, składnik](notifyicon-component-windows-forms.md)