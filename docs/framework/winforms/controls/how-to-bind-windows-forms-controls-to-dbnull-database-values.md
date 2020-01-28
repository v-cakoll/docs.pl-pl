---
title: Powiązywanie kontrolek z wartościami bazy danych DBNull
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746661"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="2adda-102">Porady: powiązanie formantów formularzy systemu Windows z wartościami bazy danych DBNull</span><span class="sxs-lookup"><span data-stu-id="2adda-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="2adda-103">Po powiązaniu Windows Forms formantów ze źródłem danych, gdy źródło danych zwróci wartość <xref:System.DBNull>, można zastąpić odpowiednią wartość bez obsługi, formatowania lub analizowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2adda-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="2adda-104">Właściwość <xref:System.Windows.Forms.Binding.NullValue%2A> będzie konwertowana <xref:System.DBNull> do określonego obiektu podczas formatowania lub analizowania wartości źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2adda-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2adda-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2adda-105">Example</span></span>  
 <span data-ttu-id="2adda-106">Poniższy przykład ilustruje sposób powiązania wartości <xref:System.DBNull> w dwóch różnych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="2adda-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="2adda-107">Pierwszy pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> dla właściwości ciągu; Drugi pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> dla właściwości obrazu.</span><span class="sxs-lookup"><span data-stu-id="2adda-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="2adda-108">Typy powiązanej właściwości i właściwości <xref:System.Windows.Forms.Binding.NullValue%2A> muszą być takie same lub mogą wystąpić błędy, a żadne dalsze wartości <xref:System.Windows.Forms.Binding.NullValue%2A> nie zostaną przetworzone.</span><span class="sxs-lookup"><span data-stu-id="2adda-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="2adda-109">W tej sytuacji wyjątek nie zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="2adda-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2adda-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2adda-110">Compiling the Code</span></span>  
 <span data-ttu-id="2adda-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2adda-111">This example requires:</span></span>  
  
- <span data-ttu-id="2adda-112">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="2adda-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2adda-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2adda-113">See also</span></span>

- [<span data-ttu-id="2adda-114">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="2adda-114">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="2adda-115">Instrukcje: obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="2adda-115">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="2adda-116">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="2adda-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
