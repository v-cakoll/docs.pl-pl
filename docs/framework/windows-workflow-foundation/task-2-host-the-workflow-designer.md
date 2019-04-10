---
title: Zadanie 2. Hostowanie projektanta przepływu pracy
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 4129d53f73c590535dcbee576cea91e7ad3ff37f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218709"
---
# <a name="task-2-host-the-workflow-designer"></a>Zadanie 2. Hostowanie projektanta przepływu pracy
W tym temacie opisano procedurę do hostowania wystąpienia [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] w aplikacji Windows Presentation Foundation (WPF).  
  
 Procedura umożliwia skonfigurowanie **siatki** kontrolkę zawierającą projektanta, programowo tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner> zawierający domyślne <xref:System.Activities.Statements.Sequence> działania, rejestruje metadane projektanta w celu zapewnienia wsparcie wszystkie wbudowane działania i hosty [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplikacji.  
  
### <a name="to-host-the-workflow-designer"></a>Do obsługi projektanta przepływów pracy  
  
1.  Otwórz HostingApplication projektu utworzonego w sekcji [zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).  
  
2.  Dopasuj rozmiar okna, aby ułatwić użyj [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Aby to zrobić, wybierz **MainWindow** w projektancie, naciśnij klawisz F4, aby wyświetlić **właściwości** okna i w **układ** sekcji istnieje, należy ustawić **szerokość** wartość 600 i **wysokość** wartości 350.  
  
3.  Ustaw nazwę siatki, wybierając **siatki** panelu w Projektancie (kliknij pole wewnątrz **MainWindow**) i ustawienie **nazwa** właściwość w górnej części  **Właściwości** okna "grid1".  
  
4.  W **właściwości** okna, kliknij przycisk wielokropka (**...** ) obok pozycji `ColumnDefinitions` właściwości, aby otworzyć **— Edytor kolekcji** okno dialogowe.  
  
5.  W **— Edytor kolekcji** okno dialogowe, kliknij przycisk **Dodaj** przycisk trzy razy, aby wstawić trzy kolumny do układu. Pierwsza kolumna będzie zawierać **przybornika**, druga kolumna będzie obsługiwać [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], a trzecia kolumna stosowanych w odniesieniu do Inspektora właściwości.  
  
6.  Ustaw `Width` właściwość w środkowej kolumnie na wartość "4 *".  
  
7.  Kliknij przycisk **OK** , aby zapisać zmiany. Następujące XAML zostanie dodany do Twojego pliku MainWindow.xaml:  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy pliku MainWindow.xaml i wybierz **Wyświetl kod**. Należy zmodyfikować kod, wykonując następujące czynności:  
  
    1.  Dodaj następujące przestrzenie nazw:  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  Aby zadeklarować pola prywatnego elementu członkowskiego, aby pomieścić wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, Dodaj następujący kod do `MainWindow` klasy.  
  
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
  
    3.  Dodaj następujący kod `AddDesigner` metody `MainWindow` klasy. Implementacja tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, dodaje <xref:System.Activities.Statements.Sequence> działania i umieszcza je w środkowej kolumnie grid1 **siatki**.  
  
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
  
    4.  Zarejestruj metadane projektanta do projektanta obsługę wbudowanych działań. Dzięki temu można upuszczać działania z przybornika do oryginalnego <xref:System.Activities.Statements.Sequence> działania w [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Aby to zrobić, Dodaj `RegisterMetadata` metody `MainWindow` klasy.  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         Aby uzyskać więcej informacji na temat rejestrowania Projektanci działań, zobacz [jak: Tworzenie niestandardowego projektanta działań](how-to-create-a-custom-activity-designer.md).  
  
    5.  W `MainWindow` konstruktora klasy, Dodaj wywołania metod uprzednio zadeklarowany, zarejestruj metadane projektanta pomocy technicznej i utworzyć <xref:System.Activities.Presentation.WorkflowDesigner>.  
  
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
        >  `RegisterMetadata` Metoda rejestruje metadane projektanta działań wbudowanych, łącznie z <xref:System.Activities.Statements.Sequence> działania. Ponieważ `AddDesigner` metoda używa <xref:System.Activities.Statements.Sequence> działania `RegisterMetadata` najpierw musi zostać wywołana metoda.  
  
9. Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie.  
  
10. Zobacz [zadanie 3: Tworzenie okienka PropertyGrid i przybornika](task-3-create-the-toolbox-and-propertygrid-panes.md) dowiesz się, jak dodać **przybornika** i **PropertyGrid** pomocy technicznej do Twojej rehostowanym projektancie przepływu pracy.  
  
## <a name="see-also"></a>Zobacz także

- [Rehostowanie projektanta przepływu pracy](rehosting-the-workflow-designer.md)
- [Zadanie 1. Tworzenie nowej aplikacji Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Zadanie 3. Tworzenie okienka PropertyGrid i przybornika](task-3-create-the-toolbox-and-propertygrid-panes.md)
