---
title: 'Porady: Tworzenie niestandardowego projektanta działań'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 3c326508744f2aa2b34f5ee574cc9ec1e2863cf6
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306349"
---
# <a name="how-to-create-a-custom-activity-designer"></a>Instrukcje: Tworzenie niestandardowego projektanta działań

Projektanci działań niestandardowych są zwykle implementowane, dzięki czemu ich skojarzone działania są przeznaczone do tworzenia z innymi działaniami, których projektanci mogą zostać porzucone do powierzchni projektowej. Ta funkcja wymaga, aby niestandardowy Projektant działań zapewniał "upuszczania strefy", w której można umieścić dowolne działanie, a także środki do zarządzania wynikiem zebrania elementów na powierzchni projektowej. W tym temacie opisano sposób tworzenia niestandardowego projektanta działań zawierającego taką strefę upuszczania oraz sposób tworzenia niestandardowego projektanta działań, który zapewnia, że funkcje edytowania potrzebne do zarządzania kolekcją elementów projektanta.

Projektanci działań niestandardowych zwykle dziedziczą <xref:System.Activities.Presentation.ActivityDesigner> z, który jest domyślnym typem projektanta działań podstawowych dla wszystkich działań bez określonego projektanta. Ten typ zapewnia środowisko czasu projektowania do współpracy z siatką właściwości i konfigurowania podstawowych aspektów, takich jak zarządzanie kolorami i ikonami.

<xref:System.Activities.Presentation.ActivityDesigner>używa dwóch kontrolek <xref:System.Activities.Presentation.WorkflowItemPresenter> pomocnika <xref:System.Activities.Presentation.WorkflowItemsPresenter> i ułatwia Opracowywanie niestandardowych projektantów działań. Obsługują one typowe funkcje, takie jak przeciąganie i upuszczanie elementów podrzędnych, usuwanie, wybieranie i Dodawanie tych elementów podrzędnych. Zezwala na pojedynczy podrzędny element interfejsu użytkownika wewnątrz, co zapewnia "strefę upuszczania", <xref:System.Activities.Presentation.WorkflowItemsPresenter> podczas gdy może zapewnić obsługę wielu elementów interfejsu użytkownika, w tym dodatkowych funkcji, takich jak porządkowanie, przesuwanie, usuwanie i Dodawanie elementów podrzędnych. <xref:System.Activities.Presentation.WorkflowItemPresenter>

Druga część tego wątku, która wymaga wyróżnienia w implementacji niestandardowego projektanta działań, ma wpływ na sposób, w jaki zmiany wizualne są powiązane przy użyciu powiązania danych WPF z wystąpieniem przechowywanym w pamięci w projektancie. Jest to realizowane przez drzewo elementów modelu, które jest również odpowiedzialne za Włączanie powiadomień o zmianach i śledzenie zdarzeń, takich jak zmiany w Stanach.

W tym temacie przedstawiono dwie procedury.

1. W pierwszej procedurze opisano sposób tworzenia niestandardowego projektanta działań z programem <xref:System.Activities.Presentation.WorkflowItemPresenter> , który zapewnia strefę upuszczania, która odbiera inne działania. Ta procedura jest oparta na [niestandardowym projektantom złożonym — przykładowi prezentera elementu przepływu pracy](./samples/custom-composite-designers-workflow-item-presenter.md) .

2. Druga procedura zawiera opis sposobu tworzenia niestandardowego projektanta działań z programem <xref:System.Activities.Presentation.WorkflowItemsPresenter> , który zapewnia funkcje konieczne do edytowania kolekcji zawartych elementów. Ta procedura jest oparta na [niestandardowym projektantom złożonym — przykładowi dla prezenterów elementów przepływu pracy](./samples/custom-composite-designers-workflow-items-presenter.md) .

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Aby utworzyć niestandardowy Projektant działań ze strefą upuszczania przy użyciu WorkflowItemPresenter

1. Uruchom program Visual Studio 2010.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie wybierz pozycję **projekt...** .

     **Nowy projekt** zostanie otwarte okno dialogowe.

3. W okienku **zainstalowane szablony** wybierz pozycję **Windows** z preferowanej kategorii języka.

4. W okienku **Szablony** wybierz pozycję **Aplikacja WPF**.

5. W polu **Nazwa** wprowadź `UsingWorkflowItemPresenter`wartość.

6. W polu **Lokalizacja** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** , aby przejść do niego.

7. W polu **rozwiązanie** Zaakceptuj wartość domyślną.

8. Kliknij przycisk **OK**.

9. Kliknij prawym przyciskiem myszy plik *MainWindows. XAML* w **Eksplorator rozwiązań**, wybierz pozycję **Usuń** i Potwierdź **OK** w oknie dialogowym **Microsoft Visual Studio** .

10. Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksplorator rozwiązań**, wybierz pozycję **Dodaj**, a następnie pozycję **nowy element...** Aby wyświetlić okno dialogowe **Dodaj nowy element** i wybrać kategorię **WPF** z sekcji **zainstalowane szablony** po lewej stronie.

11. Wybierz szablon **okna (WPF)** , nadaj mu `RehostingWFDesigner`nazwę, a następnie kliknij przycisk **Dodaj**.

12. Otwórz plik *RehostingWFDesigner. XAML* i wklej do niego następujący kod, aby zdefiniować interfejs użytkownika dla aplikacji:

    ```xaml
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

13. Aby skojarzyć projektanta działań z typem działania, należy zarejestrować ten Projektant działań w magazynie metadanych. Aby to zrobić, Dodaj `RegisterMetadata` metodę `RehostingWFDesigner` do klasy. W zakresie `RegisterMetadata` metody <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> Utwórz obiekt i Wywołaj <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metodę, aby dodać do niej atrybuty. <xref:System.Activities.Presentation.Metadata.AttributeTable> Wywołaj <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> metodę, aby dodać do magazynu metadanych. Poniższy kod zawiera logikę rehostowania dla projektanta. Rejestruje metadane, umieszcza je `SimpleNativeActivity` w przyborniku i tworzy przepływ pracy. Umieść ten kod w pliku *RehostingWFDesigner.XAML.cs* .

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
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. Kliknij prawym przyciskiem myszy katalog odwołania w Eksplorator rozwiązań i wybierz polecenie **Dodaj odwołanie...** Aby wyświetlić okno dialogowe **Dodawanie odwołania** .

15. Kliknij kartę **.NET** , odszukaj zestaw o nazwie **System. Activities. Core. Presentation**, zaznacz go i kliknij przycisk **OK**.

16. Korzystając z tej samej procedury, Dodaj odwołania do następujących zestawów:

    1. System.Data.DataSetExtensions.dll

    2. System.Activities.Presentation.dll

    3. System.ServiceModel.Activities.dll

17. Otwórz plik *App. XAML* i zmień wartość StartUpUri na "RehostingWFDesigner. XAML".

18. Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksplorator rozwiązań**, wybierz pozycję **Dodaj**, a następnie pozycję **nowy element...** Aby wyświetlić okno dialogowe **Dodaj nowy element** , a następnie wybierz kategorię **przepływ pracy** formularz w sekcji **zainstalowane szablony** po lewej stronie.

19. Wybierz szablon **projektanta działań** , nadaj mu `SimpleNativeDesigner`nazwę, a następnie kliknij przycisk **Dodaj**.

20. Otwórz plik *SimpleNativeDesigner. XAML* i wklej do niego następujący kod. Zwróć uwagę, że <xref:System.Activities.Presentation.ActivityDesigner> ten kod używa jako elementu głównego i pokazuje, jak powiązanie jest <xref:System.Activities.Presentation.WorkflowItemPresenter> używane do integrowania z projektantem, dzięki czemu typ podrzędny może być wyświetlany w projektancie działań złożonych.

    > [!NOTE]
    > Schemat dla programu <xref:System.Activities.Presentation.ActivityDesigner> umożliwia dodanie tylko jednego elementu podrzędnego do definicji projektanta działań niestandardowych, jednak ten element może `StackPanel`być, `Grid`lub innego złożonego elementu interfejsu użytkownika.

    ```xaml
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

21. Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksplorator rozwiązań**, wybierz pozycję **Dodaj**, a następnie pozycję **nowy element...** Aby wyświetlić okno dialogowe **Dodaj nowy element** , a następnie wybierz kategorię **przepływ pracy** formularz w sekcji **zainstalowane szablony** po lewej stronie.

22. Wybierz szablon **działania kod** , nadaj mu `SimpleNativeActivity`nazwę, a następnie kliknij przycisk **Dodaj**.

23. Zaimplementuj klasę, wprowadzając następujący kod do pliku *SimpleNativeActivity.cs:* `SimpleNativeActivity`

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

24. Wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** .

25. Wybierz pozycję **Uruchom bez debugowania** z menu **Debuguj** , aby otworzyć okno zaprojektowanie niestandardowe.

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Tworzenie niestandardowego projektanta działań za pomocą WorkflowItemsPresenter

1. Procedura drugiego niestandardowego projektanta działań jest równoległa do pierwszego z kilku modyfikacji, a pierwszy to nazwa drugiej aplikacji `UsingWorkflowItemsPresenter`. Ponadto ta aplikacja nie definiuje nowego działania niestandardowego.

2. Kluczowe różnice są zawarte w plikach *CustomParallelDesigner. XAML* i *RehostingWFDesigner.XAML.cs* . Oto kod z pliku *CustomParallelDesigner. XAML* , który definiuje interfejs użytkownika:

    ```xaml
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

3. Oto kod z pliku *RehostingWFDesigner.XAML.cs* , który udostępnia logikę rehostowania:

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
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
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
