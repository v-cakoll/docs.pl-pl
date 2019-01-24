---
title: 'Instrukcje: Przechowaj wiele formatów danych w obiekcie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], storing multiple formats
- DataFormats class [WPF], storing multiple formats
- drag-and-drop [WPF], storing multiple formats
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
ms.openlocfilehash: 33415dd3cb1a05263cf9fb9ecafcbc857d364d57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555677"
---
# <a name="how-to-store-multiple-data-formats-in-a-data-object"></a><span data-ttu-id="9e054-102">Instrukcje: Przechowaj wiele formatów danych w obiekcie danych</span><span class="sxs-lookup"><span data-stu-id="9e054-102">How to: Store Multiple Data Formats in a Data Object</span></span>
<span data-ttu-id="9e054-103">Poniższy przykład pokazuje, jak używać <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> metodę, aby dodać dane do obiektu danych w wielu formatach.</span><span class="sxs-lookup"><span data-stu-id="9e054-103">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e054-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e054-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9e054-105">Opis</span><span class="sxs-lookup"><span data-stu-id="9e054-105">Description</span></span>  
  
### <a name="code"></a><span data-ttu-id="9e054-106">Kod</span><span class="sxs-lookup"><span data-stu-id="9e054-106">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## <a name="see-also"></a><span data-ttu-id="9e054-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e054-107">See also</span></span>
- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="9e054-108">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="9e054-108">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
