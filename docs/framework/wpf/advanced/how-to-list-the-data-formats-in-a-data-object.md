---
title: "Jak wykazać formaty danych w obiekcie danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ef5657aefdf1c229b4f1749881cce1148435a8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a>Jak wykazać formaty danych w obiekcie danych
W poniższych przykładach pokazano, jak używać <xref:System.Windows.DataObject.GetFormats%2A> przeciążenia metody get tablica ciągów określające każdego format danych jest dostępna w obiekcie danych.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetFormats%2A> przeciążenia uzyskać tablicę ciągów określające wszystkie formaty danych dostępne w obiekcie danych (natywny i możliwe do przekonwertowania automatycznie).  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetFormats%2A> przeciążenia uzyskać tablicę ciągów określające tylko formaty danych dostępnych w obiekcie danych (dane możliwe do przekonwertowania automatycznie formaty są filtrowane).  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.IDataObject>  
 [Przeciągnij i upuść — omówienie](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
