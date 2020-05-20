---
title: 'Instrukcje: Tworzenie działania'
description: 'W tym artykule opisano sposób tworzenia dwóch działań w programie Workflow Foundation: jeden, który używa kodu do implementowania logiki i jednego zdefiniowanego przy użyciu innych działań.'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: dae099d102b0c85d09a1ef8bcce56e8a9096bd20
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419593"
---
# <a name="how-to-create-an-activity"></a>Instrukcje: Tworzenie działania

Działania są podstawową jednostką zachowania w programie [!INCLUDE[wf1](../../../includes/wf1-md.md)] . Logikę wykonywania działania można zaimplementować w kodzie zarządzanym lub można ją zaimplementować przy użyciu innych działań. W tym temacie przedstawiono sposób tworzenia dwóch działań. Pierwsze działanie to proste działanie, które używa kodu do zaimplementowania logiki wykonywania. Implementacja drugiego działania jest definiowana przy użyciu innych działań. Te działania są używane w następujących krokach w samouczku.

> [!NOTE]
> Aby pobrać kompletną wersję samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="create-the-activity-library-project"></a>Utwórz projekt biblioteki działań

1. Otwórz program Visual Studio i wybierz pozycję **Nowy**  >  **projekt** z menu **plik** .

2. W oknie dialogowym **Nowy projekt** w obszarze **zainstalowana** Kategoria wybierz pozycję przepływ pracy w **języku Visual C#**  >  **Workflow** (lub **Visual Basic**  >  **przepływ pracy**).

    > [!NOTE]
    > Jeśli nie widzisz kategorii szablonów **przepływu pracy** , może być konieczne zainstalowanie składnika **Windows Workflow Foundation** programu Visual Studio. Wybierz łącze **otwórz Instalator programu Visual Studio** po lewej stronie okna dialogowego **Nowy projekt** . W Instalator programu Visual Studio wybierz kartę **poszczególne składniki** . Następnie w kategorii **działania deweloperskie** wybierz składnik **Windows Workflow Foundation** . Wybierz pozycję **Modyfikuj** , aby zainstalować składnik.

3. Wybierz szablon projektu **Biblioteka działań** . Wpisz `NumberGuessWorkflowActivities` w polu **Nazwa** , a następnie kliknij przycisk **OK**.

4. Kliknij prawym przyciskiem myszy **zakończeniu. XAML** w **Eksplorator rozwiązań** i wybierz polecenie **Usuń**. Kliknij przycisk **OK** , aby potwierdzić.

## <a name="create-the-readint-activity"></a>Tworzenie działania ReadInt

1. Wybierz pozycję **Dodaj nowy element** z menu **projekt** .

2. W węźle **zainstalowane**  >  **elementy wspólne** wybierz pozycję **przepływ pracy**. Wybierz **działanie Code** z listy **przepływów pracy** .

3. Wpisz tekst `ReadInt` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.

4. Zastąp istniejącą `ReadInt` definicję następującą definicją.

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > `ReadInt`Działanie pochodzi od <xref:System.Activities.NativeActivity%601> zamiast <xref:System.Activities.CodeActivity> , czyli domyślnego dla szablonu działania kodu. <xref:System.Activities.CodeActivity%601>może być używany, jeśli działanie zawiera pojedynczy wynik, który jest udostępniany przez <xref:System.Activities.Activity%601.Result%2A> argument, ale nie <xref:System.Activities.CodeActivity%601> obsługuje użycia zakładek, więc <xref:System.Activities.NativeActivity%601> jest używany.

## <a name="create-the-prompt-activity"></a>Utwórz działanie monitu

1. Naciśnij **klawisze CTRL** + **SHIFT** + **B** , aby skompilować projekt. Kompilowanie projektu umożliwia `ReadInt` działanie w tym projekcie do użycia w celu utworzenia niestandardowego działania z tego kroku.

2. Wybierz pozycję **Dodaj nowy element** z menu **projekt** .

3. W węźle **zainstalowane**  >  **elementy wspólne** wybierz pozycję **przepływ pracy**. Wybierz **działanie** z listy **przepływów pracy** .

4. Wpisz tekst `Prompt` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.

5. Kliknij dwukrotnie pozycję **Prompt. XAML** w **Eksplorator rozwiązań** , aby wyświetlić ją w projektancie, jeśli nie jest jeszcze wyświetlana.

6. Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby wyświetlić okienko **argumenty** .

7. Kliknij przycisk **Utwórz argument**.

8. Wpisz tekst w `BookmarkName` polu **Nazwa** , wybierz **pozycję z** listy rozwijanej **kierunek** , wybierz pozycję **ciąg** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz **Enter** , aby zapisać argument.

9. Kliknij przycisk **Utwórz argument**.

10. Wpisz `Result` w polu **Nazwa** , który znajduje się pod nowo dodanym `BookmarkName` argumentem **Out** , wybierz pozycję z listy rozwijanej **kierunek** , wybierz pozycję **Int32** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz **Enter**.

11. Kliknij przycisk **Utwórz argument**.

12. Wpisz tekst w `Text` polu **Nazwa** , wybierz **pozycję z** listy rozwijanej **kierunek** , wybierz pozycję **ciąg** z listy rozwijanej **Typ argumentu** , a następnie naciśnij klawisz **Enter** , aby zapisać argument.

     Te trzy argumenty są powiązane z odpowiednimi argumentami <xref:System.Activities.Statements.WriteLine> i `ReadInt` działaniami, które są dodawane do `Prompt` działania w poniższych krokach.

13. Kliknij pozycję **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć okienko **argumenty** .

14. Przeciągnij aktywność **sekwencji** z sekcji **przepływ sterowania** w **przyborniku** i upuść ją na **działanie upuść w tym miejscu** w projektancie działań **monitu** .

    > [!TIP]
    > Jeśli okno **Przybornik** nie jest wyświetlane, wybierz pozycję **Przybornik** z menu **Widok** .

15. Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** w **przyborniku** i upuść je na **działanie Drop tutaj** etykieta działania **sekwencji** .

16. Powiąż argument **Text** działania **WriteLine** z argumentem **Text** działania **Prompt** , wpisując w polu `Text` **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** w oknie **Właściwości** , a następnie naciśnij klawisz **Tab** dwa razy. Spowoduje to odrzucenie okna członków listy IntelliSense i zapisanie wartości właściwości poprzez przeniesienie zaznaczenia poza właściwość. Tę właściwość można również ustawić, wpisując `Text` w polu **wprowadź wyrażenie języka C#** lub wprowadzając pole **wyrażenia VB** w samym działaniu.

    > [!TIP]
    > Jeśli **okno właściwości** nie jest wyświetlane, wybierz pozycję **okno właściwości** w menu **Widok** .

17. Przeciągnij działanie **ReadInt** z sekcji **NumberGuessWorkflowActivities** w **przyborniku** i upuść je w działaniu **sekwencji** , tak aby była zgodna z działaniem **WriteLine** .

18. Powiąż argument **BookmarkName** działania **ReadInt** z argumentem **BookmarkName** działania **Prompt** , wpisując w `BookmarkName` polu **wprowadź wyrażenie VB** z prawej strony argumentu **zakładkaname** w **oknie właściwości**, a następnie naciśnij klawisz **Tab** dwa razy, aby zamknąć okno członków listy IntelliSense i zapisać właściwość.

19. Powiązanie argumentu **wynik** działania **ReadInt** z argumentem **wynik** działania **monitu** , wpisując `Result` w polu **wprowadź wyrażenie VB** z prawej strony argumentu **wynik** w **oknie właściwości**, a następnie naciskając klawisz **Tab** dwa razy.

20. Naciśnij **klawisze CTRL** + **SHIFT** + **B** , aby skompilować rozwiązanie.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać instrukcje dotyczące sposobu tworzenia przepływu pracy przy użyciu tych działań, zobacz następny krok w samouczku [: tworzenie przepływu pracy](how-to-create-a-workflow.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [Projektowanie i implementowanie niestandardowych działań](designing-and-implementing-custom-activities.md)
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
- [Instrukcje: Tworzenie przepływu pracy](how-to-create-a-workflow.md)
- [Używanie elementu ExpressionTextBox w projektancie działań niestandardowych](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
