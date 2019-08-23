---
title: Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
ms.openlocfilehash: c05e849705f851b51a362d3a1d1d3f81a9eaf0e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923597"
---
# <a name="troubleshooting-control-and-component-authoring"></a>Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów
W tym temacie wymieniono następujące typowe problemy występujące podczas opracowywania składników i kontrolek. Aby uzyskać więcej informacji, zobacz [programowanie ze składnikami](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
- Nie można dodać kontrolki do przybornika  
  
- Nie można debugować kontrolki użytkownika Windows Forms lub składnika  
  
- Zdarzenie jest zgłaszane dwa razy w dziedziczonej kontrolce lub składniku  
  
- Błąd czasu projektowania: "Nie można utworzyć składnika"*Nazwa składnika*""  
  
- STAThreadAttribute  
  
- Ikona składnika nie jest wyświetlana w przyborniku  
  
## <a name="cannot-add-control-to-toolbox"></a>Nie można dodać kontrolki do przybornika  
 Aby dodać kontrolkę niestandardową utworzoną w innym projekcie lub kontrolce innej firmy do przybornika, należy tozrobić ręcznie. Jeśli bieżący projekt zawiera kontrolkę lub składnik, powinien być automatycznie wyświetlany w **przyborniku** . Aby uzyskać więcej informacji, [zobacz Przewodnik: Automatyczne wypełnianie przybornika składnikami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)niestandardowymi.  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>Aby dodać kontrolkę do przybornika  
  
1. Kliknij prawym przyciskiem myszy **Przybornik** i z menu skrótów wybierz **polecenie Wybierz elementy**.  
  
2. W oknie dialogowym **Wybierz elementy przybornika** Dodaj składnik:  
  
    - Jeśli chcesz dodać składnik .NET Framework lub kontrolkę, kliknij kartę **składniki .NET Framework** .  
  
         — lub —  
  
    - Jeśli chcesz dodać składnik COM lub kontrolkę ActiveX, kliknij kartę **składniki com** .  
  
3. Jeśli formant znajduje się na liście w oknie dialogowym, potwierdź, że jest zaznaczone, a następnie kliknij przycisk **OK**.  
  
     Kontrolka zostanie dodana do **przybornika**.  
  
4. Jeśli formant nie znajduje się na liście w oknie dialogowym, wykonaj następujące czynności:  
  
    1. Kliknij przycisk **Przeglądaj** .  
  
    2. Przejdź do folderu, który zawiera plik. dll, który zawiera kontrolkę.  
  
    3. Wybierz plik. dll, a następnie kliknij przycisk **Otwórz**.  
  
         Kontrolka zostanie wyświetlona w oknie dialogowym.  
  
    4. Upewnij się, że formant jest zaznaczony, a następnie kliknij przycisk **OK**.  
  
         Kontrolka zostanie dodana do **przybornika**.  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Nie można debugować kontrolki użytkownika Windows Forms lub składnika  
 Jeśli formant pochodzi z <xref:System.Windows.Forms.UserControl> klasy, można debugować jego zachowanie w czasie wykonywania za pomocą kontenera testowego. Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.  
  
 Inne niestandardowe kontrolki i składniki nie są projektami autonomicznymi. Muszą one być hostowane przez aplikację, taką jak projekt Windows Forms. Aby debugować formant lub składnik, należy dodać go do projektu Windows Forms.  
  
#### <a name="to-debug-a-control-or-component"></a>Aby debugować formant lub składnik  
  
1. W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie** , aby skompilować rozwiązanie.  
  
2. Z menu **plik** wybierz polecenie **Dodaj**, a następnie **Nowy projekt** , aby dodać projekt testowy do aplikacji.  
  
3. W oknie dialogowym **Dodaj nowy projekt** wybierz pozycję **aplikacja systemu Windows** dla typu projektu.  
  
4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla nowego projektu. W menu skrótów kliknij pozycję **Dodaj odwołanie** , aby dodać odwołanie do projektu zawierającego formant lub składnik.  
  
5. Utwórz wystąpienie formantu lub składnika w projekcie testowym. Jeśli składnik znajduje się w **przyborniku**, możesz go przeciągnąć na powierzchnię projektanta lub można utworzyć wystąpienie programowo, jak pokazano w poniższym przykładzie kodu.  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Teraz można debugować formant lub składnik w zwykły sposób.  
  
 Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) i [Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)projektowania.  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>Zdarzenie jest zgłaszane dwa razy w dziedziczonej kontrolce lub składniku  
 Prawdopodobnie jest to spowodowane zduplikowaną `Handles` klauzulą. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>Błąd czasu projektowania: "Nie można utworzyć składnika" Nazwa składnika ""  
 Składnik lub formant muszą dostarczać Konstruktor bez parametrów z parametrami. Gdy środowisko projektowe tworzy wystąpienie składnika lub formantu, nie podejmuje próby dostarczenia żadnych parametrów do przeciążenia konstruktorów przyjmujących parametry.  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 <xref:System.STAThreadAttribute> Informuje o tym, że środowisko uruchomieniowe języka wspólnego (CLR), które Windows Forms używa modelu apartamentu jednowątkowego. Możesz zauważyć niezamierzone zachowanie, jeśli nie zastosujesz tego atrybutu do `Main` metody aplikacji Windows Forms. Na przykład obrazy tła mogą nie być wyświetlane dla kontrolek <xref:System.Windows.Forms.ListView>takich jak. Niektóre kontrolki mogą również wymagać tego atrybutu w celu poprawnego autouzupełniania oraz zachowania przeciągania i upuszczania.  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>Ikona składnika nie jest wyświetlana w przyborniku  
 Gdy używasz <xref:System.Drawing.ToolboxBitmapAttribute> do kojarzenia ikony ze składnikiem niestandardowym, mapa bitowa nie jest wyświetlana w przyborniku dla automatycznie generowanych składników. Aby wyświetlić mapę bitową, Załaduj ponownie formant przy użyciu okna dialogowego **Wybierz elementy przybornika** . Aby uzyskać więcej informacji, zobacz [jak: Udostępnianie mapy bitowej przybornika dla kontrolki](how-to-provide-a-toolbox-bitmap-for-a-control.md).  
  
## <a name="see-also"></a>Zobacz także

- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Instrukcje: Testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Przewodnik: Debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- [Tworzenie składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))
- [Rozwiązywanie problemów związanych z projektowaniem czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
