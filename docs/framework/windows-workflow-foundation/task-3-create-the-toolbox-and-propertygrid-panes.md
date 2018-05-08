---
title: 'Zadanie 3: Tworzenie przybornika i PropertyGrid okienka'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 9bfce22e9de1d6115cb88daddcd2dca355b6bae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Zadanie 3: Tworzenie przybornika i PropertyGrid okienka
W ramach tego zadania spowoduje utworzenie **przybornika** i **PropertyGrid** okienka i dodaj je do rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Odwołania, kod, który powinien znajdować się w pliku MainWindow.xaml.cs po zakończeniu trzech zadania w programie [Rehosting projektanta przepływów pracy](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) serii tematów znajduje się na końcu tego tematu.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Aby utworzyć przybornika i dodać go do siatki  
  
1.  Otwórz projekt HostingApplication uzyskano, wykonując procedury opisane w sekcji [zadanie 2: Host projektanta przepływów pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).  
  
2.  W **Eksploratora rozwiązań** okienku kliknij prawym przyciskiem myszy plik MainWindow.xaml i wybierz **kod widoku**.  
  
3.  Dodaj `GetToolboxControl` metodę `MainWindow` klasy, która tworzy <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, dodaje nową **przybornika** kategorię, aby **przybornika**i przypisuje <xref:System.Activities.Statements.Assign> i <xref:System.Activities.Statements.Sequence> typy działań do tej kategorii.  
  
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
  
4.  Dodaj prywatnej `AddToolbox` metodę `MainWindow` klasy, który umieszcza **przybornika** w lewej kolumnie siatki.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  Dodaj wywołanie do `AddToolBox` metoda `MainWindow()` konstruktora klasy, jak pokazano w poniższym kodzie.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązania. **Przybornika** zawierający <xref:System.Activities.Statements.Assign> i <xref:System.Activities.Statements.Sequence> działania powinny być wyświetlane.  
  
### <a name="to-create-the-propertygrid"></a>Aby utworzyć PropertyGrid  
  
1.  W **Eksploratora rozwiązań** okienku kliknij prawym przyciskiem myszy plik MainWindow.xaml i wybierz **kod widoku**.  
  
2.  Dodaj `AddPropertyInspector` metodę `MainWindow` klasę, aby umieścić **PropertyGrid** okienka w ostatniej kolumnie siatki.  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  Dodaj wywołanie do `AddPropertyInspector` metoda `MainWindow()` konstruktora klasy, jak pokazano w poniższym kodzie.  
  
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
  
4.  Naciśnij klawisz F5, aby skompilować i uruchomić rozwiązanie. **Przybornika**, kanwy projektu przepływu pracy, i **PropertyGrid** okienka powinny być wyświetlane wszystkie i przeciągnięcie <xref:System.Activities.Statements.Assign> działania lub <xref:System.Activities.Statements.Sequence> działania na kanwę projektu siatki właściwości, należy zaktualizować w zależności od wyróżnione działania.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Rehostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Zadanie 1: Tworzenie nowej aplikacji Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [Zadanie 2: Hostowanie projektanta przepływu pracy](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
