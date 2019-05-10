---
title: 'Instrukcje: Implementowanie interfejsu ITypedList'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ITypedList interface
- BindingList(Of T) class
- data binding [Windows Forms], implementing
- IBindingList interface
ms.assetid: 834cc15c-50bc-4a8b-a610-313d6a217357
ms.openlocfilehash: 3f5a5032166087c7398d310071b3998c845e2780
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630740"
---
# <a name="how-to-implement-the-itypedlist-interface"></a><span data-ttu-id="91633-102">Instrukcje: Implementowanie interfejsu ITypedList</span><span class="sxs-lookup"><span data-stu-id="91633-102">How to: Implement the ITypedList Interface</span></span>
<span data-ttu-id="91633-103">Implementowanie <xref:System.ComponentModel.ITypedList> interfejsu, aby włączyć odnajdywanie schematu dla listy może być powiązana.</span><span class="sxs-lookup"><span data-stu-id="91633-103">Implement the <xref:System.ComponentModel.ITypedList> interface to enable discovery of the schema for a bindable list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91633-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="91633-104">Example</span></span>  
 <span data-ttu-id="91633-105">Poniższy przykład kodu demonstruje sposób implementacji <xref:System.ComponentModel.ITypedList> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="91633-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="91633-106">Typ ogólny, o nazwie `SortableBindingList` pochodzi od klasy <xref:System.ComponentModel.BindingList%601> klasy i implementuje <xref:System.ComponentModel.ITypedList> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="91633-106">A generic type named `SortableBindingList` derives from the <xref:System.ComponentModel.BindingList%601> class and implements the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="91633-107">Prostą klasę o nazwie `Customer` udostępnia dane, który jest powiązany z nagłówka <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="91633-107">A simple class named `Customer` provides data, which is bound to the header of a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="91633-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="91633-108">Compiling the Code</span></span>  
 <span data-ttu-id="91633-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="91633-109">This example requires:</span></span>  
  
- <span data-ttu-id="91633-110">Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="91633-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91633-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91633-111">See also</span></span>

- <xref:System.ComponentModel.ITypedList>
- <xref:System.ComponentModel.BindingList%601>
- <xref:System.ComponentModel.IBindingList>
- [<span data-ttu-id="91633-112">Wiązanie danych i formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91633-112">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
