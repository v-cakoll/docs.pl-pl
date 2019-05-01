---
title: 'Instrukcje: obsługa błędów i wyjątków występujących za powodu powiązania danych'
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
ms.openlocfilehash: 709db2a98074e3322adad8b1275b3c4418c14636
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941274"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="3ac7d-102">Instrukcje: obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="3ac7d-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="3ac7d-103">Często wyjątków i błędów występujących na obiekty źródłowe firm gdy powiązanie z kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="3ac7d-104">Możesz przechwytywać te błędy i wyjątki i następnie odzyskać lub przekazać informacje o błędzie dla użytkownika, obsługując <xref:System.Windows.Forms.Binding.BindingComplete> zdarzeń dla określonego <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, lub <xref:System.Windows.Forms.CurrencyManager> składnika.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ac7d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ac7d-105">Example</span></span>  
 <span data-ttu-id="3ac7d-106">Ten przykład kodu demonstruje sposób obsługi błędów i wyjątków występujących podczas operacji powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="3ac7d-107">Demonstracja przechwytywać błędy obsługi <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> zdarzenia <xref:System.Windows.Forms.Binding> obiektów.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="3ac7d-108">Aby przechwycić błędów i wyjątków, obsługa tego zdarzenia, należy włączyć formatowania dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="3ac7d-109">Możesz włączyć formatowanie powiązania jest tworzony lub dodanie do kolekcji powiązania lub poprzez skonfigurowanie <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="3ac7d-110">Podczas wykonywania kodu i ciągiem pustym wprowadzonej w mniej niż 100 nazwę części lub wartość jest wprowadzana numeru części pojawi się okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="3ac7d-111">Jest to wynik obsługi <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> zdarzenia dla tych powiązań pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ac7d-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3ac7d-112">Compiling the Code</span></span>  
 <span data-ttu-id="3ac7d-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="3ac7d-113">This example requires:</span></span>  
  
- <span data-ttu-id="3ac7d-114">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3ac7d-115">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3ac7d-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3ac7d-116">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac7d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ac7d-117">See also</span></span>

- <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>
- [<span data-ttu-id="3ac7d-118">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="3ac7d-118">BindingSource Component</span></span>](bindingsource-component.md)
