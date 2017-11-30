---
title: "Porady: ręczne zarządzanie buforowaną grafiką"
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
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 678b9ad5e8f9b40f927a35e98973cabc831c5cf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="d410d-102">Porady: ręczne zarządzanie buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="d410d-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="d410d-103">W przypadku bardziej zaawansowanych scenariuszy podwójnego buforowania, można użyć [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy do zaimplementowania własną logikę podwójnego buforowania.</span><span class="sxs-lookup"><span data-stu-id="d410d-103">For more advanced double buffering scenarios, you can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="d410d-104">Jest odpowiedzialna za przydzielanie i zarządzanie buforów poszczególnych grafiki klasy <xref:System.Drawing.BufferedGraphicsContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="d410d-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="d410d-105">Każda aplikacja ma własny domyślną <xref:System.Drawing.BufferedGraphicsContext> który zarządza wszystkich domyślnych podwójnego buforowania dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d410d-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="d410d-106">Można pobrać odwołania do tego wystąpienia przez wywołanie metody <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="d410d-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="d410d-107">Aby uzyskać odwołanie do domyślnego elementu BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="d410d-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="d410d-108">Ustaw <xref:System.Drawing.BufferedGraphicsManager.Current%2A> właściwości, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d410d-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <span data-ttu-id="d410d-109">Nie należy wywołać `Dispose` metoda <xref:System.Drawing.BufferedGraphicsContext> odwołania otrzymanych z <xref:System.Drawing.BufferedGraphicsManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="d410d-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="d410d-110"><xref:System.Drawing.BufferedGraphicsManager> Obsługuje wszystkie z alokacją pamięci i dystrybucji dla domyślnego <xref:System.Drawing.BufferedGraphicsContext> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="d410d-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="d410d-111">Graficznie znacznym aplikacji takich jak animacji, może czasem poprawić wydajność przy użyciu dedykowana <xref:System.Drawing.BufferedGraphicsContext> zamiast <xref:System.Drawing.BufferedGraphicsContext> dostarczonych przez <xref:System.Drawing.BufferedGraphicsManager>.</span><span class="sxs-lookup"><span data-stu-id="d410d-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="d410d-112">Umożliwia tworzenie i zarządzanie nimi buforów grafiki oddzielnie, bez konieczności zarządzania wszystkich innych buforowanej grafiki skojarzone z aplikacją, chociaż pamięci używane przez aplikację będą większe obciążenie.</span><span class="sxs-lookup"><span data-stu-id="d410d-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="d410d-113">Aby utworzyć dedykowane BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="d410d-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="d410d-114">Deklarowanie i Utwórz nowe wystąpienie klasy <xref:System.Drawing.BufferedGraphicsContext> klasy, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d410d-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="d410d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d410d-115">See Also</span></span>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 [<span data-ttu-id="d410d-116">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="d410d-116">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="d410d-117">Porady: ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="d410d-117">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
