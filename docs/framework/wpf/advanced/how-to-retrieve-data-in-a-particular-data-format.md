---
title: 'Instrukcje: Pobierz dane w konkretnym formacie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: d11374cbc70210e648e93a385c4a9fbca112c09f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718302"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="63da4-102">Instrukcje: Pobierz dane w konkretnym formacie danych</span><span class="sxs-lookup"><span data-stu-id="63da4-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="63da4-103">Poniższe przykłady pokazują, jak można pobrać danych z obiektu danych w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="63da4-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63da4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="63da4-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="63da4-105">Opis</span><span class="sxs-lookup"><span data-stu-id="63da4-105">Description</span></span>  
 <span data-ttu-id="63da4-106">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeładowania najpierw sprawdzić, jeśli określone dane formatu jest dostępna (natywnej lub automatyczna konwersja); Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29> metody.</span><span class="sxs-lookup"><span data-stu-id="63da4-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="63da4-107">Kod</span><span class="sxs-lookup"><span data-stu-id="63da4-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="63da4-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="63da4-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="63da4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="63da4-109">Description</span></span>  
 <span data-ttu-id="63da4-110">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> przeładowania najpierw sprawdź, czy format danych określony jest natywnie dostępny (formaty danych automatycznie przekonwertować są filtrowane); Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29>metody.</span><span class="sxs-lookup"><span data-stu-id="63da4-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="63da4-111">Kod</span><span class="sxs-lookup"><span data-stu-id="63da4-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="63da4-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63da4-112">See also</span></span>
- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="63da4-113">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="63da4-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
