---
title: 'Instrukcje: Określanie, czy format danych jest obecny w obiekcie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: 4cec733490e2a9dc5d54b3b253ac38a5090ac885
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776249"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a><span data-ttu-id="c72fa-102">Instrukcje: Określanie, czy format danych jest obecny w obiekcie danych</span><span class="sxs-lookup"><span data-stu-id="c72fa-102">How to: Determine if a Data Format is Present in a Data Object</span></span>
<span data-ttu-id="c72fa-103">W poniższych przykładach pokazano, jak używać różnych <xref:System.Windows.DataObject.GetDataPresent%2A> przeciążenia metod do wykonywania zapytań, czy w konkretnym formacie danych jest obecny w obiekcie danych.</span><span class="sxs-lookup"><span data-stu-id="c72fa-103">The following examples show how to use the various <xref:System.Windows.DataObject.GetDataPresent%2A> method overloads to query whether a particular data format is present in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c72fa-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c72fa-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c72fa-105">Opis</span><span class="sxs-lookup"><span data-stu-id="c72fa-105">Description</span></span>  
 <span data-ttu-id="c72fa-106">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeciążenia do wykonywania zapytań na obecność w konkretnym formacie danych w ciągu deskryptora.</span><span class="sxs-lookup"><span data-stu-id="c72fa-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to query for the presence of a particular data format by descriptor string.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c72fa-107">Kod</span><span class="sxs-lookup"><span data-stu-id="c72fa-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a><span data-ttu-id="c72fa-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c72fa-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c72fa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c72fa-109">Description</span></span>  
 <span data-ttu-id="c72fa-110">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> przeciążenia do wykonywania zapytań na obecność w konkretnym formacie danych według typu.</span><span class="sxs-lookup"><span data-stu-id="c72fa-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> overload to query for the presence of a particular data format by type.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c72fa-111">Kod</span><span class="sxs-lookup"><span data-stu-id="c72fa-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a><span data-ttu-id="c72fa-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c72fa-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c72fa-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c72fa-113">Description</span></span>  
 <span data-ttu-id="c72fa-114">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> przeciążenia Aby wysłać zapytanie o dane w ciągu deskryptora i określenie sposobu traktowania formatów danych automatycznie przekonwertować.</span><span class="sxs-lookup"><span data-stu-id="c72fa-114">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to query for data by descriptor string, and specifying how to treat auto-convertible data formats.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c72fa-115">Kod</span><span class="sxs-lookup"><span data-stu-id="c72fa-115">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a><span data-ttu-id="c72fa-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c72fa-116">See also</span></span>

- <xref:System.Windows.IDataObject>
