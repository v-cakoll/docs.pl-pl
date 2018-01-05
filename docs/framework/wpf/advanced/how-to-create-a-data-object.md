---
title: "Jak utworzyć obiekt danych"
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
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 014d5229026a6fdaab203c82932742c7b2c7639e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-object"></a><span data-ttu-id="f1f98-102">Jak utworzyć obiekt danych</span><span class="sxs-lookup"><span data-stu-id="f1f98-102">How to: Create a Data Object</span></span>
<span data-ttu-id="f1f98-103">W poniższych przykładach pokazano różne sposoby tworzenia obiektu danych za pomocą konstruktorów podał <xref:System.Windows.DataObject> klasy.</span><span class="sxs-lookup"><span data-stu-id="f1f98-103">The following examples show various ways to create a data object using the constructors provided by the <xref:System.Windows.DataObject> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1f98-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1f98-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f1f98-105">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f98-105">Description</span></span>  
 <span data-ttu-id="f1f98-106">Poniższy przykładowy kod tworzy nowy obiekt danych i korzysta z jednego z konstruktorów przeciążone (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) do inicjalizacji obiektu danych z ciągiem.</span><span class="sxs-lookup"><span data-stu-id="f1f98-106">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) to initialize the data object with a string.</span></span>  <span data-ttu-id="f1f98-107">W takim przypadku format danych jest ustalany automatycznie zgodnie z typem przechowywanych danych i domyślnie automatyczna konwersja przechowywanych danych jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="f1f98-107">In this case, an appropriate data format is determined automatically according to the stored data's type, and auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f1f98-108">Kod</span><span class="sxs-lookup"><span data-stu-id="f1f98-108">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a><span data-ttu-id="f1f98-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f98-109">Description</span></span>  
 <span data-ttu-id="f1f98-110">Poniższy przykładowy kod jest zmniejszoną wersję kodzie pokazanym powyżej.</span><span class="sxs-lookup"><span data-stu-id="f1f98-110">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f1f98-111">Kod</span><span class="sxs-lookup"><span data-stu-id="f1f98-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a><span data-ttu-id="f1f98-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1f98-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f1f98-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f98-113">Description</span></span>  
 <span data-ttu-id="f1f98-114">Poniższy przykładowy kod tworzy nowy obiekt danych i korzysta z jednego z konstruktorów przeciążone (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) do inicjalizacji obiektu dane z ciągu i format określonych danych.</span><span class="sxs-lookup"><span data-stu-id="f1f98-114">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="f1f98-115">W takim przypadku format danych jest określona przez ciąg. <xref:System.Windows.DataFormats> klasa udostępnia zestaw ciągów wstępnie zdefiniowanego typu.</span><span class="sxs-lookup"><span data-stu-id="f1f98-115">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="f1f98-116">Automatyczna konwersja przechowywanych danych jest dozwolone domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f1f98-116">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f1f98-117">Kod</span><span class="sxs-lookup"><span data-stu-id="f1f98-117">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a><span data-ttu-id="f1f98-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f98-118">Description</span></span>  
 <span data-ttu-id="f1f98-119">Poniższy przykładowy kod jest zmniejszoną wersję kodzie pokazanym powyżej.</span><span class="sxs-lookup"><span data-stu-id="f1f98-119">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f1f98-120">Kod</span><span class="sxs-lookup"><span data-stu-id="f1f98-120">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a><span data-ttu-id="f1f98-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1f98-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f1f98-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f98-122">Description</span></span>  
 <span data-ttu-id="f1f98-123">Poniższy przykładowy kod tworzy nowy obiekt danych i korzysta z jednego z konstruktorów przeciążone (<xref:System.Windows.DataObject.%23ctor%2A>) do inicjalizacji obiektu dane z ciągu i format określonych danych.</span><span class="sxs-lookup"><span data-stu-id="f1f98-123">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%2A>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="f1f98-124">W takim przypadku format danych jest określony przez <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="f1f98-124">In this case the data format is specified by a <xref:System.Type> parameter.</span></span>  <span data-ttu-id="f1f98-125">Automatyczna konwersja przechowywanych danych jest dozwolone domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f1f98-125">Auto-converting of the stored data is allowed by default.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f1f98-126">Kod</span><span class="sxs-lookup"><span data-stu-id="f1f98-126">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a><span data-ttu-id="f1f98-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f98-127">Description</span></span>  
 <span data-ttu-id="f1f98-128">Poniższy przykładowy kod jest zmniejszoną wersję kodzie pokazanym powyżej.</span><span class="sxs-lookup"><span data-stu-id="f1f98-128">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f1f98-129">Kod</span><span class="sxs-lookup"><span data-stu-id="f1f98-129">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a><span data-ttu-id="f1f98-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1f98-130">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f1f98-131">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f98-131">Description</span></span>  
 <span data-ttu-id="f1f98-132">Poniższy przykładowy kod tworzy nowy obiekt danych i korzysta z jednego z konstruktorów przeciążone (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) do inicjalizacji obiektu dane z ciągu i format określonych danych.</span><span class="sxs-lookup"><span data-stu-id="f1f98-132">The following example code creates a new data object and uses one of the overloaded constructors (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) to initialize the data object with a string and a specified data format.</span></span>  <span data-ttu-id="f1f98-133">W takim przypadku format danych jest określona przez ciąg. <xref:System.Windows.DataFormats> klasa udostępnia zestaw ciągów wstępnie zdefiniowanego typu.</span><span class="sxs-lookup"><span data-stu-id="f1f98-133">In this case the data format is specified by a string; the <xref:System.Windows.DataFormats> class provides a set of pre-defined type strings.</span></span> <span data-ttu-id="f1f98-134">To przeciążenie określonego konstruktora umożliwia obiekt wywołujący, aby określić, czy automatyczna konwersja jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="f1f98-134">This particular constructor overload enables the caller to specify whether auto-converting is allowed.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f1f98-135">Kod</span><span class="sxs-lookup"><span data-stu-id="f1f98-135">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a><span data-ttu-id="f1f98-136">Opis</span><span class="sxs-lookup"><span data-stu-id="f1f98-136">Description</span></span>  
 <span data-ttu-id="f1f98-137">Poniższy przykładowy kod jest zmniejszoną wersję kodzie pokazanym powyżej.</span><span class="sxs-lookup"><span data-stu-id="f1f98-137">The following example code is a condensed version of the code shown above.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f1f98-138">Kod</span><span class="sxs-lookup"><span data-stu-id="f1f98-138">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a><span data-ttu-id="f1f98-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1f98-139">See Also</span></span>  
 <xref:System.Windows.IDataObject>
