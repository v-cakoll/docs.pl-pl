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
ms.openlocfilehash: b87c46b2182884f90b427498b9af696d14acac96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a>Wskazówki: debugowanie niestandardowych formantów formularzy systemu Windows w czasie projektowania
Podczas tworzenia niestandardowego formantu będzie często jest konieczne do debugowania swojego zachowania w czasie projektowania. Jest to szczególnie w przypadku tworzenia niestandardowych projektanta dla formantu niestandardowego. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie funkcje systemu Windows formularze kontroli czy ma korzystać z programu Visual Studio czasu projektowania](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
 Kontrolki niestandardowe przy użyciu programu Visual Studio można debugować tak samo, jak może debugować innych klas .NET Framework. Różnica polega na tym że będzie debugowania osobnego wystąpienia programu Visual Studio, która działa formantu niestandardowego kodu  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu formularzy systemu Windows do hostowania formantu niestandardowego  
  
-   Tworzenie projektu biblioteki formantu  
  
-   Dodawanie właściwości do formantu niestandardowego  
  
-   Dodawanie formantu niestandardowego do formularza hosta  
  
-   Konfigurowanie projektu debugowanie w czasie projektowania  
  
-   Debugowanie formantu niestandardowego w czasie projektowania  
  
 Gdy skończysz, konieczne będzie zrozumienia zadań niezbędnych do debugowania zachowania czasu projektowania formantu niestandardowego.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu aplikacji. Użyjesz tego projektu do tworzenia aplikacji, która obsługuje kontrolki niestandardowej.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Utwórz projekt aplikacji systemu Windows o nazwie "DebuggingExample". Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
## <a name="creating-a-control-library-project"></a>Tworzenie projektu biblioteki formantu  
 Następnym krokiem jest utworzenie projektu biblioteki kontroli i skonfigurować kontrolki niestandardowej.  
  
#### <a name="to-create-the-control-library-project"></a>Aby utworzyć projekt z kontroli biblioteki  
  
1.  Dodaj **Biblioteka formantów systemu Windows** projektu do rozwiązania.  
  
2.  Dodaj nową **UserControl** elementu do projektu DebugControlLibrary. Aby uzyskać więcej informacji, zobacz [NIB: porady: dodawanie nowych elementów projektu](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce). Nadaj nazwę bazową "DebugControl" nowego pliku źródłowego.  
  
3.  Przy użyciu **Eksploratora rozwiązań**, usuń formant domyślnego projektu przez usunięcie pliku kodu z podstawowej nazwy "`UserControl1`". Aby uzyskać więcej informacji, zobacz [NIB: porady: usuwanie, usuwania i wykluczanie elementów](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
4.  Skompiluj rozwiązanie.  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można odwołać się do niestandardowego formantu w **przybornika**.  
  
#### <a name="to-check-your-progress"></a>Aby sprawdzić postęp  
  
-   Znajdź nową kartę o nazwie **składniki DebugControlLibrary** i kliknij, aby go zaznaczyć. Po otwarciu, zobaczysz formantu wymienionym **DebugControl** z domyślną ikonę obok siebie.  
  
## <a name="adding-a-property-to-your-custom-control"></a>Dodawanie właściwości do formantu niestandardowego  
 Wykazać, że formant niestandardowy kod działa w czasie projektowania, możesz dodać właściwość i ustaw punkt przerwania w kodzie, który implementuje właściwości.  
  
#### <a name="to-add-a-property-to-your-custom-control"></a>Aby dodać właściwość do formantu niestandardowego  
  
1.  Otwórz **DebugControl** w **edytora kodu**. Dodaj następujący kod do definicji klasy:  
  
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
  
## <a name="adding-your-custom-control-to-the-host-form"></a>Dodawanie formantu niestandardowego do formularza hosta  
 Aby debugować zachowania czasu projektowania formantu niestandardowego, zostaną umieszczone wystąpienia klasy kontrolki niestandardowej w formularzu hosta.  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a>Aby dodać formantu niestandardowego do formularza hosta  
  
1.  W projekcie "DebuggingExample" otworzyć Form1 w **Projektant formularzy systemu Windows**.  
  
2.  W **przybornika**, otwórz **składniki DebugControlLibrary** karcie i przeciągnij **DebugControl** wystąpienia na formularzu.  
  
3.  Znajdź `DemoString` właściwość niestandardową **właściwości** okna. Należy pamiętać, można zmienić jego wartość, jak w przypadku innych właściwości. Należy również zauważyć, że w przypadku `DemoString` właściwość jest wybrana, ciąg opisu właściwości wyświetlane w dolnej części **właściwości** okna.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Konfigurowanie projektu debugowanie w czasie projektowania  
 Aby debugować zachowanie czasu projektowania formantu niestandardowego, będzie debugowania osobnego wystąpienia programu Visual Studio, która działa formantu niestandardowego kodu.  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Aby skonfigurować projekt dla debugowanie w czasie projektowania  
  
1.  Kliknij prawym przyciskiem myszy **DebugControlLibrary** projektu w **Eksploratora rozwiązań** i wybierz **właściwości**.  
  
2.  W **DebugControlLibrary** arkusza właściwości, wybierz opcję **debugowania** kartę.  
  
     W **Akcja uruchamiania** zaznacz **uruchomienia programu zewnętrznego**. Można więc debugowanie osobnego wystąpienia programu Visual Studio, kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby wyszukać środowiska IDE programu Visual Studio. Nazwa pliku wykonywalnego jest **devenv.exe**, a jeśli został zainstalowany w domyślnej lokalizacji ścieżki %programfiles%\Microsoft 9.0\Common7\IDE\devenv.exe programu Visual Studio.  
  
3.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
4.  Kliknij prawym przyciskiem myszy **DebugControlLibrary** projekt i wybierz **Ustaw jako projekt startowy** umożliwiające tej konfiguracji debugowania.  
  
## <a name="debugging-your-custom-control-at-design-time"></a>Debugowanie formantu niestandardowego w czasie projektowania  
 Teraz można przystąpić do debugowania formantu niestandardowego, jak działa w trybie projektowania. Po ponownym uruchomieniu sesji debugowania, zostanie utworzone nowe wystąpienie programu Visual Studio i użyje do załadowania rozwiązania "DebuggingExample". Po otwarciu Form1 w **Projektant formularzy**, wystąpienie formantu niestandardowego zostanie utworzona oraz zostanie uruchomione.  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a>Aby debugować niestandardowego formantu w czasie projektowania  
  
1.  Otwórz **DebugControl** pliku źródłowego w **edytora kodu** i umieść punkt przerwania na `Set` akcesor `DemoString` właściwości.  
  
2.  Naciśnij klawisz F5, aby rozpocząć sesję debugowania. Należy pamiętać, że utworzono nowe wystąpienie programu Visual Studio. Można rozróżnić wystąpień na dwa sposoby:  
  
    -   Wystąpienie debugowania ma wyraz **systemem** na pasku tytułu  
  
    -   Wystąpienie debugowania ma **Start** znajdującego się na jego **debugowania** narzędzi wyłączone  
  
     Punkt przerwania jest ustawiony w przypadku debugowania.  
  
3.  W tym nowym wystąpieniu programu Visual Studio Otwórz rozwiązanie "DebuggingExample". Można łatwo znaleźć rozwiązania, wybierając **ostatnich projektów** z **pliku** menu. Plik rozwiązania "DebuggingExample.sln" zostaną wyświetlone jako ostatnio używanych plików.  
  
4.  Otwórz Form1 w **Projektant formularzy** i wybierz **DebugControl** formantu.  
  
5.  Zmień wartość `DemoString` właściwości. Zauważ, że po zatwierdzeniu zmian debugowania wystąpienie programu Visual Studio uzyskuje fokus i wykonywania zatrzymuje się na punkt przerwania. Można pojedynczy krok za pomocą metody dostępu właściwości równie Twojej czy innego kodu.  
  
6.  Po zakończeniu sesję debugowania można zamknąć odrzucając hostowanej wystąpienie programu Visual Studio lub klikając **Zatrzymaj debugowanie** przycisk w przypadku debugowania.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, aby umożliwić debugowanie niestandardowych formantów w czasie projektowania, istnieje wiele możliwości rozszerzania formantu interakcji z programu Visual Studio IDE.  
  
-   Można użyć <xref:System.ComponentModel.Component.DesignMode%2A> właściwość <xref:System.ComponentModel.Component> klasy do kodu zapisu, które zostaną wykonane tylko w czasie projektowania. Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.Component.DesignMode%2A>.  
  
-   Istnieje kilka atrybutów można zastosować do właściwości formantu do manipulowania interakcji kontrolki niestandardowej przy użyciu projektanta. Można znaleźć tych atrybutów w <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw.  
  
-   Można pisać niestandardowe projektanta dla formantu niestandardowego. Umożliwia pełną kontrolę nad środowiskiem projektu przy użyciu extensible infrastruktury projektanta udostępnianych przez program Visual Studio. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie funkcje systemu Windows formularze kontroli czy ma korzystać z programu Visual Studio czasu projektowania](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [Porady: uzyskiwanie dostępu do usług w czasie projektowania](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [Porady: dostęp do obsługi w formularzach systemu Windows w czasie projektowania](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
