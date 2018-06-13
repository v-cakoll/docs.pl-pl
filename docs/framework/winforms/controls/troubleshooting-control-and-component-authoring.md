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
ms.openlocfilehash: 9100d6dc41f982af340d747ad447009a183b3c7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540982"
---
# <a name="troubleshooting-control-and-component-authoring"></a>Rozwiązywanie problemów związanych z formantami oraz autoryzacją elementów
Ten temat zawiera następujące typowe problemy, które powstają podczas tworzenia składników i formantów. Aby uzyskać więcej informacji, zobacz [programowania ze składnikami](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
-   Nie można dodać formantu do przybornika  
  
-   Nie można debugować formantu użytkownika formularzy systemu Windows lub składnik  
  
-   Zdarzenie jest zgłaszane w dziedziczonej formant lub składnik  
  
-   Błąd w czasie projektowania: "nie można utworzyć składnika '*nazwa składnika*" "  
  
-   STAThreadAttribute  
  
-   Ikona składnika nie jest wyświetlana w przyborniku  
  
## <a name="cannot-add-control-to-toolbox"></a>Nie można dodać formantu do przybornika  
 Jeśli chcesz dodać kontrolkę niestandardową, który został utworzony w innym projekcie lub innych firm formantu **przybornika**, należy to zrobić ręcznie. Jeśli bieżący projekt zawiera formant lub składnik, powinny być wyświetlane w **przybornika** automatycznie. Aby uzyskać więcej informacji, zobacz [wskazówki: automatyczne zapełnianie przybornika składnikami niestandardowe](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>Aby dodać kontrolkę do przybornika  
  
1.  Kliknij prawym przyciskiem myszy **przybornika** z menu skrótów wybierz **wybierz elementy**.  
  
2.  W **wybierz elementy przybornika** okno dialogowe Dodaj składnik:  
  
    -   Jeśli chcesz dodać .NET Framework składnika lub kontrolki, kliknij przycisk **składników .NET Framework** kartę.  
  
         — lub —  
  
    -   Jeśli chcesz dodać składnik COM lub formantu ActiveX, kliknij przycisk **składniki COM** kartę.  
  
3.  Jeśli formant jest wyświetlana w oknie dialogowym, upewnij się, jest zaznaczone, a następnie kliknij przycisk **OK**.  
  
     Formant został dodany do **przybornika**.  
  
4.  Formant nie ma na liście w oknie dialogowym, wykonaj następujące czynności:  
  
    1.  Kliknij przycisk **Przeglądaj** przycisku.  
  
    2.  Przejdź do folderu, który zawiera plik .dll, który zawiera formantu.  
  
    3.  Wybierz plik dll, a następnie kliknij przycisk **Otwórz**.  
  
         W oknie dialogowym zostanie wyświetlona formantu.  
  
    4.  Upewnij się, czy formant jest zaznaczone, a następnie kliknij **OK**.  
  
         Formantu zostanie dodany do **przybornika**.  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Nie można debugować formantu użytkownika formularzy systemu Windows lub składnik  
 Jeśli pochodzi z klasy formantu <xref:System.Windows.Forms.UserControl> klasy, można debugować jego zachowania w czasie wykonywania pomocą kontenera testu. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
 Inne niestandardowe formanty i składniki nie są autonomicznych projektów. Muszą one obsługiwane przez aplikację, takich jak projektu formularzy systemu Windows. Aby debugować formant lub składnik, należy go dodać do projektu formularzy systemu Windows.  
  
#### <a name="to-debug-a-control-or-component"></a>Aby debugować formant lub składnik  
  
1.  Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie** tworzenia rozwiązań.  
  
2.  Z **pliku** menu, wybierz **Dodaj**, a następnie **nowy projekt** dodać projekt testowy do aplikacji.  
  
3.  W **Dodawanie nowego projektu** okno dialogowe Wybieranie **aplikacji systemu Windows** dla typu projektu.  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł dla nowego projektu. W menu skrótów kliknij **Dodaj odwołanie** można dodać odwołania do projektu zawierającego formant lub składnik.  
  
5.  Utwórz wystąpienie składnika lub formantu w projekcie testowym. Jeśli składnik jest w **przybornika**, przeciągnij go do Twojego powierzchni projektanta, lub można utworzyć wystąpienia programowo, jak pokazano w poniższym przykładzie kodu.  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     Możesz teraz debugować użytkownika formant lub składnik w zwykły sposób.  
  
 Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) i [wskazówki: debugowanie niestandardowych formantów formularzy systemu Windows w czasie projektowania](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>Zdarzenie jest zgłaszane w dziedziczonej formant lub składnik  
 Jest to prawdopodobnie z powodu zduplikowanego `Handles` klauzuli. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dziedziczone programów obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>Błąd w czasie projektowania: "nie można utworzyć składnika 'Nazwa składnika'"  
 Twoje składnika lub kontrolki musisz podać domyślnego konstruktora bez parametrów. W środowisku projektowania tworzy wystąpienie składnika lub kontrolki, nie jest podejmowana zapewnienie żadnych parametrów przeciążeń konstruktora, które przyjmują parametrów.  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 <xref:System.STAThreadAttribute> Środowisko uruchomieniowe języka wspólnego (CLR) informuje, że formularzy systemu Windows używa modelu jednowątkowego apartamentu. Jeśli ten atrybut nie stosować do aplikacji formularzy systemu Windows mogą pojawić się niezamierzone zachowanie `Main` metody. Na przykład obrazy tła mogą być niewidoczne dla formantów, takich jak <xref:System.Windows.Forms.ListView>. Niektóre kontrolki mogą także wymagać tego atrybutu do autouzupełniania poprawne i zachowanie przeciągania i upuszczania.  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>Ikona składnika nie jest wyświetlana w przyborniku  
 Jeśli używasz <xref:System.Drawing.ToolboxBitmapAttribute> zostać skojarzona ikona z składnik niestandardowy, mapy bitowej nie pojawia się w przyborniku składników wygenerowana automatycznie. Aby wyświetlić mapę bitową, należy ponownie załadować formantu przy użyciu **wybierz elementy przybornika** okno dialogowe. Aby uzyskać więcej informacji, zobacz [porady: Podaj mapy bitowej przybornika dla formantu](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Instrukcje: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [Przewodnik: debugowanie niestandardowych kontrolek formularzy Windows Forms w czasie projektowania](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [Tworzenie składników](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [Rozwiązywanie problemów z Programowanie w czasie projektowania](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Programowanie przy użyciu składników](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
