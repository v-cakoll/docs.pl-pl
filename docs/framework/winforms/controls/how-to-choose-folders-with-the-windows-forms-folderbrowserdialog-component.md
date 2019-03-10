---
title: 'Instrukcje: Wybierz foldery, za pomocą składnika FolderBrowserDialog formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: ea5fdc9708d8e896eb66fa42f64cac672baff08b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724560"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="3e2d3-102">Instrukcje: Wybierz foldery, za pomocą składnika FolderBrowserDialog formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="3e2d3-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>
<span data-ttu-id="3e2d3-103">Często w aplikacji Windows, które tworzysz, trzeba będzie monitować użytkowników o wybranie folderu, większość często, aby zapisać zestawu plików.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="3e2d3-104">Formularze Windows <xref:System.Windows.Forms.FolderBrowserDialog> składnik umożliwia łatwe wykonać to zadanie.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="3e2d3-105">Aby wybrać foldery, za pomocą składnika FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="3e2d3-105">To choose folders with the FolderBrowserDialog component</span></span>  
  
1.  <span data-ttu-id="3e2d3-106">W procedurze, sprawdź <xref:System.Windows.Forms.FolderBrowserDialog> składnika <xref:System.Windows.Forms.Form.DialogResult%2A> właściwości, aby zobaczyć, jak zostało zamknięte okno dialogowe i uzyskać wartość <xref:System.Windows.Forms.FolderBrowserDialog> składnika <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>  
  
2.  <span data-ttu-id="3e2d3-107">Jeśli zachodzi potrzeba folderu zestawu najlepszy, która będzie wyświetlana w widoku drzewa okna dialogowego, ustaw <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> właściwość, która przyjmuje członkiem <xref:System.Environment.SpecialFolder> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>  
  
3.  <span data-ttu-id="3e2d3-108">Ponadto można ustawić <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> właściwość, która określa ciąg znaków, który pojawia się w górnej części widoku drzewa przeglądarka folderów.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>  
  
     <span data-ttu-id="3e2d3-109">W poniższym przykładzie <xref:System.Windows.Forms.FolderBrowserDialog> składnik jest używany do wybierania folderu, podobnie jak podczas tworzenia projektu w programie Visual Studio i monit o wybranie folderu do zapisania go w.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="3e2d3-110">W tym przykładzie nazwa folderu jest następnie wyświetlana w <xref:System.Windows.Forms.TextBox> formant w formularzu.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="3e2d3-111">To dobry pomysł, aby umieścić lokalizacji w obszarze można edytować, takich jak <xref:System.Windows.Forms.TextBox> kontrolować, dzięki czemu użytkownicy mogą edytować ich zaznaczenia w przypadku błędu lub innych kwestiach.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="3e2d3-112">W tym przykładzie przyjęto założenie, formularz z <xref:System.Windows.Forms.FolderBrowserDialog> składnika i <xref:System.Windows.Forms.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
    ```vb  
    Public Sub ChooseFolder()  
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then  
            TextBox1.Text = FolderBrowserDialog1.SelectedPath  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    public void ChooseFolder()  
    {  
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)   
        {  
            textBox1.Text = folderBrowserDialog1.SelectedPath;  
        }  
    }  
    ```  
  
    ```cpp  
    public:  
       void ChooseFolder()  
       {  
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Text = folderBrowserDialog1->SelectedPath;  
          }  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3e2d3-113">Aby użyć tej klasy, zestaw wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> właściwość, która jest częścią programu <xref:System.Security.Permissions.FileIOPermissionAccess> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="3e2d3-114">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="3e2d3-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="3e2d3-115">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="3e2d3-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="3e2d3-116">Aby uzyskać informacje na temat sposobu zapisywania plików, zobacz [jak: Zapisywanie plików za pomocą składnika SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="3e2d3-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e2d3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e2d3-117">See also</span></span>
- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="3e2d3-118">FolderBrowserDialog, składnik — omówienie (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3e2d3-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="3e2d3-119">FolderBrowserDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="3e2d3-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
