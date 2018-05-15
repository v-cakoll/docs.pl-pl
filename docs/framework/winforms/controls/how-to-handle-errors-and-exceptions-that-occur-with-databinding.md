---
title: 'Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
ms.openlocfilehash: c7c05eb8d858c1f911e148def1c714e3caf74c95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="76ccb-102">Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="76ccb-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="76ccb-103">Często wyjątków i błędów są dokonywane na podstawowym obiektów biznesowych gdy związane z formantami.</span><span class="sxs-lookup"><span data-stu-id="76ccb-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="76ccb-104">Można przechwycić te błędy i wyjątki, a następnie odzyskać lub przekazać informacje o błędzie dla użytkownika obsługa <xref:System.Windows.Forms.Binding.BindingComplete> zdarzenia dla konkretnej <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, lub <xref:System.Windows.Forms.CurrencyManager> składnika.</span><span class="sxs-lookup"><span data-stu-id="76ccb-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76ccb-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="76ccb-105">Example</span></span>  
 <span data-ttu-id="76ccb-106">Ten przykład kodu pokazuje sposób obsługi błędów i wyjątków występujących podczas operacji wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="76ccb-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="76ccb-107">Demonstracja przechwycić błędy Obsługa <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> zdarzenie <xref:System.Windows.Forms.Binding> obiektów.</span><span class="sxs-lookup"><span data-stu-id="76ccb-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="76ccb-108">Aby przechwycić błędy i wyjątki przez Obsługa tego zdarzenia, należy włączyć formatowania dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="76ccb-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="76ccb-109">Można włączyć formatowania powiązania jest zbudowanych lub dodanie do kolekcji powiązanie lub przez ustawienie <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="76ccb-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="76ccb-110">Podczas wykonywania kodu, a pusty ciąg została wprowadzona nazwa części lub wartość mniejsza niż 100 jest wprowadzono numer części pojawi się komunikat.</span><span class="sxs-lookup"><span data-stu-id="76ccb-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="76ccb-111">Jest to wynik Obsługa <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> zdarzenia dla tych powiązań pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="76ccb-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76ccb-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="76ccb-112">Compiling the Code</span></span>  
 <span data-ttu-id="76ccb-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="76ccb-113">This example requires:</span></span>  
  
-   <span data-ttu-id="76ccb-114">Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="76ccb-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="76ccb-115">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="76ccb-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="76ccb-116">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="76ccb-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="76ccb-117">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="76ccb-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ccb-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76ccb-118">See Also</span></span>  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [<span data-ttu-id="76ccb-119">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="76ccb-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
