---
title: Zadanie 3. Tworzenie okienka PropertyGrid i przybornika
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 8e332c2caa43e1c9703272d7f2be16b545c44fd3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558426"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Zadanie 3. Tworzenie okienka PropertyGrid i przybornika
W tym zadaniu utworzysz **przybornika** i **PropertyGrid** okienka i dodać je do rehostowanym [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Odwołanie, kod, który powinien znajdować się w pliku MainWindow.xaml.cs po ukończeniu trzy zadania w programie [Rehostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) szeregu tematów znajduje się na końcu tego tematu.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Aby utworzyć przybornik i dodaj go do siatki  
  
1.  Otwórz projekt HostingApplication uzyskany postępując zgodnie z procedurą opisaną w artykule [zadanie 2: Hostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).  
  
2.  W **Eksploratora rozwiązań** okienku kliknij prawym przyciskiem myszy pliku MainWindow.xaml i wybierz **Wyświetl kod**.  
  
3.  Dodaj `GetToolboxControl` metody `MainWindow` klasy, która tworzy <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, dodaje nowy **przybornika** kategorię, aby **przybornika**i przypisuje <xref:System.Activities.Statements.Assign> i <xref:System.Activities.Statements.Sequence> typy działań do tej kategorii.  
  
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
  
4.  Dodaj prywatnej `AddToolbox` metody `MainWindow` klasy, która umieszcza **przybornika** w lewej kolumnie siatki.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  Dodaj wywołanie do `AddToolBox` method in Class metoda `MainWindow()` konstruktora klasy, jak pokazano w poniższym kodzie.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie. **Przybornika** zawierający <xref:System.Activities.Statements.Assign> i <xref:System.Activities.Statements.Sequence> działań powinien być wyświetlany.  
  
### <a name="to-create-the-propertygrid"></a>Aby utworzyć PropertyGrid  
  
1.  W **Eksploratora rozwiązań** okienku kliknij prawym przyciskiem myszy pliku MainWindow.xaml i wybierz **Wyświetl kod**.  
  
2.  Dodaj `AddPropertyInspector` metody `MainWindow` klasy, aby umieścić **PropertyGrid** w okienku po prawej stronie kolumny w siatce.  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  Dodaj wywołanie do `AddPropertyInspector` method in Class metoda `MainWindow()` konstruktora klasy, jak pokazano w poniższym kodzie.  
  
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
  
4.  Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie. **Przybornika**, kanwą przepływu pracy i **PropertyGrid** okienka powinny być wyświetlane wszystkie i przeciągnięcie <xref:System.Activities.Statements.Assign> działania lub <xref:System.Activities.Statements.Sequence> działania na kanwę projektu siatki właściwości, należy zaktualizować w zależności od działania wyróżnione.  
  
## <a name="example"></a>Przykład  
 Plik MainWindow.xaml.cs teraz powinien zawierać następujący kod.  
  
```  
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
- [Rehostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)
- [Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)
- [Zadanie 2. Hostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
