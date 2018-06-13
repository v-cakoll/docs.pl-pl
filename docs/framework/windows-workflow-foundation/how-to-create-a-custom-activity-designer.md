---
title: 'Porady: tworzenie Projektant działań niestandardowych'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: e4aab60a598be2d6df5546ab1c98a289b4aef04a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520347"
---
# <a name="how-to-create-a-custom-activity-designer"></a>Porady: tworzenie Projektant działań niestandardowych
Projektantów działań niestandardowych są zwykle implementowany ich działania skojarzone są zezwala na składanie z innymi działaniami projektantów, których można było porzucić na powierzchnię projektu z nimi. Ta funkcja wymaga, Projektant działań niestandardowych podania "strefy docelowej" rozmieszczenia dowolne działanie, a także sposób zarządzania wynikowy zbiór elementów na powierzchnię projektu. W tym temacie opisano, jak utworzyć projektanta działań niestandardowych, który zawiera strefy docelowej i jak utworzyć designer działania niestandardowego, który zapewnia, że funkcji edytowania potrzebne do zarządzania kolekcję elementów projektanta.  
  
 Zwykle dziedziczyć projektantów działań niestandardowych <xref:System.Activities.Presentation.ActivityDesigner> czyli domyślny typ projektanta działanie podstawowe dla dowolnego działania bez określonego projektanta. Ten typ zapewnia środowisko czasu projektowania interakcji z siatką właściwości i konfigurowania podstawowych aspektów, takie jak zarządzanie, kolory i ikon.  
  
 <xref:System.Activities.Presentation.ActivityDesigner> używa dwóch formantów pomocnika, <xref:System.Activities.Presentation.WorkflowItemPresenter> i <xref:System.Activities.Presentation.WorkflowItemsPresenter> ułatwiające opracowanie projektantów działań niestandardowych. Obsługują typowych funkcji, takich jak przeciąganie i upuszczanie elementów podrzędnych, usuwanie, wybór i dodanie tych elementów podrzędnych. <xref:System.Activities.Presentation.WorkflowItemPresenter> Umożliwia pojedynczy element potomny elementu interfejsu użytkownika wewnątrz "strefy docelowej", podając go podczas <xref:System.Activities.Presentation.WorkflowItemsPresenter> zapewniają obsługuje wiele elementów interfejsu użytkownika, takie jak dodatkowe funkcje, takie jak kolejność, przenoszenie i dodawanie elementów podrzędnych.  
  
 Inne część klucza artykuł, który wymaga wyróżnianie w implementacji Projektant działań niestandardowych dotyczy sposób, w którym zmiany wizualne są powiązane za pomocą [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] wiązanie danych do wystąpienia przechowywane w pamięci, co możemy edycji w projektancie. Jest to osiągane przez drzewo element modelu, w którym jest również odpowiada za włączanie powiadomienia o zmianie i śledzenia zdarzeń, takich jak zmiany stanów.  
  
 W tym temacie przedstawiono dwie procedury.  
  
1.  Pierwsza procedura opisuje sposób tworzenia Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemPresenter> zapewnia strefy docelowej odbierająca innych działań. Ta procedura jest oparta na [niestandardowe projektantów złożonego - Prezenterze element przepływu pracy](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) próbki.  
  
2.  W drugiej procedurze opisano sposób tworzenia Projektant działań niestandardowych z <xref:System.Activities.Presentation.WorkflowItemsPresenter> zapewnia funkcje potrzebne do edycji z kolekcją elementów zawartych w niej. Ta procedura jest oparta na [niestandardowe projektantów złożonego - Prezenterze elementy przepływu pracy](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) próbki.  
  
### <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Aby utworzyć designer działań niestandardowych z strefy docelowej przy użyciu WorkflowItemPresenter  
  
1.  Uruchom [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu...** .  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku wybierz **Windows** z kategorii preferowany język.  
  
4.  W **szablony** okienku wybierz **aplikacji WPF**.  
  
5.  W **nazwa** wprowadź `UsingWorkflowItemPresenter`.  
  
6.  W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt, lub kliknij przycisk **Przeglądaj** można przejść do niego.  
  
7.  W **rozwiązania** pozycję Zaakceptuj wartość domyślną.  
  
8.  Kliknij przycisk **OK**.  
  
9. Kliknij prawym przyciskiem myszy plik MainWindows.xaml **Eksploratora rozwiązań**, wybierz pozycję **usunąć** i Potwierdź **OK** w **programu Microsoft Visual Studio**okno dialogowe.  
  
10. Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksploratora rozwiązań**, wybierz pozycję **Dodaj**, następnie **nowy element...** Aby wyświetlić **Dodaj nowy element** dialog i wybierz **WPF** kategorii z **zainstalowane szablony** po lewej stronie.  
  
11. Wybierz **okna (WPF)** szablonu, nadaj jej nazwę `RehostingWFDesigner`i kliknij przycisk **Dodaj**.  
  
12. Otwórz plik RehostingWFDesigner.xaml i wklej następujący kod do niego, aby zdefiniować interfejsu użytkownika dla aplikacji.  
  
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
  
13. Aby skojarzyć Projektant działań z typem działania, że Projektant działań należy zarejestrować się w magazynie metadanych. Aby to zrobić, należy dodać `RegisterMetadata` metody `RehostingWFDesigner` klasy. W zakresie `RegisterMetadata` metody, Utwórz <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> obiekt i wywołanie <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metodę, aby dodać atrybuty do niego. Wywołanie <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> metody w celu dodania <xref:System.Activities.Presentation.Metadata.AttributeTable> w magazynie metadanych. Poniższy kod zawiera logikę rehosting projektanta. Rejestruje metadanych, umieszcza `SimpleNativeActivity` do przybornika i tworzy przepływ pracy. Umieść ten kod do pliku RehostingWFDesigner.xaml.cs.  
  
    ```  
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
  
14. Kliknij prawym przyciskiem myszy katalogu odwołania w Eksploratorze rozwiązań i wybierz **Dodawanie odwołania...** Aby wyświetlić **Dodaj odwołanie** dialogu.  
  
15. Kliknij przycisk **.NET** zlokalizuj zestawu o nazwie **System.Activities.Core.Presentation**, zaznacz go i kliknij **OK**.  
  
16. Przy użyciu tej samej procedury, dodaj odwołania do następujących zestawów:  
  
    1.  System.Data.DataSetExtensions.dll  
  
    2.  System.Activities.Presentation.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
17. Otwórz plik App.xaml i zmień wartość StartUpUri "RehostingWFDesigner.xaml".  
  
18. Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksploratora rozwiązań**, wybierz pozycję **Dodaj**, następnie **nowy element...** Aby wyświetlić **Dodaj nowy element** dialog i wybierz **przepływu pracy** formularz kategorii **zainstalowane szablony** po lewej stronie.  
  
19. Wybierz **Projektant działań** szablonu, nadaj jej nazwę `SimpleNativeDesigner`i kliknij przycisk **Dodaj**.  
  
20. Otwórz plik SimpleNativeDesigner.xaml i wklej następujący kod do niego. Należy pamiętać, ten kod zawiera <xref:System.Activities.Presentation.ActivityDesigner> jako element główny i pokazuje sposób powiązania jest używany do integrowania <xref:System.Activities.Presentation.WorkflowItemPresenter> w z projektantem, więc typ podrzędny mogą być wyświetlane w Projektancie Twoje działania złożonego.  
  
    > [!NOTE]
    >  Schemat dla <xref:System.Activities.Presentation.ActivityDesigner> umożliwia dodanie tylko jeden element podrzędny elementu do definicji projektanta działań niestandardowych; jednak ten element może być `StackPanel`, `Grid`, lub niektóre inne złożonego elementu interfejsu użytkownika.  
  
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
  
21. Kliknij prawym przyciskiem myszy projekt UsingWorkflowItemPresenter w **Eksploratora rozwiązań**, wybierz pozycję **Dodaj**, następnie **nowy element...** Aby wyświetlić **Dodaj nowy element** dialog i wybierz **przepływu pracy** formularz kategorii **zainstalowane szablony** po lewej stronie.  
  
22. Wybierz **działania związane z kodem** szablonu, nadaj jej nazwę `SimpleNativeActivity`i kliknij przycisk **Dodaj**.  
  
23. Implementowanie `SimpleNativeActivity` klasy wprowadzając następujący kod do pliku SimpleNativeActivity.cs.  
  
    ```  
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
  
25. Wybierz **uruchomić bez debugowania** z **debugowania** menu, aby otworzyć okno rehosted projektowania niestandardowego.  
  
### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Aby utworzyć designer działań niestandardowych, za pomocą WorkflowItemsPresenter  
  
1.  Procedura drugi Projektant działań niestandardowych jest równoleżników pierwsza z kilka zmian, z których pierwszy polega na nazwę drugiego aplikacji `UsingWorkflowItemsPresenter`. Ta aplikacja nie definiuje również nowe niestandardowe działanie.  
  
2.  Podstawowe różnice są zawarte w plikach CustomParallelDesigner.xaml i RehostingWFDesigner.xaml.cs. Oto kod z pliku CustomParallelDesigne.xaml, który definiuje interfejsu użytkownika.  
  
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
  
3.  Oto kod z pliku RehostingWFDesigner.xaml.cs, który zapewnia rehosting logiki.  
  
    ```  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Presentation.ActivityDesigner>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 <xref:System.Activities.Presentation.WorkflowViewElement>  
 <xref:System.Activities.Presentation.Model.ModelItem>  
 [Dostosowywanie środowiska projektowania przepływu pracy](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
