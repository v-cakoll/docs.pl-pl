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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9ee9df41e6f0a4e37164760a2e40740e31530121
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459074"
---
# <a name="troubleshoot-control-and-component-authoring"></a>Rozwiązywanie problemów z tworzeniem kontrolek i składników

W tym temacie wymieniono następujące typowe problemy związane z tworzeniem składników i kontrolek:

- Nie można dodać kontrolki do przybornika

- Nie można debugować kontrolki użytkownika Windows Forms lub składnika

- Zdarzenie jest zgłaszane dwa razy w dziedziczonej kontrolce lub składniku

- Błąd czasu projektowania: "nie można utworzyć składnika"*Nazwa składnika*""

- STAThreadAttribute

- Ikona składnika nie jest wyświetlana w przyborniku

## <a name="cannot-add-control-to-toolbox"></a>Nie można dodać kontrolki do przybornika

Aby dodać kontrolkę niestandardową utworzoną w innym projekcie lub kontrolce innej firmy do **przybornika**, należy to zrobić ręcznie. Jeśli bieżący projekt zawiera kontrolkę lub składnik, powinien być automatycznie wyświetlany w **przyborniku** . Aby uzyskać więcej informacji, zobacz [Przewodnik: automatyczne zapełnianie przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

### <a name="to-add-a-control-to-the-toolbox"></a>Aby dodać kontrolkę do przybornika

1. Kliknij prawym przyciskiem myszy **Przybornik** i z menu skrótów wybierz **polecenie Wybierz elementy**.

2. W oknie dialogowym **Wybierz elementy przybornika** Dodaj składnik:

    - Jeśli chcesz dodać składnik .NET Framework lub kontrolkę, kliknij kartę **składniki .NET Framework** .

         oraz

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

Jeśli formant pochodzi z klasy <xref:System.Windows.Forms.UserControl>, można debugować jego zachowanie w czasie wykonywania za pomocą kontenera testowego. Aby uzyskać więcej informacji, zobacz [jak: testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

Inne niestandardowe kontrolki i składniki nie są projektami autonomicznymi. Muszą one być hostowane przez aplikację, taką jak projekt Windows Forms. Aby debugować formant lub składnik, należy dodać go do projektu Windows Forms.

### <a name="to-debug-a-control-or-component"></a>Aby debugować formant lub składnik

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

Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowanie w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour) i [instruktaże: debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).

## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>Zdarzenie jest zgłaszane dwa razy w dziedziczonej kontrolce lub składniku

Prawdopodobnie jest to spowodowane zduplikowaną klauzulą `Handles`. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).

## <a name="design-time-error-failed-to-create-component-component-name"></a>Błąd czasu projektowania: "nie można utworzyć składnika" Nazwa składnika ""

Składnik lub formant muszą dostarczać Konstruktor bez parametrów z parametrami. Gdy środowisko projektowe tworzy wystąpienie składnika lub formantu, nie podejmuje próby dostarczenia żadnych parametrów do przeciążenia konstruktorów przyjmujących parametry.

## <a name="stathreadattribute"></a>STAThreadAttribute

<xref:System.STAThreadAttribute> informuje środowisko uruchomieniowe języka wspólnego (CLR), które Windows Forms używa modelu apartamentu jednowątkowego. Możesz zauważyć niezamierzone zachowanie, jeśli nie zastosujesz tego atrybutu do metody `Main` Windows Forms aplikacji. Na przykład obrazy tła mogą nie być wyświetlane dla kontrolek takich jak <xref:System.Windows.Forms.ListView>. Niektóre kontrolki mogą również wymagać tego atrybutu w celu poprawnego autouzupełniania oraz zachowania przeciągania i upuszczania.

## <a name="component-icon-does-not-appear-in-toolbox"></a>Ikona składnika nie jest wyświetlana w przyborniku

Gdy używasz <xref:System.Drawing.ToolboxBitmapAttribute> do skojarzenia ikony ze składnikiem niestandardowym, mapa bitowa nie jest wyświetlana w przyborniku dla automatycznie generowanych składników. Aby wyświetlić mapę bitową, Załaduj ponownie formant przy użyciu okna dialogowego **Wybierz elementy przybornika** . Aby uzyskać więcej informacji, zobacz [How to: dostarczanie mapy bitowej przybornika dla kontrolki](how-to-provide-a-toolbox-bitmap-for-a-control.md).

## <a name="see-also"></a>Zobacz także

- [Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
- [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Instrukcje: testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Przewodnik: debugowanie niestandardowych kontrolek formularzy Windows Forms w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
