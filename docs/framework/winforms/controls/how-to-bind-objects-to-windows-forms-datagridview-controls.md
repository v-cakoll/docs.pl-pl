---
title: 'Instrukcje: powiązanie obiektów z kontrolkami DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 8cdfd5d8e5ec3dcd22abb9e4efcec3bb61fee1d9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591318"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="cf720-102">Instrukcje: powiązanie obiektów z kontrolkami DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cf720-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="cf720-103">Poniższy przykład kodu pokazuje, jak powiązać kolekcji obiektów do <xref:System.Windows.Forms.DataGridView> sterowania, aby każdy obiekt jest wyświetlany jako oddzielny wiersz.</span><span class="sxs-lookup"><span data-stu-id="cf720-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="cf720-104">Ten przykład ilustruje także sposób wyświetlania właściwości dla typu wyliczenia w <xref:System.Windows.Forms.DataGridViewComboBoxColumn> tak, aby listy rozwijanej pola kombi zawiera wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cf720-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf720-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf720-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cf720-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cf720-106">Compiling the Code</span></span>  
 <span data-ttu-id="cf720-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="cf720-107">This example requires:</span></span>  
  
- <span data-ttu-id="cf720-108">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="cf720-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf720-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf720-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="cf720-110">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf720-110">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="cf720-111">Instrukcje: Uzyskiwanie dostępu do obiektów powiązanych z Windows Forms wierszami formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="cf720-111">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
