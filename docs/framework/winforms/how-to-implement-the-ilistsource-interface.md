---
title: 'Instrukcje: Implementowanie interfejsu IListSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], implementing
- IListSource interface
ms.assetid: 63ce27aa-2e23-4fbd-8228-0c1726f6c421
ms.openlocfilehash: 331abebf3336d8444559c117f5747597bc3b0122
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728216"
---
# <a name="how-to-implement-the-ilistsource-interface"></a><span data-ttu-id="fa5aa-102">Instrukcje: Implementowanie interfejsu IListSource</span><span class="sxs-lookup"><span data-stu-id="fa5aa-102">How to: Implement the IListSource Interface</span></span>
<span data-ttu-id="fa5aa-103">Implementowanie <xref:System.ComponentModel.IListSource> interfejsu do utworzenia możliwej do wiązania klasy, który nie implementuje <xref:System.Collections.IList> , ale zamiast tego zawiera listę z innej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="fa5aa-103">Implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class that does not implement <xref:System.Collections.IList> but instead provides a list from another location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa5aa-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa5aa-104">Example</span></span>  
 <span data-ttu-id="fa5aa-105">Poniższy przykład kodu demonstruje sposób implementacji <xref:System.ComponentModel.IListSource> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fa5aa-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.IListSource> interface.</span></span> <span data-ttu-id="fa5aa-106">Składnik o nazwie `EmployeeListSource` udostępnia <xref:System.Collections.IList> dla powiązania danych poprzez implementację <xref:System.ComponentModel.IListSource.GetList%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fa5aa-106">A component named `EmployeeListSource` exposes an <xref:System.Collections.IList> for data binding by implementing the <xref:System.ComponentModel.IListSource.GetList%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.IListSource#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/EmployeeListSource.cs#1)]
 [!code-vb[System.ComponentModel.IListSource#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/EmployeeListSource.vb#1)]  
  
 [!code-csharp[System.ComponentModel.IListSource#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Employee.cs#10)]
 [!code-vb[System.ComponentModel.IListSource#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Employee.vb#10)]  
  
 [!code-csharp[System.ComponentModel.IListSource#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/BusinessObjectBase.cs#100)]
 [!code-vb[System.ComponentModel.IListSource#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/BusinessObjectBase.vb#100)]  
  
 [!code-csharp[System.ComponentModel.IListSource#1000](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Form1.cs#1000)]
 [!code-vb[System.ComponentModel.IListSource#1000](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Form1.vb#1000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa5aa-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fa5aa-107">Compiling the Code</span></span>  
 <span data-ttu-id="fa5aa-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="fa5aa-108">This example requires:</span></span>  
  
-   <span data-ttu-id="fa5aa-109">Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="fa5aa-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa5aa-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa5aa-110">See also</span></span>
- <xref:System.ComponentModel.IListSource>
- <xref:System.ComponentModel.ITypedList>
- <xref:System.ComponentModel.BindingList%601>
- <xref:System.ComponentModel.IBindingList>
- [<span data-ttu-id="fa5aa-111">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fa5aa-111">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
