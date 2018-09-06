---
title: 'Wskazówki: debugowanie niestandardowych formantów formularzy systemu Windows w czasie projektowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
ms.openlocfilehash: 824c1e47cf50dc13a3a986e48a49158b15dbb935
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878034"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a>Wskazówki: debugowanie niestandardowych formantów formularzy systemu Windows w czasie projektowania
Kiedy tworzysz formant niestandardowy, będzie często jest konieczne do debugowania zachowania w czasie projektowania. Jest to szczególnie istotne w przypadku tworzenia niestandardowego projektanta dla formantu niestandardowego. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie Windows Forms kontroli, przyjmuje korzystać z czasu projektowania funkcje programu Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
 Kontrolki niestandardowe przy użyciu programu Visual Studio umożliwia debugowanie tak samo, jak debuguje się inne klasy .NET Framework. Różnica polega na to, że będziesz debugował osobnego wystąpienia programu Visual Studio, który jest uruchomiony kod kontrolki niestandardowej  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie projektu Windows Forms do hostowania formantu niestandardowego  
  
-   Tworzenie projektu biblioteki kontrolek  
  
-   Dodawanie właściwości do kontrolki niestandardowej  
  
-   Dodawanie niestandardowego formantu do formularza hosta  
  
-   Konfigurowanie projektu dla debugowania w czasie projektowania  
  
-   Debugowanie niestandardowego formantu w czasie projektowania  
  
 Gdy skończysz, masz zrozumienia zadań niezbędnych do debugowania zachowania w czasie projektowania formantu niestandardowego.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu aplikacji. Użyjesz tego projektu do kompilowania aplikacji, który jest hostem kontrolki niestandardowej.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Utwórz projekt aplikacji Windows o nazwie "DebuggingExample" (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
## <a name="creating-a-control-library-project"></a>Tworzenie projektu biblioteki kontrolek  
 Następnym krokiem jest tworzenie projektu biblioteki kontrolek i konfigurowanie kontrolki niestandardowej.  
  
#### <a name="to-create-the-control-library-project"></a>Aby utworzyć projekt Biblioteka formantów  
  
1.  Dodaj **Biblioteka formantów Windows** projektu do rozwiązania.  
  
2.  Dodaj nową **UserControl** elementu do projektu DebugControlLibrary. Aby uzyskać więcej informacji, zobacz [NIB: instrukcje: dodawanie nowych elementów projektu](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce). Nazwij nowy plik źródłowy podstawowego elementu "DebugControl".  
  
3.  Za pomocą **Eksploratora rozwiązań**, usunąć projekt domyślny formant przez usunięcie pliku kodu z podstawowej nazwy "`UserControl1`". Aby uzyskać więcej informacji, zobacz [NIB: instrukcje: usuwanie, usuwania i wykluczyć elementy](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
4.  Skompiluj rozwiązanie.  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można wyświetlić niestandardową kontrolkę w **przybornika**.  
  
#### <a name="to-check-your-progress"></a>Aby sprawdzić postęp  
  
-   Znajdź Nowa karta o nazwie **składniki DebugControlLibrary** i kliknij, aby go zaznaczyć. Po otwarciu, zobaczysz kontrolki wymieniony jako **DebugControl** z domyślną ikonę obok niej.  
  
## <a name="adding-a-property-to-your-custom-control"></a>Dodawanie właściwości do kontrolki niestandardowej  
 Aby zademonstrować, że formant niestandardowy kod jest uruchamiany w czasie projektowania, możesz dodać właściwość i ustaw punkt przerwania w kodzie, który implementuje właściwości.  
  
#### <a name="to-add-a-property-to-your-custom-control"></a>Aby dodać właściwość do formantu niestandardowego  
  
1.  Otwórz **DebugControl** w **Edytor kodu**. Dodaj następujący kod do definicji klasy:  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  Skompiluj rozwiązanie.  
  
## <a name="adding-your-custom-control-to-the-host-form"></a>Dodawanie niestandardowego formantu do formularza hosta  
 Do debugowania zachowania w czasie projektowania niestandardową kontrolkę, spowoduje umieszczenie wystąpienia klasy kontrolki niestandardowej w formularzu hosta.  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a>Aby dodać niestandardową kontrolkę w formularzu hosta  
  
1.  W projekcie "DebuggingExample" Otwórz formularz Form1 w **Windows Forms Designer**.  
  
2.  W **przybornika**, otwórz **składniki DebugControlLibrary** kartę, a następnie przeciągnij **DebugControl** wystąpienia do formularza.  
  
3.  Znajdź `DemoString` właściwości niestandardowe w **właściwości** okna. Należy pamiętać, że można zmienić jego wartość, jak w przypadku wszystkich innych właściwości. Należy również zauważyć, że w przypadku `DemoString` właściwości jest zaznaczone, ciąg opisu właściwości, pojawia się w dolnej części **właściwości** okna.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Konfigurowanie projektu dla debugowania w czasie projektowania  
 Do debugowania zachowania w czasie projektowania formantu niestandardowego, będzie debugować osobnego wystąpienia programu Visual Studio, który jest uruchomiony formantu niestandardowego kodu.  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Aby skonfigurować projekt do debugowania w czasie projektowania  
  
1.  Kliknij prawym przyciskiem myszy **DebugControlLibrary** projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.  
  
2.  W **DebugControlLibrary** arkusza właściwości, wybierz opcję **debugowania** kartę.  
  
     W **Akcja uruchamiania** zaznacz **uruchomienia programu zewnętrznego**. Można więc debugowanie osobnego wystąpienia programu Visual Studio, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby przejść do środowiska IDE programu Visual Studio. Nazwa pliku wykonywalnego jest **devenv.exe**, a jeśli został zainstalowany w lokalizacji domyślnej, jego ścieżka jest %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.  
  
3.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
4.  Kliknij prawym przyciskiem myszy **DebugControlLibrary** projektu, a następnie wybierz **Ustaw jako projekt startowy** umożliwiające tej konfiguracji debugowania.  
  
## <a name="debugging-your-custom-control-at-design-time"></a>Debugowanie niestandardowego formantu w czasie projektowania  
 Teraz można przystąpić do debugowania niestandardową kontrolkę, jak działa w trybie projektowania. Podczas uruchamiania sesji debugowania, zostanie utworzone nowe wystąpienie programu Visual Studio, a następnie użyje ładowanie rozwiązań "DebuggingExample". Po otwarciu formularza Form1 w **projektanta formularzy**, wystąpienie niestandardową kontrolkę zostanie utworzona i zostanie uruchomione.  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a>Aby debugować niestandardową kontrolkę w czasie projektowania  
  
1.  Otwórz **DebugControl** pliku źródłowego w **Edytor kodu** i umieść punkt przerwania na `Set` akcesor `DemoString` właściwości.  
  
2.  Naciśnij klawisz F5, aby rozpocząć sesję debugowania. Należy pamiętać, że tworzone jest nowe wystąpienie programu Visual Studio. Można rozróżnić wystąpień na dwa sposoby:  
  
    -   Wystąpienie debugowania zawiera wyraz **systemem** na pasku tytułu  
  
    -   Wystąpienie debugowania ma **Start** znajdujący się na jej **debugowania** narzędzi wyłączone  
  
     Punkt przerwania jest ustawiony za wystąpienie debugowania.  
  
3.  Nowe wystąpienie programu Visual Studio Otwórz rozwiązanie "DebuggingExample". Rozwiązanie można łatwo znaleźć, wybierając **ostatnich projektów** z **pliku** menu. Plik rozwiązania "DebuggingExample.sln" będą wyświetlane zgodnie z ostatnio używanych plików.  
  
4.  Otwórz formularz Form1 w **projektanta formularzy** i wybierz **DebugControl** kontroli.  
  
5.  Zmień wartość właściwości `DemoString` właściwości. Pamiętaj, że po zatwierdzeniu zmiany wystąpienie debugowania programu Visual Studio uzyskuje fokus wykonywania zatrzymuje się na punkt przerwania. Możesz pojedynczy krok za pomocą metody dostępu właściwości podobnie jak usługi będzie inny kod.  
  
6.  Po zakończeniu sesji debugowania możesz wyjść, odrzucanie hostowanej wystąpieniu programu Visual Studio lub klikając **Zatrzymaj debugowanie** przycisk wystąpienie debugowania.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, aby można było debugować Kontrolki niestandardowe, w czasie projektowania, istnieje wiele możliwości rozszerzania kontroli nad interakcji ze środowiskiem IDE programu Visual Studio.  
  
-   Możesz użyć <xref:System.ComponentModel.Component.DesignMode%2A> właściwość <xref:System.ComponentModel.Component> klasy pisanie kodu, który będzie wykonywać tylko w czasie projektowania. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.Component.DesignMode%2A>.  
  
-   Istnieje kilka atrybutów można zastosować do właściwości formantu do manipulowania interakcji kontrolki niestandardowej za pomocą projektanta. Można znaleźć tych atrybutów w <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw.  
  
-   Możesz napisać niestandardowego projektanta dla niestandardowej kontrolki. Zapewnia pełną kontrolę nad środowiskiem projektowania przy użyciu rozszerzonego infrastruktury projektanta udostępnianych przez program Visual Studio. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie Windows Forms kontroli, przyjmuje korzystać z czasu projektowania funkcje programu Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [Porady: uzyskiwanie dostępu do usług w czasie projektowania](https://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [Porady: dostęp do obsługi w czasie projektowania w formularzach Windows Forms](https://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
