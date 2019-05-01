---
title: 'Instrukcje: Tworzenie niestandardowego projektanta działań'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: e455d00ebd128c37eacb19df0e7f864505df04e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945655"
---
# <a name="how-to-create-a-custom-activity-designer"></a>Instrukcje: Tworzenie niestandardowego projektanta działań

Niestandardowi Projektanci działań są zazwyczaj implementowane tak, aby ich skojarzonych działań jest konfigurowalna z innymi działaniami, projektantów, których można było porzucić do powierzchni projektowej z nimi. Ta funkcja wymaga, że niestandardowego projektanta działań zapewniają "strefy listy" gdzie można umieścić dowolne działanie, a także sposób zarządzać wynikowy kolekcję elementów na powierzchni projektowej. W tym temacie opisano sposób tworzenia niestandardowego projektanta działań zawierający strefę listy oraz sposób tworzenia niestandardowego projektanta działań zapewniający, że edytowanie funkcji wymaganych do zarządzania kolekcję elementów projektanta.

Niestandardowi Projektanci działań, ale zazwyczaj dziedziczyć <xref:System.Activities.Presentation.ActivityDesigner> czyli domyślny typ projektanta podstawowego elementu activity dla dowolnego działania bez określonego projektanta. Ten typ zapewnia środowisko czasu projektowania interakcji z siatką właściwości i konfigurowania podstawowe kwestie, takie jak zarządzanie kolorów i ikon.

<xref:System.Activities.Presentation.ActivityDesigner> używa dwóch kontrolek pomocnika, <xref:System.Activities.Presentation.WorkflowItemPresenter> i <xref:System.Activities.Presentation.WorkflowItemsPresenter> ułatwiają tworzenie Projektanci działań niestandardowych. Obsługują one często używane funkcje takie jak przeciągnięcie i upuszczenie elementów podrzędnych, usunięcie, wybór i dodanie tych elementów podrzędnych. <xref:System.Activities.Presentation.WorkflowItemPresenter> Umożliwia pojedynczy element podrzędny elementu interfejsu użytkownika wewnątrz, zapewniając "docelowej strefie", jego podczas <xref:System.Activities.Presentation.WorkflowItemsPresenter> może zapewnić obsługuje wiele elementów interfejsu użytkownika, takie jak dodatkowe funkcje, takie jak kolejność, przenoszenie i dodawania elementów podrzędnych.

Kluczowym elementem z historią, która wymaga wyróżniania w implementacji niestandardowego projektanta działań dotyczy sposób, w którym zmiany wizualne powiązane przy użyciu [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] powiązanie danych do wystąpienia, przechowywane w pamięci w procentach co możemy edycji w projektancie. Jest to realizowane przez drzewo elementów modelu, który jest również odpowiedzialny za włączanie powiadomień o zmianach i śledzenia zdarzeń, takich jak zmiany stanów.

W tym temacie opisano dwie procedury.

1. Pierwsza procedura w tym artykule opisano sposób tworzenia niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemPresenter> zapewniający strefy listy, który odbiera innych działań. Ta procedura jest oparty na [niestandardowe projektantów złożonych — Prezenter elementu przepływu pracy](./samples/custom-composite-designers-workflow-item-presenter.md) próbki.

2. W drugiej procedurze opisano sposób tworzenia niestandardowego projektanta działań z <xref:System.Activities.Presentation.WorkflowItemsPresenter> zapewniająca funkcje potrzebne do edycji zbioru zawarte elementy. Ta procedura jest oparty na [niestandardowe projektantów złożonych — Prezenter elementy przepływu pracy](./samples/custom-composite-designers-workflow-items-presenter.md) próbki.

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Aby utworzyć niestandardowego projektanta działań ze strefą listy przy użyciu WorkflowItemPresenter

1. Start Visual Studio 2010.

2. Na **pliku** menu wskaż **New**, a następnie wybierz pozycję **projektu...** .

     **Nowy projekt** zostanie otwarte okno dialogowe.

3. W **zainstalowane szablony** okienku wybierz **Windows** z kategorii Twojego preferowanego języka.

4. W **szablony** okienku wybierz **aplikacji WPF**.

5. W **nazwa** wprowadź `UsingWorkflowItemPresenter`.

6. W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.

7. W **rozwiązania** zaakceptuj wartość domyślną.

8. Kliknij przycisk **OK**.

9. Kliknij prawym przyciskiem myszy plik MainWindows.xaml **Eksploratora rozwiązań**, wybierz opcję **Usuń** i upewnij się, **OK** w **programu Microsoft Visual Studio**okno dialogowe.

10. Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksploratora rozwiązań**, wybierz opcję **Dodaj**, następnie **nowy element...** Aby wyświetlić **Dodaj nowy element** dialog i wybierz **WPF** kategorię z **zainstalowane szablony** sekcji po lewej stronie.

11. Wybierz **okno (WPF)** szablonu, nadaj jej nazwę `RehostingWFDesigner`i kliknij przycisk **Dodaj**.

12. Otwórz plik RehostingWFDesigner.xaml i wklej następujący kod do niej, aby zdefiniować interfejsu użytkownika dla aplikacji.

    ```xml
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"
            xmlns:sys="clr-namespace:System;assembly=mscorlib"
            Title="Window1" Height="600" Width="900">
        <Window.Resources>
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>
        </Window.Resources>
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="2*"/>
                <ColumnDefinition Width="7*"/>
                <ColumnDefinition Width="3*"/>
            </Grid.ColumnDefinitions>
            <Border Grid.Column="0">
                <sapt:ToolboxControl Name="Toolbox">
                    <sapt:ToolboxCategory CategoryName="Basic">
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.Sequence
                            </sapt:ToolboxItemWrapper.ToolName>
                           </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.WriteLine
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.If
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.While
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                    </sapt:ToolboxCategory>
                </sapt:ToolboxControl>
            </Border>
            <Border Grid.Column="1" Name="DesignerBorder"/>
            <Border Grid.Column="2" Name="PropertyBorder"/>
        </Grid>
    </Window>
    ```

13. Aby skojarzyć projektanta działań z typem działania, należy zarejestrować tego projektanta działań przy użyciu magazynu metadanych. Aby to zrobić, Dodaj `RegisterMetadata` metody `RehostingWFDesigner` klasy. W zakresie `RegisterMetadata` metody tworzenia <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> obiektu, a następnie wywołać <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metodę, aby dodać atrybuty do niego. Wywołaj <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> metody w celu dodania <xref:System.Activities.Presentation.Metadata.AttributeTable> w magazynie metadanych. Poniższy kod zawiera logikę rehosting projektanta. Rejestruje metadanych, umieszcza `SimpleNativeActivity` w przyborniku i tworzy przepływ pracy. Umieść ten kod w pliku RehostingWFDesigner.xaml.cs.

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Presentation.Toolbox;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespace UsingWorkflowItemPresenter
    {
        // Interaction logic for RehostingWFDesigner.xaml
        public partial class RehostingWFDesigner
        {
            public RehostingWFDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // register metadata
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // add custom activity to toolbox
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // create the workflow designer
                WorkflowDesigner wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                AttributeTableBuilder builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. Kliknij prawym przyciskiem myszy katalog odwołania w Eksploratorze rozwiązań i wybierz **Dodaj odwołanie...** Aby wyświetlić **Dodaj odwołanie** dialogu.

15. Kliknij przycisk **.NET** kartę, Znajdź zestaw o nazwie **System.Activities.Core.Presentation**, zaznacz go i kliknij przycisk **OK**.

16. Korzystając z tej samej procedury, dodaj odwołania do następujących zestawów:

    1. System.Data.DataSetExtensions.dll

    2. System.Activities.Presentation.dll

    3. System.ServiceModel.Activities.dll

17. Otwórz plik App.xaml i zmień wartość StartUpUri na "RehostingWFDesigner.xaml".

18. Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksploratora rozwiązań**, wybierz opcję **Dodaj**, następnie **nowy element...** Aby wyświetlić **Dodaj nowy element** dialog i wybierz **przepływu pracy** formularz kategorii **zainstalowane szablony** sekcji po lewej stronie.

19. Wybierz **projektanta działań** szablonu, nadaj jej nazwę `SimpleNativeDesigner`i kliknij przycisk **Dodaj**.

20. Otwórz plik SimpleNativeDesigner.xaml i wklej następujący kod. Należy pamiętać, ten kod używa <xref:System.Activities.Presentation.ActivityDesigner> jako element główny i pokazuje, jak powiązania jest używany do integracji <xref:System.Activities.Presentation.WorkflowItemPresenter> do projektanta, typ elementu podrzędnego, może być wyświetlany na projektanta działań złożonych.

    > [!NOTE]
    > Schemat dla <xref:System.Activities.Presentation.ActivityDesigner> zezwala na dodawanie tylko jeden element podrzędny elementu definicję projektanta działań niestandardowych; jednak ten element może być `StackPanel`, `Grid`, lub innego złożonego elementu interfejsu użytkownika.

    ```xml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <StackPanel>
                    <TextBlock>This is the collapsed view</TextBlock>
                </StackPanel>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock>Custom Text</TextBlock>
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                            HintText="Please drop an activity here" />
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
        </Grid>
    </sap:ActivityDesigner>
    ```

21. Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksploratora rozwiązań**, wybierz opcję **Dodaj**, następnie **nowy element...** Aby wyświetlić **Dodaj nowy element** dialog i wybierz **przepływu pracy** formularz kategorii **zainstalowane szablony** sekcji po lewej stronie.

22. Wybierz **działanie kodu** szablonu, nadaj jej nazwę `SimpleNativeActivity`i kliknij przycisk **Dodaj**.

23. Implementowanie `SimpleNativeActivity` klasy, wprowadzając następujący kod do pliku SimpleNativeActivity.cs.

    ```csharp
    using System.Activities;

    namespace UsingWorkflowItemPresenter
    {
        public sealed class SimpleNativeActivity : NativeActivity
        {
            // this property contains an activity that will be scheduled in the execute method
            // the WorkflowItemPresenter in the designer is bound to this to enable editing
            // of the value
            public Activity Body { get; set; }

            protected override void CacheMetadata(NativeActivityMetadata metadata)
            {
               metadata.AddChild(Body);
               base.CacheMetadata(metadata);

            }

            protected override void Execute(NativeActivityContext context)
            {
                context.ScheduleActivity(Body);
            }
        }
    }
    ```

24. Wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.

25. Wybierz **Rozpocznij bez debugowania** z **debugowania** menu, aby otworzyć okno rehostowanym projektowania niestandardowego.

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Aby utworzyć niestandardowego projektanta działań przy użyciu WorkflowItemsPresenter

1. Procedura drugi niestandardowego projektanta działań jest parallels, pierwszy z kilka zmian, z których pierwszy to nazwa drugiej aplikacji `UsingWorkflowItemsPresenter`. Ta aplikacja nie definiuje również nowe niestandardowe działanie.

2. Podstawowe różnice są zawarte w plikach CustomParallelDesigner.xaml i RehostingWFDesigner.xaml.cs. Poniżej przedstawiono kod z pliku CustomParallelDesigner.xaml, który określa interfejs użytkownika.

    ```xml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <TextBlock>This is the Collapsed View</TextBlock>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"
                                        Items="{Binding Path=ModelItem.Branches}">
                        <sap:WorkflowItemsPresenter.SpacerTemplate>
                            <DataTemplate>
                                <Ellipse Width="10" Height="10" Fill="Black"/>
                            </DataTemplate>
                        </sap:WorkflowItemsPresenter.SpacerTemplate>
                        <sap:WorkflowItemsPresenter.ItemsPanel>
                            <ItemsPanelTemplate>
                                <StackPanel Orientation="Horizontal"/>
                            </ItemsPanelTemplate>
                        </sap:WorkflowItemsPresenter.ItemsPanel>
                    </sap:WorkflowItemsPresenter>
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
        </Grid>
    </sap:ActivityDesigner>
    ```

3. Poniżej przedstawiono kod z pliku RehostingWFDesigner.xaml.cs, który udostępnia logikę rehosting.

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespaceUsingWorkflowItemsPresenter
    {
        public partial class RehostingWfDesigner : Window
        {
            public RehostingWfDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // register metadata
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // create the workflow designer
                WorkflowDesigner wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                AttributeTableBuilder builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [Dostosowywanie środowiska projektowania przepływu pracy](customizing-the-workflow-design-experience.md)
