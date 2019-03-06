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
ms.openlocfilehash: f759677d9aba51fc8a65f030be8ae19eea53c02e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379136"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="b6ff7-102">Instrukcje: Pobierz dane w konkretnym formacie danych</span><span class="sxs-lookup"><span data-stu-id="b6ff7-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="b6ff7-103">Poniższe przykłady pokazują, jak można pobrać danych z obiektu danych w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6ff7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6ff7-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b6ff7-105">Opis</span><span class="sxs-lookup"><span data-stu-id="b6ff7-105">Description</span></span>  
 <span data-ttu-id="b6ff7-106">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeładowania najpierw sprawdzić, jeśli określone dane formatu jest dostępna (natywnej lub automatyczna konwersja); Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29> metody.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b6ff7-107">Kod</span><span class="sxs-lookup"><span data-stu-id="b6ff7-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="b6ff7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6ff7-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b6ff7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b6ff7-109">Description</span></span>  
 <span data-ttu-id="b6ff7-110">Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> przeładowania najpierw sprawdź, czy format danych określony jest natywnie dostępny (formaty danych automatycznie przekonwertować są filtrowane); Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29>metody.</span><span class="sxs-lookup"><span data-stu-id="b6ff7-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b6ff7-111">Kod</span><span class="sxs-lookup"><span data-stu-id="b6ff7-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="b6ff7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6ff7-112">See also</span></span>
- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="b6ff7-113">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="b6ff7-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
