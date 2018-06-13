---
title: Jak przechować wiele formatów danych w obiekcie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], storing multiple formats
- DataFormats class [WPF], storing multiple formats
- drag-and-drop [WPF], storing multiple formats
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
ms.openlocfilehash: e47d0aa2fe1c573314551ad91a2199ca97fd61a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543471"
---
# <a name="how-to-store-multiple-data-formats-in-a-data-object"></a>Jak przechować wiele formatów danych w obiekcie danych
Poniższy przykład przedstawia użycie <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> metody, aby dodać dane do obiektu danych w wielu formatach.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.IDataObject>  
 [Przegląd przeciągania i upuszczania](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
