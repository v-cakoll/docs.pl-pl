---
title: Zadanie 3. Tworzenie okienka PropertyGrid i przybornika
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 6339969c52a5c4eedfb0e89eebdc982ca3fe6686
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988713"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Zadanie 3. Tworzenie okienka PropertyGrid i przybornika
W tym zadaniu utworzysz okienka **Przybornik** i **PropertyGrid** i dodasz je do ponownego hostowania [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 W przypadku odwołania, kod, który powinien znajdować się w pliku MainWindow.xaml.cs, po wykonaniu trzech zadań w [Projektant przepływu pracy](rehosting-the-workflow-designer.md) serii tematów znajduje się na końcu tego tematu.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Aby utworzyć Przybornik i dodać go do siatki  
  
1. Otwórz projekt HostingApplication, który uzyskano zgodnie z procedurą opisaną w [zadaniu 2: Hostowanie Projektant przepływu pracy](task-2-host-the-workflow-designer.md).  
  
2. W okienku **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik MainWindow. XAML i wybierz polecenie **Wyświetl kod**.  
  
3. <xref:System.Activities.Presentation.Toolbox.ToolboxControl> <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.Assign> Dodaj metodę do klasy, która tworzy, dodaje nową kategorię przybornika do przybornika i przypisuje typy działania i do tej kategorii. `MainWindow` `GetToolboxControl`  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4. Dodaj prywatną `AddToolbox` metodę `MainWindow` do klasy, która umieszcza **Przybornik** w lewej kolumnie siatki.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5. Dodaj wywołanie `AddToolBox` metody `MainWindow()` w konstruktorze klasy, jak pokazano w poniższym kodzie.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6. Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie. Powinien zostać wyświetlony Przybornik <xref:System.Activities.Statements.Assign> zawierający <xref:System.Activities.Statements.Sequence> działania i.  
  
### <a name="to-create-the-propertygrid"></a>Aby utworzyć elementu PropertyGrid  
  
1. W okienku **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik MainWindow. XAML i wybierz polecenie **Wyświetl kod**.  
  
2. Dodaj metodę do klasy, `MainWindow` aby umieścić okienko PropertyGrid w kolumnie znajdującej się po prawej stronie siatki. `AddPropertyInspector`  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3. Dodaj wywołanie `AddPropertyInspector` metody `MainWindow()` w konstruktorze klasy, jak pokazano w poniższym kodzie.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
        this.AddToolBox();  
  
        this.AddPropertyInspector();   
    }  
    ```  
  
4. Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie. Wszystkie okienka dla **przybornika**, kanwy projektu i elementu **PropertyGrid** powinny być wyświetlane, a po przeciągnięciu <xref:System.Activities.Statements.Assign> działania lub <xref:System.Activities.Statements.Sequence> działania na kanwę projektu siatka właściwości powinna zostać zaktualizowana w zależności od wyróżnione działanie.  
  
## <a name="example"></a>Przykład  
 Plik MainWindow.xaml.cs powinien teraz zawierać następujący kod.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
//dlls added  
using System.Activities;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation;  
using System.Activities.Presentation.Metadata;  
using System.Activities.Presentation.Toolbox;  
using System.Activities.Statements;  
using System.ComponentModel;  
  
namespace HostingApplication  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
        private WorkflowDesigner wd;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
            RegisterMetadata();  
            AddDesigner();  
            this.AddToolBox();  
            this.AddPropertyInspector();  
        }  
  
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
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
                typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
            // Add the Toolbox items to the category.  
            category.Add(tool1);  
            category.Add(tool2);  
  
            // Add the category to the ToolBox control.  
            ctrl.Categories.Add(category);  
            return ctrl;  
        }  
  
        private void AddToolBox()  
        {  
            ToolboxControl tc = GetToolboxControl();  
            Grid.SetColumn(tc, 0);  
            grid1.Children.Add(tc);  
        }  
  
        private void AddPropertyInspector()  
        {  
            Grid.SetColumn(wd.PropertyInspectorView, 2);  
            grid1.Children.Add(wd.PropertyInspectorView);  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Rehostowanie projektanta przepływu pracy](rehosting-the-workflow-designer.md)
- [Zadanie 1: Utwórz nową aplikację Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Zadanie 2: Hostowanie Projektant przepływu pracy](task-2-host-the-workflow-designer.md)
