---
title: 'Instrukcje: Tworzenie działania'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 48df9b90a92468858bd3ac5498bd83fd0d57fe75
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315143"
---
# <a name="how-to-create-an-activity"></a>Instrukcje: Tworzenie działania

Działania są jednostki podstawowe zachowanie w [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Logika wykonania działania, które można zaimplementować w kodzie zarządzanym lub można ją wdrożyć za pomocą innych działań. W tym temacie pokazano, jak utworzyć dwóch działań. Pierwsze działanie jest proste działania, które używa kodu, aby zaimplementować logikę jego wykonywania. Implementacja drugiego działania jest zdefiniowana za pomocą innych działań. Te działania są używane w kolejnych krokach samouczka.

> [!NOTE]
> Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="create-the-activity-library-project"></a>Utwórz projekt biblioteki działań

1. Otwórz program Visual Studio i wybierz polecenie **New** > **projektu** z **pliku** menu.

2. W **nowy projekt** okna dialogowego, w obszarze **zainstalowane** kategorii, wybierz opcję **Visual C#** > **przepływu pracy** (lub **Języka Visual Basic** > **przepływu pracy**).

    > [!NOTE]
    > Jeśli nie widzisz **przepływu pracy** kategorii szablonu, użytkownik może być konieczne zainstalowanie **Windows Workflow Foundation** składnika programu Visual Studio. Wybierz **Otwórz Instalator programu Visual Studio** linku w lewej części **nowy projekt** okna dialogowego. Instalator programu Visual Studio wybierz **poszczególne składniki** kartę. Następnie w obszarze **działań programistycznych** kategorii, wybierz opcję **Windows Workflow Foundation** składnika. Wybierz **Modyfikuj** do instalacji składnika należy.

3. Wybierz **Biblioteka działań** szablonu projektu. Typ `NumberGuessWorkflowActivities` w **nazwa** pole, a następnie kliknij przycisk **OK**.

4. Kliknij prawym przyciskiem myszy **Activity1.xaml** w **Eksploratora rozwiązań** i wybierz polecenie **Usuń**. Kliknij przycisk **OK** o potwierdzenie.

## <a name="create-the-readint-activity"></a>Utwórz działanie readint —

1. Wybierz **Dodaj nowy element** z **projektu** menu.

2. W **zainstalowane** > **wspólne elementy** węzeł **przepływu pracy**. Wybierz **działanie kodu** z **przepływu pracy** listy.

3. Typ `ReadInt` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.

4. Zastąp istniejące `ReadInt` definicji przy użyciu następującej definicji.

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > `ReadInt` Pochodzi od klasy działania <xref:System.Activities.NativeActivity%601> zamiast <xref:System.Activities.CodeActivity>, co jest ustawieniem domyślnym dla szablonu działania kodu. <xref:System.Activities.CodeActivity%601> można użyć, jeśli działanie zapewnia pojedynczy wynik, która jest dostępna za pośrednictwem <xref:System.Activities.Activity%601.Result%2A> argument, ale <xref:System.Activities.CodeActivity%601> nie obsługuje korzystanie z zakładek, więc <xref:System.Activities.NativeActivity%601> jest używany.

## <a name="create-the-prompt-activity"></a>Utwórz działanie monitu

1. Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania projektu. Kompilowanie projektu zapewniającą `ReadInt` działania w tym projekcie ma być używany do tworzenia niestandardowych działań w tym kroku.

2. Wybierz **Dodaj nowy element** z **projektu** menu.

3. W **zainstalowane** > **wspólne elementy** węzeł **przepływu pracy**. Wybierz **działania** z **przepływu pracy** listy.

4. Typ `Prompt` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.

5. Kliknij dwukrotnie **Prompt.xaml** w **Eksploratora rozwiązań** do wyświetlenia w projektancie, jeśli nie jest już wyświetlany.

6. Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działania, aby wyświetlić **argumenty** okienka.

7. Kliknij przycisk **utworzenia argumentu**.

8. Typ `BookmarkName` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie klawisz **Enter** można zapisać argumentu.

9. Kliknij przycisk **utworzenia argumentu**.

10. Typ `Result` do **nazwa** pole, znajdujący się pod nowo dodanym `BookmarkName` argument, wybierz opcję **się** z **kierunek** listy rozwijanej wybierz **Int32** z **typ argumentu** listy rozwijanej, a następnie klawisz **Enter**.

11. Kliknij przycisk **utworzenia argumentu**.

12. Typ `Text` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie klawisz **Enter** można zapisać argumentu.

     Te trzy argumenty są powiązane z argumentami odpowiedniego <xref:System.Activities.Statements.WriteLine> i `ReadInt` działań, które są dodawane do `Prompt` działania w poniższych krokach.

13. Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.

14. Przeciągnij **sekwencji** działanie z **przepływ sterowania** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety **Monitu** projektanta działań.

    > [!TIP]
    > Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.

15. Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety **Sekwencji** działania.

16. Powiązanie **tekstu** argument **WriteLine** działanie **tekstu** argument **monitu** działania, wpisując `Text` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole w **właściwości** okna, a następnie naciśnij klawisz **kartę** klucz dwa razy. Zamknięte okno technologii IntelliSense lista elementów członkowskich i zapisuje wartości właściwości, przenosząc wyboru Wyłącz właściwości. Można również ustawić tę właściwość, wpisując `Text` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole je.

    > [!TIP]
    > Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.

17. Przeciągnij **readint —** działanie z **NumberGuessWorkflowActivities** części **przybornika** i upuść je **sekwencji** działanie, tak że następuje **WriteLine** działania.

18. Powiąż **Nazwa_zakładki** argument **readint —** działanie **Nazwa_zakładki** argument **monitu** działania, wpisując `BookmarkName` do **wprowadź wyrażenie VB** pole po prawej stronie **Nazwa_zakładki** argument **okno właściwości**, a następnie naciśnij klawisz **Kartę** dwa razy, aby zamknąć okno technologii IntelliSense listy elementów członkowskich, a następnie Zapisz właściwość klucza.

19. Powiązanie **wynik** argument **readint —** działanie **wynik** argument **monitu** działania, wpisując `Result` do **wprowadź wyrażenie VB** pole po prawej stronie **wynik** argument **okno właściwości**, a następnie naciśnij klawisz **kartę** klucza dwa razy.

20. Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania rozwiązania.

## <a name="next-steps"></a>Następne kroki

Instrukcje dotyczące sposobu tworzenia przepływu pracy przy użyciu tych działań można znaleźć następnego kroku w tym samouczku [jak: Tworzenie przepływu pracy](how-to-create-a-workflow.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [Projektowanie i implementowanie niestandardowych działań](designing-and-implementing-custom-activities.md)
- [Wprowadzenie — samouczek](getting-started-tutorial.md)
- [Instrukcje: Tworzenie przepływu pracy](how-to-create-a-workflow.md)
- [Używanie elementu ExpressionTextBox w projektancie działań niestandardowych](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)