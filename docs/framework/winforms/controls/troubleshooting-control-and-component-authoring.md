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
ms.openlocfilehash: 9f284904fe9fec9ba423a8b9cd1e87457d768a2b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651604"
---
# <a name="troubleshooting-control-and-component-authoring"></a>Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów
Ten temat zawiera następujące typowe problemy, które występują podczas tworzenia składników i formantów. Aby uzyskać więcej informacji, zobacz [Programowanie przy użyciu składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).  
  
- Nie można dodać kontrolki do przybornika  
  
- Nie można debugować kontrolki użytkownika interfejsu Windows Forms lub składnika  
  
- Zdarzenie jest zgłaszane w dwukrotnie odziedziczoną kontrolkę lub składnika  
  
- Błąd w czasie projektowania: "Nie można utworzyć składnika"*nazwa składnika*""  
  
- STAThreadAttribute  
  
- Ikona składnika nie jest wyświetlana w przyborniku  
  
## <a name="cannot-add-control-to-toolbox"></a>Nie można dodać kontrolki do przybornika  
 Jeśli chcesz dodać formant niestandardowy, który został utworzony w innym projekcie lub kontrolki z innych firm **przybornika**, należy to zrobić ręcznie. Jeśli bieżący projekt zawiera kontrolki lub składnika, powinien pojawić się w **przybornika** automatycznie. Aby uzyskać więcej informacji, zobacz [instruktażu: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>Aby dodać formant do przybornika  
  
1. Kliknij prawym przyciskiem myszy **przybornika** z menu skrótów wybierz **wybierz elementy**.  
  
2. W **wybierz elementy przybornika** okna dialogowego Dodaj składnik:  
  
    - Jeśli chcesz dodać do składnik .NET Framework lub formantu, kliknij przycisk **składników .NET Framework** kartę.  
  
         — lub —  
  
    - Aby dodać składnik COM lub formantu ActiveX, kliknij przycisk **składników COM** kartę.  
  
3. Jeśli formant znajduje się w oknie dialogowym, upewnij się, jest zaznaczone, a następnie kliknij przycisk **OK**.  
  
     Formant jest dodawany do **przybornika**.  
  
4. Jeśli formant nie znajduje się w oknie dialogowym, wykonaj następujące czynności:  
  
    1. Kliknij przycisk **Przeglądaj** przycisku.  
  
    2. Przejdź do folderu, który zawiera plik .dll, który zawiera formant.  
  
    3. Wybierz plik .dll, a następnie kliknij przycisk **Otwórz**.  
  
         Formant zostanie wyświetlony w oknie dialogowym.  
  
    4. Upewnij się, czy formant jest zaznaczone, a następnie kliknij **OK**.  
  
         Formant jest dodawany do **przybornika**.  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Nie można debugować kontrolki użytkownika interfejsu Windows Forms lub składnika  
 Jeśli pochodzi od klasy formantu <xref:System.Windows.Forms.UserControl> klasy, można debugować jego zachowanie w czasie wykonywania za pomocą kontenera testu. Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Inne niestandardowe formanty i składniki nie są autonomiczne projektów. One muszą być obsługiwane przez aplikację, taki jak projekt Windows Forms. Aby debugować formant lub składnika, należy dodać go do projektu Windows Forms.  
  
#### <a name="to-debug-a-control-or-component"></a>Aby debugować formant lub składnika  
  
1. Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie** tworzenia rozwiązań.  
  
2. Z **pliku** menu, wybierz **Dodaj**, a następnie **nowy projekt** dodać projekt testowy do aplikacji.  
  
3. W **Dodaj nowy projekt** okno dialogowe Wybierz **aplikacji Windows** dla typu projektu.  
  
4. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł dla nowego projektu. W menu skrótów kliknij **Dodaj odwołanie** można dodać odwołania do projektu zawierającego kontrola lub składników.  
  
5. Utwórz wystąpienie składnika lub kontrolki w projekcie testowym. Jeśli składnik jest w **przybornika**, a następnie przeciągnij go do Twojego powierzchni projektanta lub można utworzyć wystąpienia programistycznie, jak pokazano w poniższym przykładzie kodu.  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Można teraz debugować swoje kontroli lub składnika w zwykły sposób w całym dokumencie.  
  
 Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) i [instruktażu: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>Zdarzenie jest zgłaszane w dwukrotnie odziedziczoną kontrolkę lub składnika  
 Jest to prawdopodobnie spowodowane zduplikowane `Handles` klauzuli. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dziedziczone procedury obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>Błąd w czasie projektowania: "Nie można utworzyć składnika"Nazwa składnika""  
 Składnik lub kontrolki, należy podać domyślnego konstruktora bez parametrów. Gdy środowisko projektowania tworzy wystąpienie składnika lub kontrolki, nie próbuje zapewniają żadnych parametrów do przeciążenia konstruktora, które przyjmują parametry.  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 <xref:System.STAThreadAttribute> Informuje środowisko uruchomieniowe języka wspólnego (CLR), Windows Forms korzysta z modelu apartamentem jednowątkowym. Możesz zauważyć niezamierzone zachowanie, jeśli ten atrybut nie są stosowane do aplikacji Windows Forms `Main` metody. Na przykład obrazy tła mogą być niewidoczne dla kontrolki, takie jak <xref:System.Windows.Forms.ListView>. Niektóre kontrolki mogą także wymagać tego atrybutu poprawne Autouzupełnianie i zachowanie przeciągnij i upuść.  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>Ikona składnika nie jest wyświetlana w przyborniku  
 Kiedy używasz <xref:System.Drawing.ToolboxBitmapAttribute> zostać skojarzona ikona za pomocą składnika niestandardowego, mapa bitowa nie ma w przyborniku dla składników wygenerowany automatycznie. Aby wyświetlić mapę bitową, należy ponownie załadować formantu za pomocą **wybierz elementy przybornika** okno dialogowe. Aby uzyskać więcej informacji, zobacz [jak: Dostarczanie mapy bitowej przybornika dla formantu](how-to-provide-a-toolbox-bitmap-for-a-control.md).  
  
## <a name="see-also"></a>Zobacz także

- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Instrukcje: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Przewodnik: Debugowanie Windows niestandardowych formantów formularzy w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- [Tworzenie składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))
- [Rozwiązywanie problemów podczas projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
