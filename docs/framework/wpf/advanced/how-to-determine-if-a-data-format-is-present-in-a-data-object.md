---
title: "Jak określić, czy format danych jest obecny w obiekcie danych"
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
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9e5eaad64e18ff955340a8e91bfe8bd0e09dd8d7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a><span data-ttu-id="ad9a3-102">Jak określić, czy format danych jest obecny w obiekcie danych</span><span class="sxs-lookup"><span data-stu-id="ad9a3-102">How to: Determine if a Data Format is Present in a Data Object</span></span>
<span data-ttu-id="ad9a3-103">W poniższych przykładach pokazano, jak używać różnych <xref:System.Windows.DataObject.GetDataPresent%2A> przeciążanie metod do zapytania, czy format danych znajduje się w obiekcie danych.</span><span class="sxs-lookup"><span data-stu-id="ad9a3-103">The following examples show how to use the various <xref:System.Windows.DataObject.GetDataPresent%2A> method overloads to query whether a particular data format is present in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad9a3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad9a3-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ad9a3-105">Opis</span><span class="sxs-lookup"><span data-stu-id="ad9a3-105">Description</span></span>  
 <span data-ttu-id="ad9a3-106">Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeciążenia zapytania na obecność formatu danych w ciągu deskryptora.</span><span class="sxs-lookup"><span data-stu-id="ad9a3-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to query for the presence of a particular data format by descriptor string.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ad9a3-107">Kod</span><span class="sxs-lookup"><span data-stu-id="ad9a3-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a><span data-ttu-id="ad9a3-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad9a3-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ad9a3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ad9a3-109">Description</span></span>  
 <span data-ttu-id="ad9a3-110">Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> przeciążenia zapytania na obecność format danych określonego typu.</span><span class="sxs-lookup"><span data-stu-id="ad9a3-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> overload to query for the presence of a particular data format by type.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ad9a3-111">Kod</span><span class="sxs-lookup"><span data-stu-id="ad9a3-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a><span data-ttu-id="ad9a3-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad9a3-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ad9a3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ad9a3-113">Description</span></span>  
 <span data-ttu-id="ad9a3-114">Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> przeciążenia zapytania dla danych w ciągu deskryptora i określenie sposobu traktowania formaty danych auto-możliwe do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="ad9a3-114">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to query for data by descriptor string, and specifying how to treat auto-convertible data formats.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ad9a3-115">Kod</span><span class="sxs-lookup"><span data-stu-id="ad9a3-115">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a><span data-ttu-id="ad9a3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad9a3-116">See Also</span></span>  
 <xref:System.Windows.IDataObject>
