---
title: "Jak pobrać dane w konkretnym formacie danych"
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
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e6513fd6d8d443b76059626c0e40991e35830c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a>Jak pobrać dane w konkretnym formacie danych
Poniższe przykłady pokazują, jak można pobrać danych z obiektu danych w określonym formacie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeładowania najpierw sprawdź, czy określone dane formatu jest dostępna (natywnie lub automatyczną konwersję); Jeśli określony format jest dostępny, przykładzie pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29> metody.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> przeciążenia, aby najpierw sprawdzić, czy format określonych danych jest dostępna natywnie (dane możliwe do przekonwertowania automatycznie formaty są filtrowane); Jeśli określony format jest dostępny, przykładzie pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29>metody.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.IDataObject>  
 [Przeciągnij i upuść — omówienie](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
