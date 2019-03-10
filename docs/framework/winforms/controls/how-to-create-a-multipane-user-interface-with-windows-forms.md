---
title: 'Instrukcje: Tworzenie złożonego interfejsu użytkownika z formularzami Windows'
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
ms.openlocfilehash: 4db424b27af09dcb7def0051fba070fe9ccf0491
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721973"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a>Instrukcje: Tworzenie złożonego interfejsu użytkownika z formularzami Windows
W poniższej procedurze utworzysz złożonego interfejsu użytkownika podobny do komentarzowi użytemu w programie Microsoft Outlook przy użyciu **folderu** listy **wiadomości** okienku i **wwersjizapoznawczej** okienka. Taki układ odbywa się głównie za pośrednictwem dokowanie kontrolek za pomocą formularza.  
  
 Po zadokowaniu kontrolkę, należy określić, które krawędzią kontenera nadrzędnego formantu jest podłączony. W związku z tym Jeśli ustawisz <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Right>, prawą krawędzią kontrolki będzie zadokowany na prawej krawędzi kontrolki nadrzędnej. Ponadto aby pasował do jego kontrolki kontenera zmieniany jest zadokowany krawędzią formantu. Aby uzyskać więcej informacji o tym, jak <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość znaleźć [jak: Dokowanie formantów na formularzach Windows Forms](how-to-dock-controls-on-windows-forms.md).  
  
 Ta procedura polega na rozmieszczanie <xref:System.Windows.Forms.SplitContainer> i inne kontrolki na formularzu, a nie na dodawanie funkcji do aplikacji Microsoft Outlook naśladować.  
  
 Aby utworzyć ten interfejs użytkownika, umieść wszystkie kontrolki w ramach <xref:System.Windows.Forms.SplitContainer> formant, który zawiera <xref:System.Windows.Forms.TreeView> kontrolki w panelu po lewej stronie. Na panelu po prawej stronie <xref:System.Windows.Forms.SplitContainer> kontrolka zawiera sekundy <xref:System.Windows.Forms.SplitContainer> kontrolką <xref:System.Windows.Forms.ListView> kontrolki powyżej <xref:System.Windows.Forms.RichTextBox> kontroli. Te <xref:System.Windows.Forms.SplitContainer> kontrolki umożliwiają, niezależnie od rozmiaru formantów w formularzu. Możliwość dostosowania technik w tej procedurze, aby tworzenie niestandardowych interfejsów użytkownika samodzielnie.  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a>Aby utworzyć programowo interfejsu użytkownika w stylu programu Outlook  
  
1.  W formularzu należy zadeklarować każdego formantu, który składa się z poziomu interfejsu użytkownika. W tym przykładzie użyj <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, i <xref:System.Windows.Forms.RichTextBox> formantów, aby mógł naśladować interfejsu użytkownika programu Microsoft Outlook.  
  
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
  
2.  Tworzenie procedury, która definiuje interfejs użytkownika. Poniższy kod ustawia właściwości, dzięki czemu formularz będzie przypominał interfejsu użytkownika w programie Microsoft Outlook. Jednak za pomocą innych formantów lub dokowanie ich inaczej, jest równie proste do tworzenia innych interfejsów użytkownika, które są równie elastyczne.  
  
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
  
3.  W języku Visual Basic należy dodać wywołanie procedury nowo utworzoną `New()` procedury. W elemencie wizualnym C#, Dodaj następujący wiersz kodu do konstruktora dla klasy formularza.  
  
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
- [Instrukcje: Tworzenie złożonego interfejsu użytkownika za pomocą interfejsu Windows Forms przy użyciu narzędzia Projektant](create-a-multipane-user-interface-with-wf-using-the-designer.md)
