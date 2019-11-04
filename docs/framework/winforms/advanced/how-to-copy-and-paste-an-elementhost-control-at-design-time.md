---
title: 'Porady: kopiowanie i wklejanie formantu ElementHost w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e89510558274558e560bf810afe746e250ff26a4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459230"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Instrukcje: kopiowanie i wklejanie kontrolki ElementHost

Ta procedura pokazuje, jak skopiować formant Windows Presentation Foundation (WPF) w formularzu systemu Windows w programie Visual Studio.

1. W programie Visual Studio Dodaj nowy <xref:System.Windows.Controls.UserControl> WPF do projektu Windows Forms. Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> `UserControl1` na **200**.

3. Ustaw wartość właściwości <xref:System.Windows.Controls.Control.Background%2A> na **niebieską**.

4. Skompiluj projekt.

5. Otwórz `Form1` w Projektant formularzy systemu Windows.

6. Z **przybornika**przeciągnij wystąpienie `UserControl1` na formularz.

   Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost1`.

7. Po wybraniu `elementHost1` naciśnij **kombinację klawiszy Ctrl**+**C** , aby skopiować ją do Schowka.

8. Naciśnij klawisz **Ctrl**+**V** , aby wkleić skopiowany formant do formularza.

   W formularzu zostanie utworzona nowa kontrolka <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost2`.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
