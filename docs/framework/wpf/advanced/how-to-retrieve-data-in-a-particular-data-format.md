---
title: Jak pobrać dane w konkretnym formacie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: 405fff1b586207249fbabafb28791ffa2901cf49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545110"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="4d337-102">Jak pobrać dane w konkretnym formacie danych</span><span class="sxs-lookup"><span data-stu-id="4d337-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="4d337-103">Poniższe przykłady pokazują, jak można pobrać danych z obiektu danych w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="4d337-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d337-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d337-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4d337-105">Opis</span><span class="sxs-lookup"><span data-stu-id="4d337-105">Description</span></span>  
 <span data-ttu-id="4d337-106">Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeładowania najpierw sprawdź, czy określone dane formatu jest dostępna (natywnie lub automatyczną konwersję); Jeśli określony format jest dostępny, przykładzie pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29> metody.</span><span class="sxs-lookup"><span data-stu-id="4d337-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4d337-107">Kod</span><span class="sxs-lookup"><span data-stu-id="4d337-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="4d337-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d337-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4d337-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4d337-109">Description</span></span>  
 <span data-ttu-id="4d337-110">Poniższy przykład kodu wykorzystuje <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> przeciążenia, aby najpierw sprawdzić, czy format określonych danych jest dostępna natywnie (dane możliwe do przekonwertowania automatycznie formaty są filtrowane); Jeśli określony format jest dostępny, przykładzie pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29>metody.</span><span class="sxs-lookup"><span data-stu-id="4d337-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4d337-111">Kod</span><span class="sxs-lookup"><span data-stu-id="4d337-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="4d337-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d337-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="4d337-113">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="4d337-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
