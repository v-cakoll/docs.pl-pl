---
title: Tworzenie wielookienkowego interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], examples
- ListView control [Windows Forms], examples
- RichTextBox control [Windows Forms], examples
- Panel control [Windows Forms], examples
- TreeView control [Windows Forms], examples
- Splitter control [Windows Forms], examples
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
ms.openlocfilehash: 4b168a6d566e20814d4403f90e157d80efe3bf12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731337"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a>Porady: tworzenie złożonego interfejsu użytkownika z formularzami Windows
Poniższa procedura umożliwia utworzenie wielookienkowego interfejsu użytkownika, który jest podobny do tego, który jest używany w programie Microsoft Outlook, z listą **folderów** , okienkiem **wiadomości** i okienkiem **podglądu** . To rozwiązanie jest uzyskiwane głównie przez dokowanie kontrolek za pomocą formularza.  
  
 Po zadokowanym formancie należy określić, z której krawędzią kontenera nadrzędnego jest przymocowany formant. W takim przypadku, jeśli ustawisz właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Right>, prawą krawędzią kontrolki będzie zadokowany do prawej krawędzi jego kontrolki nadrzędnej. Ponadto zostanie zmieniony rozmiar zadokowanej krawędzi kontrolki w celu dopasowania jej do kontrolki kontenera. Aby uzyskać więcej informacji na temat działania właściwości <xref:System.Windows.Forms.SplitContainer.Dock%2A>, zobacz [How to: Docking Controls on Windows Forms](how-to-dock-controls-on-windows-forms.md).  
  
 Ta procedura koncentruje się na układaniu <xref:System.Windows.Forms.SplitContainer> i innych kontrolek w formularzu, a nie na dodawaniu funkcji, aby aplikacja naśladuje program Microsoft Outlook.  
  
 Aby utworzyć ten interfejs użytkownika, należy umieścić wszystkie kontrolki w kontrolce <xref:System.Windows.Forms.SplitContainer>, która zawiera kontrolkę <xref:System.Windows.Forms.TreeView> w panelu po lewej stronie. Panel po prawej stronie kontrolki <xref:System.Windows.Forms.SplitContainer> zawiera drugą kontrolkę <xref:System.Windows.Forms.SplitContainer> z kontrolką <xref:System.Windows.Forms.ListView> nad formantem <xref:System.Windows.Forms.RichTextBox>. Te <xref:System.Windows.Forms.SplitContainer> formantów umożliwiają niezależne zmienianie rozmiarów innych kontrolek w formularzu. Można dostosować techniki w tej procedurze, aby nawiązać własne niestandardowe interfejsy użytkownika.  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a>Aby programowo utworzyć interfejs użytkownika w stylu programu Outlook  
  
1. W formularzu Zadeklaruj każdą kontrolkę, która składa się z interfejsu użytkownika. W tym przykładzie Użyj kontrolek <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>i <xref:System.Windows.Forms.RichTextBox>, aby naśladować interfejs użytkownika programu Microsoft Outlook.  
  
    ```vb  
    Private WithEvents treeView1 As System.Windows.Forms.TreeView  
    Private WithEvents listView1 As System.Windows.Forms.ListView  
    Private WithEvents richTextBox1 As System.Windows.Forms.RichTextBox  
    Private WithEvents splitContainer1 As _  
        System.Windows.Forms.SplitContainer  
    Private WithEvents splitContainer2 As _  
        System.Windows.Forms.SplitContainer  
    ```  
  
    ```csharp  
    private System.Windows.Forms.TreeView treeView1;  
    private System.Windows.Forms.ListView listView1;  
    private System.Windows.Forms.RichTextBox richTextBox1;  
    private System.Windows.Forms. SplitContainer splitContainer2;  
    private System.Windows.Forms. SplitContainer splitContainer1;  
    ```  
  
2. Utwórz procedurę, która definiuje interfejs użytkownika. Poniższy kod ustawia właściwości tak, aby formularz wyglądał podobnie do interfejsu użytkownika w programie Microsoft Outlook. Jednak przy użyciu innych kontrolek lub zadokowanie ich inaczej jest równie proste, aby można było tworzyć inne interfejsy użytkownika, które są równie elastyczne.  
  
    ```vb  
    Public Sub CreateOutlookUI()  
        ' Create an instance of each control being used.  
        Me.components = New System.ComponentModel.Container()  
        Me.treeView1 = New System.Windows.Forms.TreeView()  
        Me.listView1 = New System.Windows.Forms.ListView()  
        Me.richTextBox1 = New System.Windows.Forms.RichTextBox()  
        Me.splitContainer1 = New System.Windows.Forms.SplitContainer()  
        Me.splitContainer2= New System.Windows.Forms. SplitContainer()  
  
        ' Should you develop this into a working application,  
        ' use the AddHandler method to hook up event procedures here.  
  
        ' Set properties of TreeView control.  
        ' Use the With statement to avoid repetitive code.  
        With Me.treeView1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 0  
            .Nodes.Add("treeView")  
        End With  
  
    ' Set properties of ListView control.  
       With Me.listView1  
          .Dock = System.Windows.Forms.DockStyle.Top  
          .TabIndex = 2  
          .Items.Add("listView")  
       End With  
  
    ' Set properties of RichTextBox control.  
       With Me.richTextBox1  
          .Dock = System.Windows.Forms.DockStyle.Fill  
          .TabIndex = 3  
          .Text = "richTextBox1"  
       End With  
  
        ' Set properties of the first SplitContainer control.  
        With Me.splitContainer1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 1  
            .SplitterWidth = 4  
            .SplitterDistance = 150  
            .Orientation = Orientation.Horizontal  
            .Panel1.Controls.Add(Me.listView1)  
            .Panel2.Controls.Add(Me.richTextBox1)  
    End With  
  
        ' Set properties of the second SplitContainer control.  
        With Me.splitContainer2  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 4  
            .SplitterWidth = 4  
            .SplitterDistance = 100  
            .Panel1.Controls.Add(Me.treeView1)  
            .Panel2.Controls.Add(Me.SplitContainer1)  
    End With  
  
    ' Add the main SplitContainer control to the form.  
        Me.Controls.Add(Me.splitContainer2)  
        Me.Text = "Intricate UI Example"  
    End Sub  
    ```  
  
    ```csharp  
    public void createOutlookUI()  
    {  
        // Create an instance of each control being used.  
        treeView1 = new System.Windows.Forms.TreeView();  
        listView1 = new System.Windows.Forms.ListView();  
        richTextBox1 = new System.Windows.Forms.RichTextBox();  
        splitContainer2 = new System.Windows.Forms.SplitContainer();  
        splitContainer1 = new System.Windows.Forms.SplitContainer();  
  
        // Insert code here to hook up event methods.  
  
        // Set properties of TreeView control.  
        treeView1.Dock = System.Windows.Forms.DockStyle.Fill;  
        treeView1.TabIndex = 0;  
        treeView1.Nodes.Add("treeView");  
  
        // Set properties of ListView control.  
        listView1.Dock = System.Windows.Forms.DockStyle.Top;  
        listView1.TabIndex = 2;  
        listView1.Items.Add("listView");  
  
        // Set properties of RichTextBox control.  
        richTextBox1.Dock = System.Windows.Forms.DockStyle.Fill;  
        richTextBox1.TabIndex = 3;  
        richTextBox1.Text = "richTextBox1";  
  
        // Set properties of first SplitContainer control.  
        splitContainer1.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 1;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 150;  
        splitContainer2.Orientation = Orientation.Horizontal;  
        splitContainer2.Panel1.Controls.Add(this.listView1);  
        splitContainer2.Panel1.Controls.Add(this.richTextBox1);  
  
        // Set properties of second SplitContainer control.  
        splitContainer2.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 4;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 100;  
        splitContainer2.Panel1.Controls.Add(this.treeView1);  
        splitContainer2.Panel1.Controls.Add(this.splitContainer1);  
  
        // Add the main SplitContainer control to the form.  
        this.Controls.Add(this.splitContainer2);  
        this.Text = "Intricate UI Example";  
    }  
    ```  
  
3. W Visual Basic Dodaj wywołanie do procedury, która została właśnie utworzona w procedurze `New()`. W wizualizacji C#Dodaj ten wiersz kodu do konstruktora dla klasy form.  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer, kontrolka](splitcontainer-control-windows-forms.md)
- [Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami Windows Forms przy użyciu narzędzia Projektant](create-a-multipane-user-interface-with-wf-using-the-designer.md)
