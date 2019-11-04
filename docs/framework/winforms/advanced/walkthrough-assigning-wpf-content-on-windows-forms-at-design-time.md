---
title: 'Wskazówki: przypisywanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c1e0c91b7ab8bded677a86b597b02b9cb442d98
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460673"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>Przewodnik: przypisywanie zawartości WPF na Windows Forms w czasie projektowania

W tym artykule pokazano, jak wybrać typy formantów Windows Presentation Foundation (WPF), które mają być wyświetlane w formularzu. Można wybrać dowolne typy formantów WPF, które są uwzględnione w projekcie.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub wizualizacji C# o nazwie `SelectingWpfContent`.

> [!NOTE]
> W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.

## <a name="create-the-wpf-control-types"></a>Tworzenie typów formantów WPF

Po dodaniu typów formantów WPF do projektu można hostować je w różnych <xref:System.Windows.Forms.Integration.ElementHost>ych kontrolkach.

1. Dodaj nowy projekt WPF <xref:System.Windows.Controls.UserControl> do rozwiązania. Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. W widok Projekt upewnij się, że wybrano pozycję `UserControl1`.

3. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Dodaj kontrolkę <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> do <xref:System.Windows.Controls.UserControl> i ustaw wartość właściwości <xref:System.Windows.Controls.TextBox.Text%2A> na **hostowaną zawartość**.

5. Dodaj drugi <xref:System.Windows.Controls.UserControl> WPF do projektu. Użyj domyślnej nazwy dla typu formantu, `UserControl2.xaml`.

6. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

7. Dodaj kontrolkę <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> do <xref:System.Windows.Controls.UserControl> i ustaw wartość właściwości <xref:System.Windows.Controls.TextBox.Text%2A> na **hostowaną zawartość 2**.

   > [!NOTE]
   > Ogólnie rzecz biorąc, należy hostować bardziej zaawansowaną zawartość WPF. Kontrolka <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> jest używana tutaj tylko do celów informacyjnych.

8. Skompiluj projekt.

## <a name="select-wpf-controls"></a>Wybieranie formantów WPF

Możesz przypisać inną zawartość WPF do kontrolki <xref:System.Windows.Forms.Integration.ElementHost>, która już obsługuje zawartość.

1. Otwórz `Form1` w Projektant formularzy systemu Windows.

2. W **przyborniku**kliknij dwukrotnie `UserControl1`, aby utworzyć wystąpienie `UserControl1` w formularzu.

   Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost1`.

3. Na panelu tagów inteligentnych dla `elementHost1`Otwórz listę rozwijaną **Wybierz hostowaną zawartość** .

4. W polu listy rozwijanej wybierz pozycję **UserControl2** .

   Kontrolka `elementHost1` teraz obsługuje wystąpienie typu `UserControl2`.

5. W oknie **Właściwości** upewnij się, że właściwość <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> jest ustawiona na **UserControl2**.

6. Z **przybornika**w grupie **współdziałanie WPF** przeciągnij kontrolkę <xref:System.Windows.Forms.Integration.ElementHost> na formularz.

   Domyślna nazwa nowej kontrolki jest `elementHost2`.

7. Na panelu tagów inteligentnych dla `elementHost2`Otwórz listę rozwijaną **Wybierz hostowaną zawartość** .

8. Wybierz pozycję **UserControl1** z listy rozwijanej.

9. Kontrolka `elementHost2` teraz obsługuje wystąpienie typu `UserControl1`.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
