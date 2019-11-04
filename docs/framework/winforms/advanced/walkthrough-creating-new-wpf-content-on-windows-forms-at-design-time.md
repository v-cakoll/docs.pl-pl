---
title: 'Wskazówki: tworzenie nowej zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 395543a3141af66038cabef9a3c9fed40a36b47e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460655"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania

W tym artykule pokazano, jak utworzyć formant Windows Presentation Foundation (WPF) do użycia w aplikacjach opartych na Windows Forms.

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="create-the-project"></a>Utwórz projekt

Otwórz program Visual Studio i Utwórz nowy projekt **aplikacji Windows Forms (.NET Framework)** w Visual Basic lub wizualizacji C# o nazwie `HostingWpf`.

> [!NOTE]
> W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.

## <a name="create-a-new-wpf-control"></a>Utwórz nową kontrolkę WPF

Utworzenie nowej kontrolki WPF i dodanie jej do projektu jest tak proste jak dodanie innego elementu do projektu. Projektant formularzy systemu Windows działa z określonym rodzajem kontrolki o nazwie *formant złożony*lub *kontrolka użytkownika*. Aby uzyskać więcej informacji na temat kontrolek użytkownika WPF, zobacz <xref:System.Windows.Controls.UserControl>.

> [!NOTE]
> Typ <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> dla WPF jest różny od typu kontrolki użytkownika dostarczonej przez Windows Forms, która jest również nazywana <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.

Aby utworzyć nową kontrolkę WPF:

1. W **Eksplorator rozwiązań**Dodaj nowy projekt **biblioteki formantów użytkownika WPF (.NET Framework)** do rozwiązania. Użyj domyślnej nazwy biblioteki formantów `WpfControlLibrary1`. Domyślna nazwa kontrolki to `UserControl1.xaml`.

   Dodanie nowej kontrolki ma następujące skutki:

   - Plik UserControl1. XAML został dodany.

   - Dodano plik UserControl1.xaml.cs (lub UserControl1. XAML. vb). Ten plik zawiera kod związany z obsługą zdarzeń oraz inne implementacje.

   - Dodano odwołania do zestawów WPF.

   - Plik UserControl1. XAML zostanie otwarty w projektancie WPF dla programu Visual Studio.

2. W widok Projekt upewnij się, że wybrano pozycję `UserControl1`.

3. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.

4. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> na powierzchnię projektu.

5. W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Controls.TextBox.Text%2A> na **hostowaną zawartość**.

   > [!NOTE]
   > Ogólnie rzecz biorąc, należy hostować bardziej zaawansowaną zawartość WPF. Kontrolka <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> jest używana tutaj tylko do celów informacyjnych.

6. Skompiluj projekt.

## <a name="add-a-wpf-control-to-a-windows-form"></a>Dodawanie formantu WPF do formularza systemu Windows

Nowa kontrolka WPF jest gotowa do użycia w formularzu. Windows Forms używa kontrolki <xref:System.Windows.Forms.Integration.ElementHost> do hostowania zawartości WPF.

Aby dodać formant WPF do formularza systemu Windows:

1. Otwórz `Form1` w Projektant formularzy systemu Windows.

2. W **przyborniku**Znajdź kartę z **WPFUserControlLibraryą formantów użytkownika WPF**.

3. Przeciągnij wystąpienie `UserControl1` na formularz.

    - Formant <xref:System.Windows.Forms.Integration.ElementHost> jest automatycznie tworzony w formularzu, aby hostować formant WPF.

    - Kontrolka <xref:System.Windows.Forms.Integration.ElementHost> ma nazwę `elementHost1` i w oknie **Właściwości** można zobaczyć, że właściwość <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> jest ustawiona na **UserControl1**.

    - Odwołania do zestawów WPF są dodawane do projektu.

    - Kontrolka `elementHost1` ma panel tagu inteligentnego, który zawiera dostępne opcje hostingu.

4. W panelu Tagi inteligentne **ElementHost zadania** wybierz pozycję **Zadokuj w kontenerze nadrzędnym**.

5. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.

## <a name="next-steps"></a>Następne kroki

Windows Forms i WPF są różnymi technologiami, ale są one tak zaprojektowane, aby ściśle współpracować. Aby zapewnić bogatszy wygląd i zachowanie aplikacji, spróbuj wykonać następujące czynności:

- Hostowanie kontrolki Windows Forms na stronie WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: hosting formantu Windows Forms w WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).

- Zastosuj Windows Forms style wizualne do zawartości WPF. Aby uzyskać więcej informacji, zobacz [jak: włączyć style wizualne w aplikacji hybrydowej](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).

- Zmień styl zawartości WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: style zawartości WPF](walkthrough-styling-wpf-content.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
