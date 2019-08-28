---
title: 'Instrukcje: wybieranie folderów za pomocą składnika FolderBrowserDialog formularzy systemu Windows'
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
ms.openlocfilehash: fc19ea466f535f783d3b0537a973ce41c223902d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046137"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="26a64-102">Instrukcje: wybieranie folderów za pomocą składnika FolderBrowserDialog formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="26a64-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>

<span data-ttu-id="26a64-103">Często w aplikacjach systemu Windows tworzone są monity użytkowników o wybranie folderu, najczęściej w celu zapisania zestawu plików.</span><span class="sxs-lookup"><span data-stu-id="26a64-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="26a64-104">Składnik Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> pozwala łatwo wykonać to zadanie.</span><span class="sxs-lookup"><span data-stu-id="26a64-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="26a64-105">Aby wybrać foldery ze składnikiem FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="26a64-105">To choose folders with the FolderBrowserDialog component</span></span>

1. <span data-ttu-id="26a64-106">W <xref:System.Windows.Forms.FolderBrowserDialog> procedurze Sprawdź <xref:System.Windows.Forms.Form.DialogResult%2A> Właściwość składnika, aby zobaczyć, jak okno dialogowe zostało zamknięte i <xref:System.Windows.Forms.FolderBrowserDialog> pobrać <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> wartość właściwości składnika.</span><span class="sxs-lookup"><span data-stu-id="26a64-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>

2. <span data-ttu-id="26a64-107">Jeśli musisz ustawić górny folder, który będzie wyświetlany w widoku drzewa okna dialogowego, ustaw <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> właściwość, która przyjmuje element członkowski <xref:System.Environment.SpecialFolder> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="26a64-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>

3. <span data-ttu-id="26a64-108">Ponadto można ustawić <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> właściwość, która określa ciąg tekstowy, który pojawia się w górnej części widoku drzewa folderów.</span><span class="sxs-lookup"><span data-stu-id="26a64-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>

    <span data-ttu-id="26a64-109">W poniższym <xref:System.Windows.Forms.FolderBrowserDialog> przykładzie składnik jest używany do wybrania folderu, podobnie jak podczas tworzenia projektu w programie Visual Studio i zostanie wyświetlony monit o wybranie folderu w celu zapisania go w programie.</span><span class="sxs-lookup"><span data-stu-id="26a64-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="26a64-110">W tym przykładzie nazwa folderu jest następnie wyświetlana w <xref:System.Windows.Forms.TextBox> kontrolce formularza.</span><span class="sxs-lookup"><span data-stu-id="26a64-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="26a64-111">Dobrym pomysłem jest umieszczenie lokalizacji w obszarze edytowalnym, takim jak <xref:System.Windows.Forms.TextBox> kontrolka, dzięki czemu użytkownicy mogą edytować wybór w przypadku wystąpienia błędu lub innych problemów.</span><span class="sxs-lookup"><span data-stu-id="26a64-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="26a64-112">W tym przykładzie przyjęto, że <xref:System.Windows.Forms.FolderBrowserDialog> formularz ze składnikiem <xref:System.Windows.Forms.TextBox> i kontrolką.</span><span class="sxs-lookup"><span data-stu-id="26a64-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>

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
    > <span data-ttu-id="26a64-113">Aby użyć tej klasy, zestaw wymaga poziomu uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> właściwość, która jest częścią <xref:System.Security.Permissions.FileIOPermissionAccess> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="26a64-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="26a64-114">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="26a64-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="26a64-115">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="26a64-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="26a64-116">Aby uzyskać informacje na temat sposobu zapisywania plików, [zobacz How to: Zapisz pliki przy użyciu składnika](how-to-save-files-using-the-savefiledialog-component.md)SaveFileDialog.</span><span class="sxs-lookup"><span data-stu-id="26a64-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26a64-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26a64-117">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="26a64-118">FolderBrowserDialog, składnik — omówienie (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="26a64-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="26a64-119">FolderBrowserDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="26a64-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
