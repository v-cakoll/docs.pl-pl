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
ms.openlocfilehash: abdeb2e77486d4f94f3d0543d94186168baae31c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528658"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a>Wskazówki: przypisywanie zawartości WPF na formularzach systemu Windows w czasie projektowania
W tym przewodniku opisano sposób wybierz typy formantów systemu Windows Presentation Foundation (WPF), które mają być wyświetlane w formularzu. Możesz wybrać wszystkie typy formantów WPF, które są zawarte w projekcie.  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Tworzenie projektu.  
  
-   Utwórz typy formantów WPF.  
  
-   Wybierz formantów WPF.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.  
  
> [!NOTE]
>  Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `SelectingWpfContent`.  
  
## <a name="creating-the-wpf-control-types"></a>Tworzenie typy formantów WPF  
 Po dodaniu typy formantów WPF do projektu może obsługiwać je w różnych <xref:System.Windows.Forms.Integration.ElementHost> kontrolki.  
  
#### <a name="to-create-wpf-control-types"></a>Aby utworzyć typy formantów WPF  
  
1.  Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania. Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone. Aby uzyskać więcej informacji, zobacz [porady: Wybierz i Przenieś elementy na powierzchnię projektu](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.  
  
4.  Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanego zawartości**.  
  
5.  Dodaj drugi WPF <xref:System.Windows.Controls.UserControl> do projektu. Użyj domyślnej nazwy dla typu formantu `UserControl2.xaml`.  
  
6.  W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.  
  
7.  Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanego zawartości 2**.  
  
 **Uwaga** ogólnie rzecz biorąc, należy udostępnić dokładniejsze zawartości WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontroli jest tu używany wyłącznie w celach ilustracyjnych.  
  
1.  Skompiluj projekt.  
  
## <a name="selecting-wpf-controls"></a>Zaznaczanie formantów WPF  
 Można przypisać różne zawartości WPF <xref:System.Windows.Forms.Integration.ElementHost> kontroli, która obecnie prowadzi hosting zawartości.  
  
#### <a name="to-select-wpf-controls"></a>Aby wybrać formantów WPF  
  
1.  Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.  
  
2.  W **przybornika**, kliknij dwukrotnie `UserControl1` można utworzyć wystąpienia `UserControl1` w formularzu.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
3.  W panelu tagów inteligentnych dla `elementHost1`, otwórz **wybierz hostowanej zawartości** listy rozwijanej.  
  
4.  Wybierz **UserControl2** w polu listy rozwijanej.  
  
     `elementHost1` Kontroli teraz udostępnia wystąpienie `UserControl2` typu.  
  
5.  W **właściwości** okna, upewnij się, że <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl2**.  
  
6.  Z **przybornika**w **współdziałanie WPF** grupy, przeciągnij <xref:System.Windows.Forms.Integration.ElementHost> sterowania do formularza.  
  
     Domyślna nazwa nowego formantu jest `elementHost2`.  
  
7.  W panelu tagów inteligentnych dla `elementHost2`, otwórz **wybierz hostowanej zawartości** listy rozwijanej.  
  
8.  Wybierz **UserControl1** z listy rozwijanej.  
  
9. `elementHost2` Kontroli teraz udostępnia wystąpienie `UserControl1` typu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Korzystanie z kontrolek WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
