---
title: 'Zadanie 2: Host projektanta przepływów pracy'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 8ac6b3590d146909c1cb9fd8cf9cae2352b0155b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="task-2-host-the-workflow-designer"></a>Zadanie 2: Host projektanta przepływów pracy
W tym temacie opisano procedurę obsługi wystąpienia [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] w aplikacji Windows Presentation Foundation (WPF).  
  
 Procedura powoduje skonfigurowanie **siatki** formant, który zawiera projektancie programowo tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner> zawierający domyślne <xref:System.Activities.Statements.Sequence> działania, rejestruje projektanta metadanych w celu zapewnienia projektanta obsługę wszystkich wbudowane działania i hosty [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplikacji.  
  
### <a name="to-host-the-workflow-designer"></a>Do obsługi projektanta przepływów pracy  
  
1.  Otwórz HostingApplication projektu utworzonego w [zadanie 1: Tworzenie nowej aplikacji systemu Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).  
  
2.  Dopasuj rozmiar okna, aby ułatwić korzystanie [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Aby to zrobić, wybierz **właściwości MainWindow** w projektancie, naciśnij klawisz F4, aby wyświetlić **właściwości** okna i w **układu** Brak sekcji, ustaw **szerokość** na wartość 600 i **wysokość** wartość 350.  
  
3.  Ustaw nazwę siatki, wybierając **siatki** panelu w Projektancie (kliknij pole wewnątrz **właściwości MainWindow**) i ustawienie **nazwa** właściwość w górnej części  **Właściwości** okna "grid1".  
  
4.  W **właściwości** okna, kliknij przycisk wielokropka (**...** ) obok pozycji `ColumnDefinitions` właściwości, aby otworzyć **edytora kolekcji** okno dialogowe.  
  
5.  W **edytora kolekcji** okno dialogowe, kliknij przycisk **Dodaj** przycisk trzy razy, aby wstawić trzy kolumny do układu. Pierwsza kolumna będzie zawierać **przybornika**, druga kolumna będzie obsługiwać [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], i trzecia kolumna będzie służyć do Inspektora właściwości.  
  
6.  Ustaw `Width` właściwości środkowej kolumny, która ma wartość "4 *".  
  
7.  Kliknij przycisk **OK** , aby zapisać zmiany. Następujące XAML został dodany do pliku MainWindow.xaml:  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy MainWindow.xaml i wybierz **kod widoku**. Zmodyfikuj kod, wykonując następujące czynności:  
  
    1.  Dodaj następujących przestrzeni nazw:  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  Aby zadeklarować pole prywatnego elementu członkowskiego, aby pomieścić wystąpienia <xref:System.Activities.Presentation.WorkflowDesigner>, Dodaj następujący kod do `MainWindow` klasy.  
  
        ```csharp  
        public partial class MainWindow : Window  
        {  
            private WorkflowDesigner wd;  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
        }  
        ```  
  
    3.  Dodaj następujące `AddDesigner` metody `MainWindow` klasy. Implementacja tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, dodaje <xref:System.Activities.Statements.Sequence> działania i umieszcza je w środkowej kolumnie grid1 **siatki**.  
  
        ```csharp  
        private void AddDesigner()  
        {  
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
        ```  
  
    4.  Zarejestruj projektanta metadane w celu dodania obsługi projektanta dla wszystkich działań wbudowanych. Dzięki temu można porzucić działań z przybornika do oryginalnej <xref:System.Activities.Statements.Sequence> działania w [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Aby to zrobić, należy dodać `RegisterMetadata` metody `MainWindow` klasy.  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         Aby uzyskać więcej informacji o rejestrowaniu projektantów działań, zobacz [jak: utworzyć Designer działania niestandardowe](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).  
  
    5.  W `MainWindow` Konstruktor klasy, Dodaj wywołania metod poprzednio zadeklarowany rejestrowanie metadanych dla wsparcia projektanta i utworzyć <xref:System.Activities.Presentation.WorkflowDesigner>.  
  
        ```csharp  
        public MainWindow()  
        {  
            InitializeComponent();  
  
            // Register the metadata  
            RegisterMetadata();  
  
            // Add the WFF Designer  
            AddDesigner();  
        }  
        ```  
  
        > [!NOTE]
        >  `RegisterMetadata` Metoda rejestruje projektanta metadane działań wbudowanych, łącznie z <xref:System.Activities.Statements.Sequence> działania. Ponieważ `AddDesigner` używa metody <xref:System.Activities.Statements.Sequence> działania, `RegisterMetadata` najpierw musi zostać wywołana metoda.  
  
9. Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie.  
  
10. Zobacz [zadanie 3: tworzenie przybornika i okienka PropertyGrid](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) Aby dowiedzieć się, jak dodać **przybornika** i **PropertyGrid** obsługiwać z projektantem rehosted przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Rehostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [Zadanie 3: Tworzenie okienka PropertyGrid i przybornika](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
