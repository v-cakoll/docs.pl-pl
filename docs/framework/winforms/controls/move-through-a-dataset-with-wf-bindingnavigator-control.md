---
title: 'Porady: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 54cb04aefa8111873ca5c31ed94fe641437ae990
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537193"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="0b952-102">Porady: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0b952-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="0b952-103">Podczas tworzenia aplikacji opartych na danych, często konieczne będzie wyświetlana użytkownikom kolekcji danych.</span><span class="sxs-lookup"><span data-stu-id="0b952-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="0b952-104"><xref:System.Windows.Forms.BindingNavigator> Kontroli w połączeniu z <xref:System.Windows.Forms.BindingSource> składnika rozwiązaniem jest wygodne i rozszerzalny do przenoszenia do kolekcji i wyświetlanie elementów po kolei.</span><span class="sxs-lookup"><span data-stu-id="0b952-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b952-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b952-105">Example</span></span>  
 <span data-ttu-id="0b952-106">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Forms.BindingNavigator> formantu można przenieść za pomocą danych.</span><span class="sxs-lookup"><span data-stu-id="0b952-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="0b952-107">Zestaw znajduje się w <xref:System.Data.DataView>, która jest powiązana <xref:System.Windows.Forms.TextBox> sterować za pomocą <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="0b952-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b952-108">Przechowywanie poufne informacje, takie jak hasła, w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b952-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="0b952-109">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0b952-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="0b952-110">Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="0b952-110">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b952-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0b952-111">Compiling the Code</span></span>  
 <span data-ttu-id="0b952-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0b952-112">This example requires:</span></span>  
  
-   <span data-ttu-id="0b952-113">Odwołania do zestawów systemu, dane systemowe, System.Drawing, System.Windows.Forms i zestawów System.Xml.</span><span class="sxs-lookup"><span data-stu-id="0b952-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="0b952-114">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0b952-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0b952-115">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="0b952-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0b952-116">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0b952-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b952-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b952-117">See Also</span></span>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="0b952-118">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0b952-118">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="0b952-119">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="0b952-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="0b952-120">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="0b952-120">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
