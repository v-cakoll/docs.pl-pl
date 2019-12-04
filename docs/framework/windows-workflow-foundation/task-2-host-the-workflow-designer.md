---
title: Zadanie 2. hostowanie Projektant przepływu pracy
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 8e4c17ed182cec7748b9a1f11f76ff90aa60c39e
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715788"
---
# <a name="task-2-host-the-workflow-designer"></a>Zadanie 2. hostowanie Projektant przepływu pracy

W tym temacie opisano procedurę hostingu wystąpienia Projektant przepływu pracy systemu Windows w aplikacji Windows Presentation Foundation (WPF).

Procedura konfiguruje kontrolkę **siatki** , która zawiera projektanta, programowo tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, które zawiera domyślne działanie <xref:System.Activities.Statements.Sequence>, rejestruje metadane projektanta w celu zapewnienia obsługi projektanta dla wszystkich wbudowanych działań i hostuje Projektant przepływu pracy w aplikacji WPF.

## <a name="to-host-the-workflow-designer"></a>Aby hostować projektanta przepływu pracy

1. Otwórz projekt HostingApplication utworzony w [zadaniu 1: Tworzenie nowej aplikacji Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).

2. Dostosuj rozmiar okna, aby ułatwić korzystanie z Projektant przepływu pracy. Aby to zrobić, wybierz pozycję **MainWindow** w projektancie, naciśnij klawisz F4, aby wyświetlić okno **Właściwości** , a następnie w sekcji **układ** Ustaw **Szerokość** na wartość 600 i **wysokość** na wartość 350.

3. Ustaw nazwę siatki, wybierając panel **siatki** w projektancie (kliknij pole wewnątrz **MainWindow**) i ustaw właściwość **Nazwa** w górnej części okna **Właściwości** na "grid1".

4. W oknie **Właściwości** kliknij przycisk wielokropka ( **...** ) obok właściwości `ColumnDefinitions`, aby otworzyć okno dialogowe **Edytor kolekcji** .

5. W oknie dialogowym **Edytor kolekcji** kliknij przycisk **Dodaj** trzy razy, aby wstawić trzy kolumny do układu. Pierwsza kolumna będzie zawierać **Przybornik**, druga kolumna będzie hostować Projektant przepływu pracy, a trzecia kolumna zostanie użyta dla Inspektora właściwości.

6. Ustaw właściwość `Width` środkowej kolumny na wartość "4 *".

7. Kliknij przycisk **OK** , aby zapisać zmiany. Następujący kod XAML zostanie dodany do pliku *MainWindow. XAML* :

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję *MainWindow. XAML* i wybierz polecenie **Wyświetl kod**. Zmodyfikuj kod, wykonując następujące czynności:

    1. Dodaj następujące przestrzenie nazw:

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. Aby zadeklarować prywatne pole elementu członkowskiego do przechowywania wystąpienia <xref:System.Activities.Presentation.WorkflowDesigner>, Dodaj następujący kod do klasy `MainWindow`:

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

    3. Dodaj następującą metodę `AddDesigner` do klasy `MainWindow`. Implementacja tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, dodaje do niego działanie <xref:System.Activities.Statements.Sequence> i umieszcza je w środkowej kolumnie **siatki**grid1.

        ```csharp
        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. Zarejestruj metadane projektanta, aby dodać obsługę projektanta dla wszystkich wbudowanych działań. Dzięki temu można porzucić działania z przybornika do oryginalnego działania <xref:System.Activities.Statements.Sequence> w Projektant przepływu pracy. Aby to zrobić, Dodaj metodę `RegisterMetadata` do klasy `MainWindow`:

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Aby uzyskać więcej informacji na temat rejestrowania projektantów działań, zobacz [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).

    5. W konstruktorze klasy `MainWindow` Dodaj wywołania do metod zadeklarowanych wcześniej, aby zarejestrować metadane dla wsparcia projektanta i utworzyć <xref:System.Activities.Presentation.WorkflowDesigner>.

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > Metoda `RegisterMetadata` rejestruje metadane projektanta działań wbudowanych, w tym działanie <xref:System.Activities.Statements.Sequence>. Ponieważ metoda `AddDesigner` używa działania <xref:System.Activities.Statements.Sequence>, Metoda `RegisterMetadata` musi być wywoływana jako pierwsza.

9. Naciśnij klawisz <kbd>F5</kbd> , aby skompilować i uruchomić rozwiązanie.

10. Zobacz [zadanie 3. Tworzenie okienek Przybornik i PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) , aby dowiedzieć się, jak dodać **Przybornik** i obsługę elementu **PropertyGrid** do zahostowanego projektanta przepływu pracy.

## <a name="see-also"></a>Zobacz także

- [Rehostowanie projektanta przepływu pracy](rehosting-the-workflow-designer.md)
- [Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Zadanie 3: Tworzenie okienka PropertyGrid i przybornika](task-3-create-the-toolbox-and-propertygrid-panes.md)
