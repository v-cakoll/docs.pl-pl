---
title: 'Instrukcje: Wyświetlanie listy formatów danych w obiekcie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: f8230eac33a18a0d99cc757d54c2b901c1afe977
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077748"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="acea9-102">Instrukcje: Wyświetlanie listy formatów danych w obiekcie danych</span><span class="sxs-lookup"><span data-stu-id="acea9-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="acea9-103">W poniższych przykładach pokazano sposób użycia <xref:System.Windows.DataObject.GetFormats%2A> przeciążenia metody uzyskiwania tablicy ciągów oznaczający każdego format danych, która jest dostępna w obiekcie danych.</span><span class="sxs-lookup"><span data-stu-id="acea9-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acea9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="acea9-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="acea9-105">Opis</span><span class="sxs-lookup"><span data-stu-id="acea9-105">Description</span></span>  
 <span data-ttu-id="acea9-106">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetFormats%2A> przeciążenie, można pobrać tablicę ciągów, określające elementy w obiekcie danych (natywne i automatycznie przekonwertować) wszystkie formaty danych.</span><span class="sxs-lookup"><span data-stu-id="acea9-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="acea9-107">Kod</span><span class="sxs-lookup"><span data-stu-id="acea9-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="acea9-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="acea9-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="acea9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="acea9-109">Description</span></span>  
 <span data-ttu-id="acea9-110">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetFormats%2A> przeciążenie, można pobrać tablicę ciągów, określające elementy tylko formatów danych dostępnych w obiekcie danych (dane automatycznie przekonwertować formaty są filtrowane).</span><span class="sxs-lookup"><span data-stu-id="acea9-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="acea9-111">Kod</span><span class="sxs-lookup"><span data-stu-id="acea9-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="acea9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acea9-112">See also</span></span>

- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="acea9-113">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="acea9-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
