---
title: 'Przewodnik: Przypisywanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc5f5e2d8808c0a60df721bf2c0ed76b45ef49a0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666260"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>Przewodnik: Przypisywanie zawartości WPF na Windows Forms w czasie projektowania

W tym artykule pokazano, jak wybrać typy formantów Windows Presentation Foundation (WPF), które mają być wyświetlane w formularzu. Można wybrać dowolne typy formantów WPF, które są uwzględnione w projekcie.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub C# wizualizacji `SelectingWpfContent`o nazwie.

> [!NOTE]
> W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.

## <a name="create-the-wpf-control-types"></a>Tworzenie typów formantów WPF

Po dodaniu typów formantów WPF do projektu można hostować je w różnych <xref:System.Windows.Forms.Integration.ElementHost> kontrolkach.

1. Dodaj nowy projekt WPF <xref:System.Windows.Controls.UserControl> do rozwiązania. Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`. Aby uzyskać więcej informacji, [zobacz Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)projektowania.

2. W widok Projekt upewnij się, że `UserControl1` jest zaznaczone.

3. W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Dodaj kontrolkę <xref:System.Windows.Controls.UserControl> do i <xref:System.Windows.Controls.TextBox.Text%2A> ustaw wartość właściwości na **hostowaną zawartość**. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

5. Dodaj drugi WPF <xref:System.Windows.Controls.UserControl> do projektu. Użyj domyślnej nazwy dla typu formantu, `UserControl2.xaml`.

6. W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

7. Dodaj kontrolkę <xref:System.Windows.Controls.UserControl> do i <xref:System.Windows.Controls.TextBox.Text%2A> ustaw wartość właściwości na **hostowaną zawartość 2**. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

   > [!NOTE]
   > Ogólnie rzecz biorąc, należy hostować bardziej zaawansowaną zawartość WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontrolka jest używana w tym miejscu tylko do celów informacyjnych.

8. Skompiluj projekt.

## <a name="select-wpf-controls"></a>Wybieranie formantów WPF

Można przypisać inną zawartość WPF do <xref:System.Windows.Forms.Integration.ElementHost> kontrolki, która jest już hostem zawartości.

1. Otwórz `Form1` w Projektant formularzy systemu Windows.

2. W **przyborniku**kliknij `UserControl1` dwukrotnie, aby utworzyć wystąpienie elementu `UserControl1` w formularzu.

   Wystąpienie `UserControl1` jest hostowane w nowym <xref:System.Windows.Forms.Integration.ElementHost> formancie o nazwie `elementHost1`.

3. W panelu tagów inteligentnych dla programu `elementHost1`Otwórz listę rozwijaną **Wybierz hostowaną zawartość** .

4. W polu listy rozwijanej wybierz pozycję **UserControl2** .

   Kontrolka teraz obsługuje wystąpienie `UserControl2` typu. `elementHost1`

5. W oknie **Właściwości** upewnij się, że <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl2**.

6. Z **przybornika**w grupie współdziałanie **WPF** przeciągnij <xref:System.Windows.Forms.Integration.ElementHost> kontrolkę na formularz.

   Domyślna nazwa nowej kontrolki to `elementHost2`.

7. W panelu tagów inteligentnych dla programu `elementHost2`Otwórz listę rozwijaną **Wybierz hostowaną zawartość** .

8. Wybierz pozycję **UserControl1** z listy rozwijanej.

9. Kontrolka teraz obsługuje wystąpienie `UserControl1` typu. `elementHost2`

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
