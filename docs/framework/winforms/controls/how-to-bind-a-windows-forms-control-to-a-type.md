---
title: Powiązywanie kontroli z typem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744985"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="5cc2e-102">Porady: powiązanie formantu formularzy systemu Windows z typem</span><span class="sxs-lookup"><span data-stu-id="5cc2e-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="5cc2e-103">Podczas kompilowania formantów, które współpracują z danymi, czasami trzeba będzie powiązać formant z typem, a nie obiektem.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="5cc2e-104">Ta sytuacja występuje szczególnie w czasie projektowania, gdy dane mogą nie być dostępne, ale kontrolki powiązane z danymi nadal muszą wyświetlać informacje z interfejsu publicznego typu.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="5cc2e-105">Na przykład można powiązać formant <xref:System.Windows.Forms.DataGridView> z obiektem uwidocznionym przez usługę sieci Web i chcieć, aby kontrolka <xref:System.Windows.Forms.DataGridView> mogła oznaczyć kolumny w czasie projektowania z nazwami elementów członkowskich typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="5cc2e-106">Można łatwo powiązać kontrolkę z typem ze składnikiem <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cc2e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cc2e-107">Example</span></span>  
 <span data-ttu-id="5cc2e-108">Poniższy przykład kodu demonstruje, jak powiązać formant <xref:System.Windows.Forms.DataGridView> z typem niestandardowym za pomocą składnika <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="5cc2e-109">Po uruchomieniu przykładu można zauważyć, że <xref:System.Windows.Forms.DataGridView> ma etykiety kolumn, które odzwierciedlają właściwości obiektu `Customer`, przed zapełnieniem formantu danymi.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="5cc2e-110">Przykład zawiera przycisk Dodaj klienta, aby dodać dane do kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5cc2e-111">Po kliknięciu przycisku do <xref:System.Windows.Forms.BindingSource>zostanie dodany nowy obiekt `Customer`.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="5cc2e-112">W rzeczywistym scenariuszu dane mogą zostać uzyskane przez wywołanie usługi sieci Web lub innego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cc2e-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5cc2e-113">Compiling the Code</span></span>  
 <span data-ttu-id="5cc2e-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5cc2e-114">This example requires:</span></span>  
  
- <span data-ttu-id="5cc2e-115">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="5cc2e-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc2e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cc2e-116">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="5cc2e-117">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="5cc2e-117">BindingSource Component</span></span>](bindingsource-component.md)
