---
title: 'Instrukcje: Kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666178"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Instrukcje: Kopiowanie i wklejanie kontrolki ElementHost

Ta procedura pokazuje, jak skopiować formant Windows Presentation Foundation (WPF) w formularzu systemu Windows w programie Visual Studio.

1. W programie Visual Studio Dodaj nową WPF <xref:System.Windows.Controls.UserControl> do projektu Windows Forms. Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`. Aby uzyskać więcej informacji, [zobacz Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)projektowania.

2. W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości `UserControl1` i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

3. Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości na niebieską.

4. Skompiluj projekt.

5. Otwórz `Form1` w Projektant formularzy systemu Windows.

6. Z **przybornika**przeciągnij wystąpienie `UserControl1` na formularz.

   Wystąpienie `UserControl1` jest hostowane w nowym <xref:System.Windows.Forms.Integration.ElementHost> formancie o nazwie `elementHost1`.

7. Po wybraniu naciśnij klawisz **Ctrl**+C, aby skopiować go do Schowka. `elementHost1`

8. Naciśnij klawisz **Ctrl**+, aby wkleić skopiowany formant do formularza.

   W formularzu <xref:System.Windows.Forms.Integration.ElementHost> zostanie utworzona `elementHost2` Nowa kontrolka o nazwie.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
