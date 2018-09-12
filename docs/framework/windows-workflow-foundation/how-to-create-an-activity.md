---
title: 'Porady: tworzenie działania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: deb1b6ca5c6fc996a015e32dd5e0c7b9bd6530fa
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699998"
---
# <a name="how-to-create-an-activity"></a>Porady: tworzenie działania
Działania są jednostki podstawowe zachowanie w [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Logika wykonania działania, które można zaimplementować w kodzie zarządzanym lub można ją wdrożyć za pomocą innych działań. W tym temacie pokazano, jak utworzyć dwóch działań. Pierwsze działanie jest proste działania, które używa kodu, aby zaimplementować logikę jego wykonywania. Implementacja drugiego działania jest zdefiniowana za pomocą innych działań. Te działania są używane w kolejnych krokach samouczka.  
  
> [!NOTE]
>  Aby pobrać pełną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-activity-library-project"></a>Aby utworzyć projekt biblioteki działań  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i wybierz polecenie **New**, **projektu** z **pliku** menu.  
  
2.  Rozwiń **inne typy projektów** w węźle **zainstalowane**, **szablony** listy i wybierz **Visual Studio Solutions**.  
  
3.  Wybierz **puste rozwiązanie** z **Visual Studio Solutions** listy. Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework. Typ `WF45GettingStartedTutorial` w **nazwa** pole, a następnie kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy projekt**.  
  
    > [!TIP]
    >  Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.  
  
5.  W **zainstalowane** węzeł **Visual C#**, **przepływu pracy** (lub **języka Visual Basic**, **przepływu pracy**). Upewnij się, że **.NET Framework 4.5** wybrano [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wersji listy rozwijanej. Wybierz **Biblioteka działań** z **przepływu pracy** listy. Typ `NumberGuessWorkflowActivities` w **nazwa** pole, a następnie kliknij przycisk **OK**.  
  
    > [!NOTE]
    >  Zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **języka Visual Basic** węzła może znajdować się w **inne języki** w węźle **zainstalowane** węzła.  
  
6.  Kliknij prawym przyciskiem myszy **Activity1.xaml** w **Eksploratora rozwiązań** i wybierz polecenie **Usuń**. Kliknij przycisk **OK** o potwierdzenie.  
  
### <a name="to-create-the-readint-activity"></a>Aby utworzyć działanie readint —  
  
1.  Wybierz **Dodaj nowy element** z **projektu** menu.  
  
2.  W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**. Wybierz **działanie kodu** z **przepływu pracy** listy.  
  
3.  Typ `ReadInt` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.  
  
4.  Zastąp istniejące `ReadInt` definicji przy użyciu następującej definicji.  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` Pochodzi od klasy działania <xref:System.Activities.NativeActivity%601> zamiast <xref:System.Activities.CodeActivity>, co jest ustawieniem domyślnym dla szablonu działania kodu. <xref:System.Activities.CodeActivity%601> można użyć, jeśli działanie zapewnia pojedynczy wynik, która jest dostępna za pośrednictwem <xref:System.Activities.Activity%601.Result%2A> argument, ale <xref:System.Activities.CodeActivity%601> nie obsługuje korzystanie z zakładek, więc <xref:System.Activities.NativeActivity%601> jest używany.  
  
### <a name="to-create-the-prompt-activity"></a>Aby utworzyć działanie monitu  
  
1.  Naciśnij kombinację klawiszy CTRL+SHIFT+B. Projekt zostanie skompilowany. Kompilowanie projektu zapewniającą `ReadInt` działania w tym projekcie ma być używany do tworzenia niestandardowych działań w tym kroku.  
  
2.  Wybierz **Dodaj nowy element** z **projektu** menu.  
  
3.  W **zainstalowane**, **wspólne elementy** węzeł **przepływu pracy**. Wybierz **działania** z **przepływu pracy** listy.  
  
4.  Typ `Prompt` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.  
  
5.  Kliknij dwukrotnie **Prompt.xaml** w **Eksploratora rozwiązań** do wyświetlenia w projektancie, jeśli nie jest już wyświetlany.  
  
6.  Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działania, aby wyświetlić **argumenty** okienka.  
  
7.  Kliknij przycisk **utworzenia argumentu**.  
  
8.  Typ `BookmarkName` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.  
  
9. Kliknij przycisk **utworzenia argumentu**.  
  
10. Typ `Result` do **nazwa** pole, znajdujący się pod nowo dodanym `BookmarkName` argument, wybierz opcję **się** z **kierunek** listy rozwijanej wybierz **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.  
  
11. Kliknij przycisk **utworzenia argumentu**.  
  
12. Typ `Text` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.  
  
     Te trzy argumenty są powiązane z argumentami odpowiedniego <xref:System.Activities.Statements.WriteLine> i `ReadInt` działań, które są dodawane do `Prompt` działania w poniższych krokach.  
  
13. Kliknij przycisk **argumenty** w lewym dolnym rogu projektanta działań, aby zamknąć **argumenty** okienka.  
  
14. Przeciągnij **sekwencji** działanie z **przepływ sterowania** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety **Monitu** projektanta działań.  
  
    > [!TIP]
    >  Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.  
  
15. Przeciągnij **WriteLine** działanie z **podstawowych** części **przybornika** i upuść je na **Upuść działanie tutaj** etykiety **Sekwencji** działania.  
  
16. Powiązanie **tekstu** argument **WriteLine** działanie **tekstu** argument **monitu** działania, wpisując `Text` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole w **właściwości** okna, a następnie naciśnij klawisz TAB klucza dwa razy. Zamknięte okno technologii IntelliSense lista elementów członkowskich i zapisuje wartości właściwości, przenosząc wyboru Wyłącz właściwości. Można również ustawić tę właściwość, wpisując `Text` do **wprowadź wyrażenie języka C#** lub **wprowadź wyrażenie VB** pole je.  
  
    > [!TIP]
    >  Jeśli **okno właściwości** nie jest wyświetlany, wybierz opcję **okno właściwości** z **widoku** menu.  
  
17. Przeciągnij **readint —** działanie z **NumberGuessWorkflowActivities** części **przybornika** i upuść je **sekwencji** działanie, tak że następuje **WriteLine** działania.  
  
18. Powiąż **Nazwa_zakładki** argument **readint —** działanie **Nazwa_zakładki** argument **monitu** działania, wpisując `BookmarkName` do **wprowadź wyrażenie VB** pole po prawej stronie **Nazwa_zakładki** argument **okno właściwości**, a następnie naciśnij klawisz TAB dwa czas, aby zamknąć okno technologii IntelliSense lista elementów członkowskich i zapisać właściwości.  
  
19. Powiązanie **wynik** argument **readint —** działanie **wynik** argument **monitu** działania, wpisując `Result` do **wprowadź wyrażenie VB** pole po prawej stronie **wynik** argument **okno właściwości**, a następnie naciśnij klawisz TAB dwa razy.  
  
20. Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
     Instrukcje dotyczące sposobu tworzenia przepływu pracy przy użyciu tych działań można znaleźć następnego kroku w tym samouczku [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [Projektowanie i implementowanie niestandardowych działań](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Instrukcje: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Używanie elementu ExpressionTextBox w projektancie działań niestandardowych](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
