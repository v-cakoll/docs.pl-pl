---
title: Wiązanie obiektów z kontrolkami DataGridView
description: Dowiedz się, jak powiązać kolekcję obiektów z Windows Forms kontrolką DataGridView, aby każdy obiekt był wyświetlany jako osobny wiersz.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: add0047937b404dcec1ea12bac8053bb9bdfcf1c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325866"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="95192-103">Porady: powiązanie obiektów z formantami DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="95192-103">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="95192-104">Poniższy przykład kodu demonstruje sposób powiązania kolekcji obiektów z <xref:System.Windows.Forms.DataGridView> kontrolką tak, aby każdy obiekt był wyświetlany jako osobny wiersz.</span><span class="sxs-lookup"><span data-stu-id="95192-104">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="95192-105">Ten przykład ilustruje również sposób wyświetlania właściwości z typem wyliczenia w, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> tak że lista rozwijana pola kombi zawiera wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="95192-105">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95192-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="95192-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95192-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="95192-107">Compiling the Code</span></span>  
 <span data-ttu-id="95192-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="95192-108">This example requires:</span></span>  
  
- <span data-ttu-id="95192-109">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="95192-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95192-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95192-110">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="95192-111">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95192-111">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="95192-112">Instrukcje: uzyskiwanie dostępu do obiektów powiązanych z wierszami kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95192-112">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
