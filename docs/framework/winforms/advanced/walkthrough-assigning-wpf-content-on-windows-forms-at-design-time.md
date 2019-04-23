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
ms.openlocfilehash: b4efef869c96ddb4e58445e45ecad12b5658f9f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343353"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a>Przewodnik: Przypisywanie zawartości WPF na formularzach systemu Windows w czasie projektowania
W tym instruktażu dowiesz się, jak wybrać typy kontrolek Windows Presentation Foundation (WPF), które mają być wyświetlane w formularzu. Możesz wybrać wszystkie typy kontrolek WPF, które są zawarte w projekcie.

 W tym przewodniku należy wykonać następujące zadania:

-   Utwórz projekt.

-   Tworzenie typów formantów WPF.

-   Wybierz kontrolek WPF.

> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Visual Studio 2012.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu Windows Forms.  
  
> [!NOTE]
>  Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `SelectingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>Tworzenie typów formantów WPF  
 Po dodaniu typów formantów WPF do projektu, można umieścić je w różnych <xref:System.Windows.Forms.Integration.ElementHost> kontrolki.  
  
#### <a name="to-create-wpf-control-types"></a>Aby utworzyć typy kontrolek WPF  
  
1. Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania. Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2. W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone. Aby uzyskać więcej informacji, zobacz [jak: Wybierz i Przesuń elementy na powierzchni projektowej](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).  
  
3. W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.  
  
4. Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanej zawartości**.  
  
5. Dodaj drugi WPF <xref:System.Windows.Controls.UserControl> do projektu. Użyj domyślnej nazwy dla kontrolek typu `UserControl2.xaml`.  
  
6. W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.  
  
7. Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanej zawartości 2**.  
  
 **Uwaga** ogólnie rzecz biorąc, należy obsługiwać bardziej złożone zawartości WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontroli jest tu używany wyłącznie w celach opisowy.  
  
1. Skompiluj projekt.  
  
## <a name="selecting-wpf-controls"></a>Zaznaczanie kontrolek WPF  
 Można przypisać różne zawartości WPF na <xref:System.Windows.Forms.Integration.ElementHost> formant, który jest już hosting zawartości.  
  
#### <a name="to-select-wpf-controls"></a>Aby wybrać kontrolek WPF  
  
1. Otwórz `Form1` w programie Windows Forms Designer.  
  
2. W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w formularzu.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
3. W panelu tagi inteligentne dla `elementHost1`, otwórz **zaznacz hostowana zawartość** listy rozwijanej.  
  
4. Wybierz **UserControl2** w polu listy rozwijanej.  
  
     `elementHost1` Kontroli teraz udostępnia wystąpienie `UserControl2` typu.  
  
5. W **właściwości** okna, upewnij się, że <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl2**.  
  
6. Z **przybornika**w **współdziałanie WPF** grupy, przeciągnij <xref:System.Windows.Forms.Integration.ElementHost> formant na formularzu.  
  
     Domyślna nazwa dla nowego formantu to `elementHost2`.  
  
7. W panelu tagi inteligentne dla `elementHost2`, otwórz **zaznacz hostowana zawartość** listy rozwijanej.  
  
8. Wybierz **UserControl1** z listy rozwijanej.  
  
9. `elementHost2` Kontroli teraz udostępnia wystąpienie `UserControl1` typu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)
- [Korzystanie z kontrolek WPF](using-wpf-controls.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
