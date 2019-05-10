---
title: 'Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 876de650f9c182c0f82a02d1c5b356faa4f7f118
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211160"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi

Jeśli składniki są zdefiniowane w projekcie w aktualnie otwarte rozwiązanie, zostanie automatycznie wyświetlona w **przybornika**, za pomocą trzeba wykonywać żadnych czynności przez użytkownika. Możesz również ręcznie wypełnić **przybornika** za pomocą składników niestandardowych za pomocą [wybierz przybornika dialogowego elementy (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100)), ale **przybornika** uwzględnia elementy w Twoim rozwiązaniu kompilacji danych wyjściowych o następującej charakterystyce:

- Implementuje <xref:System.ComponentModel.IComponent>;

- Nie ma <xref:System.ComponentModel.ToolboxItemAttribute> równa `false`;

- Nie ma <xref:System.ComponentModel.DesignTimeVisibleAttribute> równa `false`.

> [!NOTE]
> **Przybornika** nie jest zgodna z łańcuchów odwołania, dzięki czemu nie będzie ona wyświetlana elementy, które nie są kompilowane przez projekt w rozwiązaniu.

W tym instruktażu pokazano, jak niestandardowy składnik jest automatycznie odzwierciedlana w **przybornika** Po skompilowaniu składnika. Zadania zilustrowane w tym przewodniku obejmują:

- Tworzenie projektu Windows Forms.

- Tworzenie niestandardowych składników.

- Tworzenie wystąpienia składnika niestandardowego.

- Zwalnianie i ponowne załadowanie niestandardowych składników.

Gdy to zrobisz, zostanie wyświetlony **przybornika** jest wypełniana przy użyciu składnika, który został utworzony.

## <a name="create-the-project"></a>Utwórz projekt

1. W programie Visual Studio Utwórz projekt aplikacji systemu Windows o nazwie `ToolboxExample` (**pliku** > **New** > **projektu**  >  **Visual C#**  lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms Aplikacja**).

2. Dodaj nowy składnik do projektu. Wywołaj go `DemoComponent`.

     Aby uzyskać więcej informacji, zobacz [jak: Dodaj nowe elementy projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).

3. Skompiluj projekt.

4. Z **narzędzia** menu, kliknij przycisk **opcje** elementu. Kliknij przycisk **ogólne** w obszarze **Windows Forms Designer** element i upewnij się, że **AutoToolboxPopulate** ustawiono opcję **True**.

## <a name="create-an-instance-of-a-custom-component"></a>Utwórz wystąpienie obiektu niestandardowych składników

Następnym krokiem jest do utworzenia wystąpienia składnika niestandardowego w formularzu. Ponieważ **przybornika** automatycznie kont dla nowego składnika, jest to tak proste, jak tworzenie innych składnika lub kontrolki.

1. Otwieranie formularza projektu w **projektanta formularzy**.

2. W **przybornika**, kliknij przycisk Nowa karta o nazwie **składniki ToolboxExample**.

     Po kliknięciu karty, zostanie wyświetlony **DemoComponent**.

    > [!NOTE]
    > Ze względu na wydajność składników w obszarze automatycznie wypełniony **przybornika** niestandardowych map bitowych, nie są wyświetlane i <xref:System.Drawing.ToolboxBitmapAttribute> nie jest obsługiwane. Aby wyświetlić ikonę do składnika niestandardowego w **przybornika**, użyj **wybierz elementy przybornika** okno dialogowe, aby załadować składnika.

3. Przeciągnij składnik do formularza.

     Wystąpienia składnika, zostanie utworzony i dodany do **zasobniku składnika**.

## <a name="unload-and-reload-a-custom-component"></a>Zwolnij i ponownie załaduj niestandardowych składników

**Przybornika** uwzględnia składników w każdym ładowania projektu oraz gdy projekt jest zwalniana, powoduje usunięcie odwołania do składników projektów.

1. Zwolnij projekt z rozwiązania.

     Aby uzyskać więcej informacji na temat zwalniając projekty, zobacz [jak: Zwolnij i ponownie Załaduj projekty](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100)). Jeśli zostanie wyświetlony monit, aby zapisać, wybierz opcję **tak**.

2. Dodaj nową **aplikacji Windows** projektu do rozwiązania. Otwórz formularz w **projektanta**.

     **Składniki ToolboxExample** kartę z poprzednim projektu jest teraz usunięte.

3. Załaduj ponownie `ToolboxExample` projektu.

     **Składniki ToolboxExample** karcie teraz będzie pojawiać się ponownie.

## <a name="next-steps"></a>Następne kroki

Ten przewodnik pokazuje, że **przybornika** bierze pod uwagę elementów projektu, ale **przybornika** jest również uwzględnia kontrolki. Poeksperymentuj z Kontrolki niestandardowe, dodając i usuwając kontroli projektów w rozwiązaniu.

## <a name="see-also"></a>Zobacz także

- [Ogólne, Windows Forms Designer, okno dialogowe Opcje](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))
- [Instrukcje: Manipulowanie karty przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))
- [Wybierz elementy przybornika, okno dialogowe (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [Umieszczanie kontrolek na formularzach Windows Forms](putting-controls-on-windows-forms.md)
