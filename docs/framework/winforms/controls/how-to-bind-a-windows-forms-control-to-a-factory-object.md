---
title: 'Instrukcje: powiązanie kontrolki formularzy systemu Windows z obiektem fabryki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2de892d94afdfcdc580d20f90fb60ebabf4a9b37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093036"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="90c56-102">Instrukcje: powiązanie kontrolki formularzy systemu Windows z obiektem fabryki</span><span class="sxs-lookup"><span data-stu-id="90c56-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="90c56-103">Podczas tworzenia formantów, które współdziałają z danymi będą czasami jest konieczne powiązać formant z obiektem lub metodę, która generuje innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="90c56-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="90c56-104">Obiekt lub metoda jest wywoływana fabrykę.</span><span class="sxs-lookup"><span data-stu-id="90c56-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="90c56-105">Źródło danych może być na przykład, wartość zwracana z wywołania metody, zamiast obiektu w pamięci lub typu.</span><span class="sxs-lookup"><span data-stu-id="90c56-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="90c56-106">Kontrolki można powiązać z tym rodzajem źródła danych, tak długo, jak źródło zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="90c56-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="90c56-107">Można łatwo powiązać formant z obiektem fabryki, korzystając z <xref:System.Windows.Forms.BindingSource> kontroli.</span><span class="sxs-lookup"><span data-stu-id="90c56-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90c56-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="90c56-108">Example</span></span>  
 <span data-ttu-id="90c56-109">Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Forms.DataGridView> kontrolki metoda fabryki, korzystając z <xref:System.Windows.Forms.BindingSource> kontroli.</span><span class="sxs-lookup"><span data-stu-id="90c56-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="90c56-110">Metoda fabryki nosi nazwę `GetOrdersByCustomerId`, i zwraca wszystkie zamówienia dla danego klienta w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="90c56-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="90c56-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="90c56-111">Compiling the Code</span></span>  
 <span data-ttu-id="90c56-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="90c56-112">This example requires:</span></span>  
  
-   <span data-ttu-id="90c56-113">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="90c56-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="90c56-114">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="90c56-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="90c56-115">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="90c56-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c56-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90c56-116">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="90c56-117">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="90c56-117">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="90c56-118">Instrukcje: Powiązanie z typem formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="90c56-118">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
