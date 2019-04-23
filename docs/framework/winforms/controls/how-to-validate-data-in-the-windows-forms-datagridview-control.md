---
title: 'Instrukcje: sprawdzanie poprawności danych w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: dae254c14790841b37162fca9f998be429006125
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225615"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7c59a-102">Instrukcje: sprawdzanie poprawności danych w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7c59a-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7c59a-103">Poniższy przykład kodu demonstruje sposób sprawdzania poprawności danych wprowadzanych przez użytkownika do <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7c59a-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7c59a-104">W tym przykładzie <xref:System.Windows.Forms.DataGridView> jest wypełniana przy użyciu wierszy z `Customers` tabelę w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c59a-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="7c59a-105">Gdy użytkownik edytuje komórkę w `CompanyName` kolumny, jego wartość jest sprawdzane pod kątem ważności, sprawdzając, czy nie jest pusty.</span><span class="sxs-lookup"><span data-stu-id="7c59a-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="7c59a-106">Jeśli program obsługi zdarzeń dla <xref:System.Windows.Forms.DataGridView.CellValidating> zdarzeń wykryje, że wartość jest ciągiem pustym <xref:System.Windows.Forms.DataGridView> uniemożliwia użytkownikowi zamykania komórki, dopóki nie podano niepustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="7c59a-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="7c59a-107">Aby uzyskać pełne wyjaśnienie ten przykład kodu, zobacz [instruktażu: Sprawdzanie poprawności danych w Windows formantu DataGridView formularzy](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7c59a-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c59a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c59a-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c59a-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7c59a-109">Compiling the Code</span></span>  
 <span data-ttu-id="7c59a-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7c59a-110">This example requires:</span></span>  
  
-   <span data-ttu-id="7c59a-111">Odwołania do zestawów systemu, dane systemowe, przestrzeń nazw System.Windows.Forms i System.XML.</span><span class="sxs-lookup"><span data-stu-id="7c59a-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="7c59a-112">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7c59a-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7c59a-113">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="7c59a-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7c59a-114">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7c59a-114">.NET Framework Security</span></span>  
 <span data-ttu-id="7c59a-115">Przechowywanie poufnych informacji, takich jak hasła, w ciągu połączenia mogą wpływać na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7c59a-115">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="7c59a-116">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7c59a-116">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="7c59a-117">Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="7c59a-117">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c59a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c59a-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="7c59a-119">Przewodnik: Sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c59a-119">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7c59a-120">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c59a-120">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7c59a-121">Przewodnik: Obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7c59a-121">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="7c59a-122">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="7c59a-122">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
