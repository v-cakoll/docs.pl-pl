---
title: 'Instrukcje: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d76c2e5882c9df94674294da00ba446dfbfd2b3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086523"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="b63bd-102">Instrukcje: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b63bd-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="b63bd-103">Podczas tworzenia aplikacji opartych na danych, często konieczne będzie wyświetlana użytkownikom zbiory danych.</span><span class="sxs-lookup"><span data-stu-id="b63bd-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="b63bd-104"><xref:System.Windows.Forms.BindingNavigator> Kontroli w połączeniu z <xref:System.Windows.Forms.BindingSource> składnik udostępnia wygodne i umożliwiające rozbudowę rozwiązanie do przenoszenia wszystkich elementów w kolekcji i wyświetlanie elementów po kolei.</span><span class="sxs-lookup"><span data-stu-id="b63bd-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b63bd-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b63bd-105">Example</span></span>  
 <span data-ttu-id="b63bd-106">Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.BindingNavigator> sterowania, aby przeglądać dane.</span><span class="sxs-lookup"><span data-stu-id="b63bd-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="b63bd-107">Zestaw jest zawarty w <xref:System.Data.DataView>, która jest powiązana <xref:System.Windows.Forms.TextBox> kontrolką <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="b63bd-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b63bd-108">Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b63bd-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="b63bd-109">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b63bd-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="b63bd-110">Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="b63bd-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b63bd-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b63bd-111">Compiling the Code</span></span>  
 <span data-ttu-id="b63bd-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b63bd-112">This example requires:</span></span>  
  
-   <span data-ttu-id="b63bd-113">Odwołania do zestawów systemu, dane systemowe, System.Drawing, przestrzeń nazw System.Windows.Forms i System.Xml.</span><span class="sxs-lookup"><span data-stu-id="b63bd-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="b63bd-114">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b63bd-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b63bd-115">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="b63bd-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63bd-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b63bd-116">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="b63bd-117">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b63bd-117">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="b63bd-118">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="b63bd-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="b63bd-119">Instrukcje: Powiązanie z typem formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b63bd-119">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
