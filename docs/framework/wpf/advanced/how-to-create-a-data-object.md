---
title: 'Instrukcje: Tworzenie obiektu danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
ms.openlocfilehash: deae8751518d9322e8d924a1b1fcbc20e25b35ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121795"
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="8a21d-102">Instrukcje: Tworzenie obiektu danych</span><span class="sxs-lookup"><span data-stu-id="8a21d-102">How to: Create a Data Object</span></span>
<span data-ttu-id="8a21d-103">W poniższych przykładach pokazano różne sposoby tworzenia obiektu danych za pomocą konstruktorów, dostarczone przez <xref:System.Windows.DataObject> klasy.</span><span class="sxs-lookup"><span data-stu-id="8a21d-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a21d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a21d-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a21d-105">Opis</span><span class="sxs-lookup"><span data-stu-id="8a21d-105">Description</span></span>  
 <span data-ttu-id="8a21d-106">Poniższy przykład kodu tworzy nowy obiekt danych i używa jednego z przeciążenia konstruktorów (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) do inicjalizacji obiektu danych przy użyciu parametrów.</span><span class="sxs-lookup"><span data-stu-id="8a21d-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="8a21d-107">W takim przypadku na format danych jest określana automatycznie zgodnie z typem przechowywanych danych i automatyczna konwersja przechowywanych danych jest domyślnie dozwolone.</span><span class="sxs-lookup"><span data-stu-id="8a21d-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a21d-108">Kod</span><span class="sxs-lookup"><span data-stu-id="8a21d-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="8a21d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8a21d-109">Description</span></span>  
 <span data-ttu-id="8a21d-110">Poniższy przykład kodu jest skrócona wersja kodu powyżej.</span><span class="sxs-lookup"><span data-stu-id="8a21d-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a21d-111">Kod</span><span class="sxs-lookup"><span data-stu-id="8a21d-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="8a21d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a21d-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a21d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8a21d-113">Description</span></span>  
 <span data-ttu-id="8a21d-114">Poniższy przykład kodu tworzy nowy obiekt danych i używa jednego z przeciążenia konstruktorów (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) do inicjalizacji obiektu danych przy użyciu ciągu i format określone dane.</span><span class="sxs-lookup"><span data-stu-id="8a21d-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="8a21d-115">W tym przypadku format danych jest określona przez ciąg; <xref:System.Windows.DataFormats> klasa oferuje zestaw wstępnie zdefiniowanych typów ciągów.</span><span class="sxs-lookup"><span data-stu-id="8a21d-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="8a21d-116">Automatyczna konwersja przechowywanych danych jest domyślnie dozwolone.</span><span class="sxs-lookup"><span data-stu-id="8a21d-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a21d-117">Kod</span><span class="sxs-lookup"><span data-stu-id="8a21d-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="8a21d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="8a21d-118">Description</span></span>  
 <span data-ttu-id="8a21d-119">Poniższy przykład kodu jest skrócona wersja kodu powyżej.</span><span class="sxs-lookup"><span data-stu-id="8a21d-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a21d-120">Kod</span><span class="sxs-lookup"><span data-stu-id="8a21d-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="8a21d-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a21d-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a21d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="8a21d-122">Description</span></span>  
 <span data-ttu-id="8a21d-123">Poniższy przykład kodu tworzy nowy obiekt danych i używa jednego z przeciążenia konstruktorów (<xref:System.Windows.DataObject.%23ctor%2A>) do inicjalizacji obiektu danych przy użyciu ciągu i format określone dane.</span><span class="sxs-lookup"><span data-stu-id="8a21d-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="8a21d-124">W tym przypadku format danych jest określony przez <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="8a21d-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="8a21d-125">Automatyczna konwersja przechowywanych danych jest domyślnie dozwolone.</span><span class="sxs-lookup"><span data-stu-id="8a21d-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a21d-126">Kod</span><span class="sxs-lookup"><span data-stu-id="8a21d-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="8a21d-127">Opis</span><span class="sxs-lookup"><span data-stu-id="8a21d-127">Description</span></span>  
 <span data-ttu-id="8a21d-128">Poniższy przykład kodu jest skrócona wersja kodu powyżej.</span><span class="sxs-lookup"><span data-stu-id="8a21d-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a21d-129">Kod</span><span class="sxs-lookup"><span data-stu-id="8a21d-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="8a21d-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a21d-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a21d-131">Opis</span><span class="sxs-lookup"><span data-stu-id="8a21d-131">Description</span></span>  
 <span data-ttu-id="8a21d-132">Poniższy przykład kodu tworzy nowy obiekt danych i używa jednego z przeciążenia konstruktorów (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) do inicjalizacji obiektu danych przy użyciu ciągu i format określone dane.</span><span class="sxs-lookup"><span data-stu-id="8a21d-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="8a21d-133">W tym przypadku format danych jest określona przez ciąg; <xref:System.Windows.DataFormats> klasa oferuje zestaw wstępnie zdefiniowanych typów ciągów.</span><span class="sxs-lookup"><span data-stu-id="8a21d-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="8a21d-134">Tego przeciążenia konstruktora określonego umożliwia obiektowi wywołującemu określenie, czy automatyczna konwersja jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="8a21d-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a21d-135">Kod</span><span class="sxs-lookup"><span data-stu-id="8a21d-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="8a21d-136">Opis</span><span class="sxs-lookup"><span data-stu-id="8a21d-136">Description</span></span>  
 <span data-ttu-id="8a21d-137">Poniższy przykład kodu jest skrócona wersja kodu powyżej.</span><span class="sxs-lookup"><span data-stu-id="8a21d-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a21d-138">Kod</span><span class="sxs-lookup"><span data-stu-id="8a21d-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="8a21d-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a21d-139">See also</span></span>

- <xref:System.Windows.IDataObject>
