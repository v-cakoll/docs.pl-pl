---
title: 'Porady: tworzenie złożonego interfejsu użytkownika z formularzami Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6011eb2d49e537a2f5dfc540611af40a30b3e721
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a><span data-ttu-id="57d14-102">Porady: tworzenie złożonego interfejsu użytkownika z formularzami Windows</span><span class="sxs-lookup"><span data-stu-id="57d14-102">How to: Create a Multipane User Interface with Windows Forms</span></span>
<span data-ttu-id="57d14-103">W poniższej procedurze utworzysz złożonego interfejsu użytkownika podobny do tego używanego w programie Microsoft Outlook z **folderu** listy **wiadomości** okienku i **wwersjizapoznawczej** okienka.</span><span class="sxs-lookup"><span data-stu-id="57d14-103">In the following procedure, you will create a multipane user interface that is similar to the one used in Microsoft Outlook, with a **Folder** list, a **Messages** pane, and a **Preview** pane.</span></span> <span data-ttu-id="57d14-104">To rozmieszczenie odbywa się głównie za pośrednictwem dokowanie formantów w formularzu.</span><span class="sxs-lookup"><span data-stu-id="57d14-104">This arrangement is achieved chiefly through docking controls with the form.</span></span>  
  
 <span data-ttu-id="57d14-105">Dokowanie formantu, określić, które krawędzią kontenera nadrzędnego formantu jest podłączony.</span><span class="sxs-lookup"><span data-stu-id="57d14-105">When you dock a control, you determine which edge of the parent container a control is fastened to.</span></span> <span data-ttu-id="57d14-106">W związku z tym Jeśli ustawisz <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Right>, prawą krawędzią formantu zostanie zadokowane do prawej krawędzi kontrolki nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="57d14-106">Thus, if you set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Right>, the right edge of the control will be docked to the right edge of its parent control.</span></span> <span data-ttu-id="57d14-107">Ponadto zadokowanych krawędzią formantu jest zmieniany na zgodny z jego formantu kontenera.</span><span class="sxs-lookup"><span data-stu-id="57d14-107">Additionally, the docked edge of the control is resized to match that of its container control.</span></span> <span data-ttu-id="57d14-108">Aby uzyskać więcej informacji na temat sposobu <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości znaleźć [porady: dokowania formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="57d14-108">For more information about how the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property works, see [How to: Dock Controls on Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).</span></span>  
  
 <span data-ttu-id="57d14-109">Ta procedura polega na rozmieszczanie <xref:System.Windows.Forms.SplitContainer> i innych kontrolek w formularzu, a nie na dodawanie funkcji, aby aplikacja naśladować Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="57d14-109">This procedure focuses on arranging the <xref:System.Windows.Forms.SplitContainer> and the other controls on the form, not on adding functionality to make the application mimic Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="57d14-110">Aby utworzyć ten interfejs użytkownika, umieść wszystkie formanty w <xref:System.Windows.Forms.SplitContainer> formant, który zawiera <xref:System.Windows.Forms.TreeView> kontroli w lewym panelu.</span><span class="sxs-lookup"><span data-stu-id="57d14-110">To create this user interface, you place all the controls within a <xref:System.Windows.Forms.SplitContainer> control, which contains a <xref:System.Windows.Forms.TreeView> control in the left-hand panel.</span></span> <span data-ttu-id="57d14-111">Na prawym panelu <xref:System.Windows.Forms.SplitContainer> formant zawiera drugi <xref:System.Windows.Forms.SplitContainer> sterować za pomocą <xref:System.Windows.Forms.ListView> powyższej kontrolki <xref:System.Windows.Forms.RichTextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="57d14-111">The right-hand panel of the <xref:System.Windows.Forms.SplitContainer> control contains a second <xref:System.Windows.Forms.SplitContainer> control with a <xref:System.Windows.Forms.ListView> control above a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="57d14-112">Te <xref:System.Windows.Forms.SplitContainer> formanty włączyć niezależne zmiana rozmiaru formantów w formularzu.</span><span class="sxs-lookup"><span data-stu-id="57d14-112">These <xref:System.Windows.Forms.SplitContainer> controls enable independent resizing of the other controls on the form.</span></span> <span data-ttu-id="57d14-113">Istnieje możliwość dostosowania technik w ramach tej procedury, aby jednostki niestandardowych interfejsów użytkownika własny.</span><span class="sxs-lookup"><span data-stu-id="57d14-113">You can adapt the techniques in this procedure to craft custom user interfaces of your own.</span></span>  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a><span data-ttu-id="57d14-114">Aby programowo utworzyć interfejsu użytkownika w stylu programu Outlook</span><span class="sxs-lookup"><span data-stu-id="57d14-114">To create an Outlook-style user interface programmatically</span></span>  
  
1.  <span data-ttu-id="57d14-115">W formularzu należy zadeklarować każdego formantu, który składa się z interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="57d14-115">Within a form, declare each control that comprises your user interface.</span></span> <span data-ttu-id="57d14-116">Na przykład użyć <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, i <xref:System.Windows.Forms.RichTextBox> formantów, aby naśladował interfejsu użytkownika programu Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="57d14-116">For this example, use the <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, and <xref:System.Windows.Forms.RichTextBox> controls to mimic the Microsoft Outlook user interface.</span></span>  
  
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
  
2.  <span data-ttu-id="57d14-117">Tworzenie procedury, która definiuje interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="57d14-117">Create a procedure that defines your user interface.</span></span> <span data-ttu-id="57d14-118">Poniższy kod ustawia właściwości, aby formularz będzie podobny interfejsu użytkownika w programie Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="57d14-118">The following code sets the properties so that the form will resemble the user interface in Microsoft Outlook.</span></span> <span data-ttu-id="57d14-119">Jednak za pomocą innych mechanizmów kontroli lub dokowanie je inaczej, jest tak proste utworzyć inne interfejsy użytkownika, które są równie elastyczne.</span><span class="sxs-lookup"><span data-stu-id="57d14-119">However, by using other controls or docking them differently, it is just as easy to create other user interfaces that are equally flexible.</span></span>  
  
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
  
3.  <span data-ttu-id="57d14-120">W języku Visual Basic, dodaj wywołanie do procedury nowo utworzoną `New()` procedury.</span><span class="sxs-lookup"><span data-stu-id="57d14-120">In Visual Basic, add a call to the procedure you just created in the `New()` procedure.</span></span> <span data-ttu-id="57d14-121">W środowisku Visual C#, Dodaj następujący wiersz kodu do konstruktora dla klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="57d14-121">In Visual C#, add this line of code to the constructor for the form class.</span></span>  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="57d14-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57d14-122">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="57d14-123">SplitContainer, kontrolka</span><span class="sxs-lookup"><span data-stu-id="57d14-123">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [<span data-ttu-id="57d14-124">Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="57d14-124">How to: Create a Multipane User Interface with Windows Forms Using the Designer</span></span>](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)
