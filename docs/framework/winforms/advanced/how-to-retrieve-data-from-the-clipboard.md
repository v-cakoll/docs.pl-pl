---
title: 'Porady: pobieranie danych ze schowka'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c009efe743865896341da268bd14bf24158df46d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a><span data-ttu-id="b4dd8-102">Porady: pobieranie danych ze schowka</span><span class="sxs-lookup"><span data-stu-id="b4dd8-102">How to: Retrieve Data from the Clipboard</span></span>
<span data-ttu-id="b4dd8-103"><xref:System.Windows.Forms.Clipboard> Klasa dostarcza metody, które służy do interakcji z funkcją Schowka systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="b4dd8-104">Wiele aplikacji korzysta Schowka jako tymczasowy repozytorium dla danych.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="b4dd8-105">Na przykład edytory użyć Schowka podczas operacji kopiowania i wklejania.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="b4dd8-106">Schowek jest również przydatne w przypadku przenoszenia informacji z jednej aplikacji do innej.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-106">The Clipboard is also useful for transferring information from one application to another.</span></span>  
  
 <span data-ttu-id="b4dd8-107">Niektóre aplikacje przechowują dane do Schowka w wielu formatach, aby zwiększyć liczbę inne aplikacje, które mogą za pomocą danych.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-107">Some applications store data on the Clipboard in multiple formats to increase the number of other applications that can potentially use the data.</span></span> <span data-ttu-id="b4dd8-108">Format Schowka jest ciągiem, który identyfikuje format.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-108">A Clipboard format is a string that identifies the format.</span></span> <span data-ttu-id="b4dd8-109">Aplikacja, która używa formatu zidentyfikowanych można pobrać skojarzone dane do Schowka.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-109">An application that uses the identified format can retrieve the associated data on the Clipboard.</span></span> <span data-ttu-id="b4dd8-110"><xref:System.Windows.Forms.DataFormats> Klasy udostępnia wstępnie zdefiniowane format nazwy do użycia.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="b4dd8-111">Możesz również użyć nazwy formatu lub typ obiektu jako jego format.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-111">You can also use your own format names or use an object's type as its format.</span></span> <span data-ttu-id="b4dd8-112">Aby uzyskać informacje dotyczące dodawania danych do Schowka, zobacz [porady: Dodawanie danych do Schowka](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).</span><span class="sxs-lookup"><span data-stu-id="b4dd8-112">For information about adding data to the Clipboard, see [How to: Add Data to the Clipboard](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).</span></span>  
  
 <span data-ttu-id="b4dd8-113">Aby ustalić, czy Schowek zawiera dane w określonym formacie, użyj jednej z `Contains` *Format* metody lub <xref:System.Windows.Forms.Clipboard.GetData%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-113">To determine whether the Clipboard contains data in a particular format, use one of the `Contains`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="b4dd8-114">Aby pobrać danych ze Schowka, użyj jednej z `Get` *Format* metody lub <xref:System.Windows.Forms.Clipboard.GetData%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-114">To retrieve data from the Clipboard, use one of the `Get`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="b4dd8-115">Te metody są nowością w programie [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4dd8-115">These methods are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
 <span data-ttu-id="b4dd8-116">Dostęp do danych ze Schowka za pomocą wersji starszej niż [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], użyj <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> — metoda i wywoływać metod zwróconego elementu <xref:System.Windows.Forms.IDataObject>.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-116">To access data from the Clipboard by using versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> method and call the methods of the returned <xref:System.Windows.Forms.IDataObject>.</span></span> <span data-ttu-id="b4dd8-117">Aby sprawdzić, czy określony format jest dostępna w zwrócony obiekt, na przykład wywołać <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-117">To determine whether a particular format is available in the returned object, for example, call the <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4dd8-118">Wszystkie aplikacje systemu Windows Udostępnianie Schowka systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-118">All Windows-based applications share the system Clipboard.</span></span> <span data-ttu-id="b4dd8-119">W związku z tym zawartość mogą ulec zmianie po przełączeniu do innej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-119">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="b4dd8-120"><xref:System.Windows.Forms.Clipboard> Klasy można używać tylko w wątkach ustawiony na tryb Jednowątkowego apartamentu wątku pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-120">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="b4dd8-121">Aby korzystać z tej klasy, upewnij się, że Twoje `Main` metoda jest oznaczona atrybutem <xref:System.STAThreadAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-121">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="b4dd8-122">Można pobrać danych ze Schowka w formacie jednej, wspólnej</span><span class="sxs-lookup"><span data-stu-id="b4dd8-122">To retrieve data from the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="b4dd8-123">Użyj <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, lub <xref:System.Windows.Forms.Clipboard.GetText%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-123">Use the <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, or <xref:System.Windows.Forms.Clipboard.GetText%2A> method.</span></span> <span data-ttu-id="b4dd8-124">Można też użyć odpowiedniego `Contains` *Format* metod, aby ustalić, czy dane są dostępne w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-124">Optionally, use the corresponding `Contains`*Format* methods first to determine whether data is available in a particular format.</span></span> <span data-ttu-id="b4dd8-125">Te metody są dostępne tylko w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4dd8-125">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a><span data-ttu-id="b4dd8-126">Można pobrać danych ze Schowka w niestandardowym formacie</span><span class="sxs-lookup"><span data-stu-id="b4dd8-126">To retrieve data from the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="b4dd8-127">Użyj <xref:System.Windows.Forms.Clipboard.GetData%2A> metodę o nazwie formatu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-127">Use the <xref:System.Windows.Forms.Clipboard.GetData%2A> method with a custom format name.</span></span> <span data-ttu-id="b4dd8-128">Ta metoda jest dostępna tylko w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4dd8-128">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="b4dd8-129">Można również użyć nazwy formatu wstępnie zdefiniowane z <xref:System.Windows.Forms.Clipboard.SetData%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-129">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="b4dd8-130">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DataFormats>.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-130">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a><span data-ttu-id="b4dd8-131">Można pobrać danych ze Schowka w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="b4dd8-131">To retrieve data from the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="b4dd8-132">Użyj <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b4dd8-132">Use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> method.</span></span> <span data-ttu-id="b4dd8-133">Tej metody należy użyć do pobierania danych ze Schowka w wersjach wcześniejszych niż [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4dd8-133">You must use this method to retrieve data from the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="b4dd8-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4dd8-134">See Also</span></span>  
 [<span data-ttu-id="b4dd8-135">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="b4dd8-135">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="b4dd8-136">Instrukcje: dodawanie danych do schowka</span><span class="sxs-lookup"><span data-stu-id="b4dd8-136">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
