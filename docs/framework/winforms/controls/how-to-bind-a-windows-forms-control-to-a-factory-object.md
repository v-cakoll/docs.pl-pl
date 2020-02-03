---
title: Powiązywanie kontroli z obiektem fabryki
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
ms.openlocfilehash: 2b4d9aca3345a0cb1e7e995f66a8982dee983ca8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745094"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="dd62c-102">Porady: powiązanie formantu formularzy systemu Windows z obiektem fabryki</span><span class="sxs-lookup"><span data-stu-id="dd62c-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="dd62c-103">Podczas kompilowania formantów, które współpracują z danymi, czasami trzeba będzie powiązać formant z obiektem lub metodą, która generuje inne obiekty.</span><span class="sxs-lookup"><span data-stu-id="dd62c-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="dd62c-104">Taki obiekt lub metoda nazywa się fabryką.</span><span class="sxs-lookup"><span data-stu-id="dd62c-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="dd62c-105">Źródło danych może być na przykład wartością zwracaną z wywołania metody zamiast obiektu w pamięci lub typu.</span><span class="sxs-lookup"><span data-stu-id="dd62c-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="dd62c-106">Można powiązać kontrolkę z tym rodzajem źródła danych, o ile Źródło zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="dd62c-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="dd62c-107">Można łatwo powiązać formant z obiektem fabryki przy użyciu kontrolki <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="dd62c-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd62c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd62c-108">Example</span></span>  
 <span data-ttu-id="dd62c-109">Poniższy przykład ilustruje sposób powiązania formantu <xref:System.Windows.Forms.DataGridView> z metodą fabryki przy użyciu kontrolki <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="dd62c-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="dd62c-110">Metoda Factory ma nazwę `GetOrdersByCustomerId`i zwraca wszystkie zamówienia dla danego klienta w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="dd62c-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dd62c-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="dd62c-111">Compiling the Code</span></span>  
 <span data-ttu-id="dd62c-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="dd62c-112">This example requires:</span></span>  
  
- <span data-ttu-id="dd62c-113">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="dd62c-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd62c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd62c-114">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="dd62c-115">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="dd62c-115">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="dd62c-116">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="dd62c-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
