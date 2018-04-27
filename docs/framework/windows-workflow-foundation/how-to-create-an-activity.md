---
title: 'Porady: tworzenie działania'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: 39
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0d0d48d1e78efb3484f521958edf22d97ca8053d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-an-activity"></a>Porady: tworzenie działania
Działania są jednostki podstawowe zachowanie w [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Logiki wykonywania działania można zaimplementować w kodzie zarządzanym lub można ją wdrożyć za pomocą innych działań. W tym temacie przedstawiono sposób tworzenia dwóch działań. Pierwsze działanie jest proste działanie, które używa kod do implementacji logiki jego wykonywania. Do implementacji działania drugi jest definiowana za pomocą innych działań. Te działania są używane w następujących krokach samouczka.  
  
> [!NOTE]
>  Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-activity-library-project"></a>Aby utworzyć projekt z biblioteki działań  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i wybierz polecenie **nowy**, **projektu** z **pliku** menu.  
  
2.  Rozwiń węzeł **inne typy projektów** w węźle **zainstalowana**, **szablony** i wybraniu **rozwiązań programu Visual Studio**.  
  
3.  Wybierz **puste rozwiązanie** z **rozwiązań programu Visual Studio** listy. Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework. Typ `WF45GettingStartedTutorial` w **nazwa** a następnie kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy projekt**.  
  
    > [!TIP]
    >  Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.  
  
5.  W **zainstalowana** węzła, wybierz opcję **Visual C#**, **przepływu pracy** (lub **Visual Basic**, **przepływu pracy**). Upewnij się, że **.NET Framework 4.5** wybrano [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] wersja listy rozwijanej. Wybierz **Biblioteka działań** z **przepływu pracy** listy. Typ `NumberGuessWorkflowActivities` w **nazwa** a następnie kliknij przycisk **OK**.  
  
    > [!NOTE]
    >  W zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **Visual Basic** węzeł może być w obszarze **inne języki** w węźle **zainstalowana** węzła.  
  
6.  Kliknij prawym przyciskiem myszy **Activity1.xaml** w **Eksploratora rozwiązań** i wybierz polecenie **usunąć**. Kliknij przycisk **OK** o potwierdzenie.  
  
### <a name="to-create-the-readint-activity"></a>Aby utworzyć działanie ReadInt  
  
1.  Wybierz **Dodaj nowy element** z **projektu** menu.  
  
2.  W **zainstalowana**, **wspólne elementy** węzła, wybierz opcję **przepływu pracy**. Wybierz **działania związane z kodem** z **przepływu pracy** listy.  
  
3.  Typ `ReadInt` do **nazwa** a następnie kliknij przycisk **Dodaj**.  
  
4.  Zastąp istniejące `ReadInt` definicji z następującej definicji.  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` Działania jest pochodną <xref:System.Activities.NativeActivity%601> zamiast <xref:System.Activities.CodeActivity>, co jest ustawieniem domyślnym dla szablonu działania kodu. <xref:System.Activities.CodeActivity%601> można użyć, gdy działanie zawiera jeden wynik, który jest ujawniany przez <xref:System.Activities.Activity%601.Result%2A> argumentu, ale <xref:System.Activities.CodeActivity%601> nie obsługuje korzystanie z zakładek, więc <xref:System.Activities.NativeActivity%601> jest używany.  
  
### <a name="to-create-the-prompt-activity"></a>Aby utworzyć działanie monitu  
  
1.  Naciśnij kombinację klawiszy CTRL+SHIFT+B. Projekt zostanie skompilowany. Tworzenie projektu umożliwia `ReadInt` działania w tym projekcie ma być używany do tworzenia działań niestandardowych z tego kroku.  
  
2.  Wybierz **Dodaj nowy element** z **projektu** menu.  
  
3.  W **zainstalowana**, **wspólne elementy** węzła, wybierz opcję **przepływu pracy**. Wybierz **działania** z **przepływu pracy** listy.  
  
4.  Typ `Prompt` do **nazwa** a następnie kliknij przycisk **Dodaj**.  
  
5.  Kliknij dwukrotnie **Prompt.xaml** w **Eksploratora rozwiązań** do wyświetlenia w projektancie, jeśli nie jest już wyświetlany.  
  
6.  Kliknij przycisk **argumenty** w lewym dolnym rogu Projektant działań, aby wyświetlić **argumenty** okienka.  
  
7.  Kliknij przycisk **utworzenia argumentu**.  
  
8.  Typ `BookmarkName` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
9. Kliknij przycisk **utworzenia argumentu**.  
  
10. Typ `Result` do **nazwa** pole poniżej nowo dodanego `BookmarkName` argumentu, wybierz opcję **limit** z **kierunek** listy rozwijanej wybierz pozycję **Int32** z **typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER.  
  
11. Kliknij przycisk **utworzenia argumentu**.  
  
12. Typ `Text` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej wybierz **ciąg** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
     Te trzy argumenty są powiązane z odpowiedniego argumenty <xref:System.Activities.Statements.WriteLine> i `ReadInt` działań, które są dodawane do `Prompt` działania w kolejnych krokach.  
  
13. Kliknij przycisk **argumenty** w lewym dolnym rogu Projektant działań, aby zamknąć **argumenty** okienka.  
  
14. Przeciągnij **sekwencji** działania z **przepływ sterowania** sekcji **przybornika** i upuść ją na **Upuść tutaj działanie** etykieta **Monitu** Projektant działań.  
  
    > [!TIP]
    >  Jeśli **przybornika** nie zostanie wyświetlone okno, wybierz **przybornika** z **widoku** menu.  
  
15. Przeciągnij **WriteLine** działania z **podstawowych** sekcji **przybornika** i upuść ją na **Upuść tutaj działanie** etykieta **Sekwencji** działania.  
  
16. Powiązać **tekst** argument **WriteLine** działanie **tekst** argument **monitu** działania, wpisując `Text` do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** polu **właściwości** okna, a następnie naciśnij klawisz TAB klucza dwa razy. To odrzuci oknie IntelliSense lista elementów członkowskich i zapisuje wartość właściwości przez przeniesienie zaznaczenia poza właściwości. Można również ustawić tę właściwość, wpisując `Text` do **wprowadź wyrażenie C#** lub **wprowadź wyrażenia języka VB.** pole w działaniu samej siebie.  
  
    > [!TIP]
    >  Jeśli **okna właściwości** nie jest wyświetlane, wybierz pozycję **okna właściwości** z **widoku** menu.  
  
17. Przeciągnij **ReadInt** działania z **NumberGuessWorkflowActivities** sekcji **przybornika** i upuść je w **sekwencji** działanie, którego nie jest zgodna **WriteLine** działania.  
  
18. Powiązanie **Nazwa zakładki** argument **ReadInt** do działania **Nazwa zakładki** argument **monitu** działania, wpisując `BookmarkName` do **wprowadź wyrażenia języka VB.** pole z prawej strony **Nazwa zakładki** argument **okno właściwości**i naciśnij klawisz TAB dwa czas, aby zamknąć okno IntelliSense lista elementów członkowskich i zapisać właściwości.  
  
19. Powiązać **wynik** argument **ReadInt** działanie **wynik** argument **monitu** działania, wpisując `Result` do **wprowadź wyrażenia języka VB.** pole z prawej strony **wynik** argumentu w **okna właściwości**i naciśnij klawisz TAB dwa razy.  
  
20. Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
     Instrukcje dotyczące sposobu tworzenia przepływu pracy przy użyciu tych działań można znaleźć następnego kroku w samouczku [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [Projektowanie i implementowanie niestandardowych działań](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Instrukcje: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Używanie elementu ExpressionTextBox w projektancie działań niestandardowych](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
