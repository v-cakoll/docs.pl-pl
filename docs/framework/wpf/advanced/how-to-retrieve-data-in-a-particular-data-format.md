---
title: 'Instrukcje: Uzyskiwanie danych w konkretnym formacie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: b3ec1b8fa873fd449956912e9e77e98b0362cb0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080023"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="ee2fe-102">Instrukcje: Uzyskiwanie danych w konkretnym formacie danych</span><span class="sxs-lookup"><span data-stu-id="ee2fe-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="ee2fe-103">Poniższe przykłady pokazują, jak można pobrać danych z obiektu danych w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="ee2fe-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee2fe-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee2fe-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ee2fe-105">Opis</span><span class="sxs-lookup"><span data-stu-id="ee2fe-105">Description</span></span>  
 <span data-ttu-id="ee2fe-106">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeładowania najpierw sprawdzić, jeśli określone dane formatu jest dostępna (natywnej lub automatyczna konwersja); Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29> metody.</span><span class="sxs-lookup"><span data-stu-id="ee2fe-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ee2fe-107">Kod</span><span class="sxs-lookup"><span data-stu-id="ee2fe-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="ee2fe-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee2fe-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ee2fe-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ee2fe-109">Description</span></span>  
 <span data-ttu-id="ee2fe-110">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> przeładowania najpierw sprawdź, czy format danych określony jest natywnie dostępny (formaty danych automatycznie przekonwertować są filtrowane); Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29>metody.</span><span class="sxs-lookup"><span data-stu-id="ee2fe-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ee2fe-111">Kod</span><span class="sxs-lookup"><span data-stu-id="ee2fe-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="ee2fe-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee2fe-112">See also</span></span>

- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="ee2fe-113">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="ee2fe-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
