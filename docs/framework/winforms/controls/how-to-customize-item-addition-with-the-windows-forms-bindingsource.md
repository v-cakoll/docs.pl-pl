---
title: 'Instrukcje: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 0a2f8491d0f027ca834257e2ec3a08d0b8bdb7ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129554"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="2687c-102">Instrukcje: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2687c-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="2687c-103">Kiedy używasz <xref:System.Windows.Forms.BindingSource> składnika, aby powiązać formant programu Windows Forms ze źródłem danych może okazać się konieczne dostosowanie tworzenia nowych elementów.</span><span class="sxs-lookup"><span data-stu-id="2687c-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="2687c-104"><xref:System.Windows.Forms.BindingSource> Ze składników zgłasza to prosta, zapewniając <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie, które zazwyczaj jest inicjowane, gdy formant związany potrzebne do utworzenia nowego elementu.</span><span class="sxs-lookup"><span data-stu-id="2687c-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="2687c-105">Procedury obsługi zdarzenia może zapewnić dowolne niestandardowe zachowanie jest wymagana (na przykład, wywołanie metody usługi sieci Web lub wprowadzenie nowego obiektu z fabryki klas).</span><span class="sxs-lookup"><span data-stu-id="2687c-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2687c-106">Gdy element zostanie dodany do obsługi <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzeń, nie można anulować dodawanie.</span><span class="sxs-lookup"><span data-stu-id="2687c-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2687c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2687c-107">Example</span></span>  
 <span data-ttu-id="2687c-108">Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Forms.DataGridView> kontrolki fabryki klas przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="2687c-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="2687c-109">Kiedy użytkownik kliknie <xref:System.Windows.Forms.DataGridView> kontrolki nowy wiersz <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="2687c-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="2687c-110">Program obsługi zdarzeń tworzy nową `DemoCustomer` obiektu, który jest przypisany do <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2687c-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="2687c-111">Powoduje to, że nowe `DemoCustomer` obiektów, które mają zostać dodane do <xref:System.Windows.Forms.BindingSource> listy składnika i mają być wyświetlane w nowym wierszu <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2687c-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2687c-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2687c-112">Compiling the Code</span></span>  
 <span data-ttu-id="2687c-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2687c-113">This example requires:</span></span>  
  
-   <span data-ttu-id="2687c-114">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2687c-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2687c-115">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2687c-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2687c-116">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="2687c-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2687c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2687c-117">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="2687c-118">BindingSource — Składnik</span><span class="sxs-lookup"><span data-stu-id="2687c-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="2687c-119">Instrukcje: powiązanie kontrolki formularzy systemu Windows z typem</span><span class="sxs-lookup"><span data-stu-id="2687c-119">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
