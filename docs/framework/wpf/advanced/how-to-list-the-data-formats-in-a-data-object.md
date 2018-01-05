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
ms.workload: dotnet
ms.openlocfilehash: cb27928031b551da2957aab0696646e8adc3f803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="07a34-102">Jak wykazać formaty danych w obiekcie danych</span><span class="sxs-lookup"><span data-stu-id="07a34-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="07a34-103">W poniższych przykładach pokazano, jak używać <xref:System.Windows.DataObject.GetFormats%2A> przeciążenia metody get tablica ciągów określające każdego format danych jest dostępna w obiekcie danych.</span><span class="sxs-lookup"><span data-stu-id="07a34-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07a34-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="07a34-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="07a34-105">Opis</span><span class="sxs-lookup"><span data-stu-id="07a34-105">Description</span></span>  
 <span data-ttu-id="07a34-106">Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetFormats%2A> przeciążenia uzyskać tablicę ciągów określające wszystkie formaty danych dostępne w obiekcie danych (natywny i możliwe do przekonwertowania automatycznie).</span><span class="sxs-lookup"><span data-stu-id="07a34-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="07a34-107">Kod</span><span class="sxs-lookup"><span data-stu-id="07a34-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="07a34-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="07a34-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="07a34-109">Opis</span><span class="sxs-lookup"><span data-stu-id="07a34-109">Description</span></span>  
 <span data-ttu-id="07a34-110">Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetFormats%2A> przeciążenia uzyskać tablicę ciągów określające tylko formaty danych dostępnych w obiekcie danych (dane możliwe do przekonwertowania automatycznie formaty są filtrowane).</span><span class="sxs-lookup"><span data-stu-id="07a34-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="07a34-111">Kod</span><span class="sxs-lookup"><span data-stu-id="07a34-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="07a34-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07a34-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="07a34-113">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="07a34-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
