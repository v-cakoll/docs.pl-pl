---
title: Zadanie 2. Hostowanie projektanta przepływu pracy
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 92c5fa347cc7a2c0088ab8f4fbdfddf25ffb83c1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037869"
---
# <a name="task-2-host-the-workflow-designer"></a>Zadanie 2. Hostowanie projektanta przepływu pracy

[!INCLUDE[wfd1](../../../includes/wfd1-md.md)] W tym temacie opisano procedurę hostingu wystąpienia programu w aplikacji Windows Presentation Foundation (WPF).

Procedura konfiguruje kontrolkę **siatki** , która zawiera projektanta, programowo tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner> , które zawiera domyślne <xref:System.Activities.Statements.Sequence> działanie, rejestruje metadane projektanta, aby zapewnić obsługę projektanta dla wszystkich wbudowane działania i hosty [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w aplikacji WPF.

### <a name="to-host-the-workflow-designer"></a>Aby hostować projektanta przepływu pracy

1. Otwórz projekt HostingApplication utworzony w [zadaniu 1: Utwórz nową aplikację](task-1-create-a-new-wpf-app.md)Windows Presentation Foundation.

2. Dostosuj rozmiar okna, aby ułatwić korzystanie z programu [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Aby to zrobić, wybierz pozycję **MainWindow** w projektancie, naciśnij klawisz F4, aby wyświetlić okno **Właściwości** , a następnie w sekcji **układ** Ustaw **Szerokość** na wartość 600 i **wysokość** na wartość 350.

3. Ustaw nazwę siatki, wybierając panel **siatki** w projektancie (kliknij pole wewnątrz **MainWindow**) i ustaw właściwość **Nazwa** w górnej części okna **Właściwości** na "grid1".

4. W oknie **Właściwości** kliknij przycisk wielokropka ( **...** ) `ColumnDefinitions` obok właściwości, aby otworzyć okno dialogowe **Edytor kolekcji** .

5. W oknie dialogowym **Edytor kolekcji** kliknij przycisk **Dodaj** trzy razy, aby wstawić trzy kolumny do układu. Pierwsza kolumna będzie zawierać **Przybornik**, druga kolumna będzie hostować [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], a trzecia kolumna zostanie użyta dla Inspektora właściwości.

6. `Width` Ustaw właściwość środkowej kolumny na wartość "4 *".

7. Kliknij przycisk **OK** , aby zapisać zmiany. Następujący kod XAML zostanie dodany do pliku MainWindow. XAML:

    ```xml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję MainWindow. XAML i wybierz polecenie **Wyświetl kod**. Zmodyfikuj kod, wykonując następujące czynności:

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

    2. Aby zadeklarować prywatne pole elementu członkowskiego do przechowywania wystąpienia <xref:System.Activities.Presentation.WorkflowDesigner>obiektu, Dodaj następujący kod `MainWindow` do klasy.

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

    3. Dodaj następującą `AddDesigner` metodę `MainWindow` do klasy. Implementacja tworzy wystąpienie <xref:System.Activities.Presentation.WorkflowDesigner>, <xref:System.Activities.Statements.Sequence> dodaje do niego działanie i umieszcza je w środkowej kolumnie **siatki**grid1.

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

    4. Zarejestruj metadane projektanta, aby dodać obsługę projektanta dla wszystkich wbudowanych działań. Dzięki temu można porzucić działania z przybornika na pierwotne <xref:System.Activities.Statements.Sequence> działanie [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]w. Aby to zrobić, Dodaj `RegisterMetadata` metodę `MainWindow` do klasy.

        ```csharp
        private void RegisterMetadata()
        {
            DesignerMetadata dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Aby uzyskać więcej informacji na temat rejestrowania projektantów działań [, zobacz How to: Tworzenie niestandardowego projektanta](how-to-create-a-custom-activity-designer.md)działań.

    5. W konstruktorze <xref:System.Activities.Presentation.WorkflowDesigner>klasyDodajwywołania do metod zadeklarowanych wcześniej, aby zarejestrować metadane dla wsparcia projektanta i utworzyć. `MainWindow`

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
        > Metoda rejestruje metadane projektanta działań wbudowanych, w <xref:System.Activities.Statements.Sequence> tym działanie. `RegisterMetadata` Ponieważ metoda używa działania, `RegisterMetadata` Metoda musi być wywoływana jako pierwsza. <xref:System.Activities.Statements.Sequence> `AddDesigner`

9. Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie.

10. Zobacz [zadanie 3: Utwórz okienka](task-3-create-the-toolbox-and-propertygrid-panes.md) Przybornik i PropertyGrid, aby dowiedzieć się, jak dodać **Przybornik** i obsługę elementu **PropertyGrid** do zahostowanego projektanta przepływu pracy.

## <a name="see-also"></a>Zobacz także

- [Rehostowanie projektanta przepływu pracy](rehosting-the-workflow-designer.md)
- [Zadanie 1: Utwórz nową aplikację Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Zadanie 3: Tworzenie okienek Przybornik i PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md)
