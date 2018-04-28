---
title: 'Porady: powiązanie formantu formularzy systemu Windows z obiektem fabryki'
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
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c489227d12afd5e6d63a43c752ea97f06aa974e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="86dcb-102">Porady: powiązanie formantu formularzy systemu Windows z obiektem fabryki</span><span class="sxs-lookup"><span data-stu-id="86dcb-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="86dcb-103">Podczas tworzenia formantów, które współdziałają z danymi będą czasami jest konieczne do wiązania kontrolki do obiektu lub metodę, która generuje inne obiekty.</span><span class="sxs-lookup"><span data-stu-id="86dcb-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="86dcb-104">Obiekt lub metoda jest wywoływana fabrykę.</span><span class="sxs-lookup"><span data-stu-id="86dcb-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="86dcb-105">Źródło danych może być na przykład, wartość zwracana z wywołania metody, zamiast obiektu w pamięci lub typu.</span><span class="sxs-lookup"><span data-stu-id="86dcb-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="86dcb-106">Formant można powiązać z tym rodzajem źródła danych, tak długo, jak źródło zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="86dcb-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="86dcb-107">Można łatwo powiązanie formantu z obiektem fabryki, za pomocą <xref:System.Windows.Forms.BindingSource> formantu.</span><span class="sxs-lookup"><span data-stu-id="86dcb-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86dcb-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="86dcb-108">Example</span></span>  
 <span data-ttu-id="86dcb-109">W poniższym przykładzie pokazano, jak można powiązać <xref:System.Windows.Forms.DataGridView> formantu przy użyciu metody fabryki <xref:System.Windows.Forms.BindingSource> formantu.</span><span class="sxs-lookup"><span data-stu-id="86dcb-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="86dcb-110">Metoda fabryki nosi nazwę `GetOrdersByCustomerId`, i zwraca wszystkich zamówień klienta w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="86dcb-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="86dcb-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="86dcb-111">Compiling the Code</span></span>  
 <span data-ttu-id="86dcb-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="86dcb-112">This example requires:</span></span>  
  
-   <span data-ttu-id="86dcb-113">Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="86dcb-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="86dcb-114">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="86dcb-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="86dcb-115">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="86dcb-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="86dcb-116">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="86dcb-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86dcb-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86dcb-117">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="86dcb-118">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="86dcb-118">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="86dcb-119">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="86dcb-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
