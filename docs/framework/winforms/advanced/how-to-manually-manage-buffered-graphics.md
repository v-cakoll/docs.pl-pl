---
title: 'Instrukcje: Ręczne zarządzanie buforowaną grafiką'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968605"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="d57c9-102">Instrukcje: Ręczne zarządzanie buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="d57c9-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="d57c9-103">W przypadku bardziej zaawansowanych scenariuszy podwójnego buforowania można użyć .NET Framework klas do zaimplementowania własnej logiki podwójnego buforowania.</span><span class="sxs-lookup"><span data-stu-id="d57c9-103">For more advanced double buffering scenarios, you can use the .NET Framework classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="d57c9-104">Klasa odpowiedzialna za przydzielanie pojedynczych buforów grafiki i zarządzanie nimi <xref:System.Drawing.BufferedGraphicsContext> jest klasą.</span><span class="sxs-lookup"><span data-stu-id="d57c9-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="d57c9-105">Każda aplikacja ma swoją własną wartość <xref:System.Drawing.BufferedGraphicsContext> domyślną, która zarządza wszystkimi domyślnymi buforowaniem podwójnym dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d57c9-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="d57c9-106">Możesz pobrać odwołanie do tego wystąpienia, wywołując <xref:System.Drawing.BufferedGraphicsManager.Current%2A>metodę.</span><span class="sxs-lookup"><span data-stu-id="d57c9-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="d57c9-107">Aby uzyskać odwołanie do domyślnego BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="d57c9-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="d57c9-108"><xref:System.Drawing.BufferedGraphicsManager.Current%2A> Ustaw właściwość, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d57c9-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > <span data-ttu-id="d57c9-109">Nie trzeba wywoływać `Dispose` metody <xref:System.Drawing.BufferedGraphicsContext> na odwołanie <xref:System.Drawing.BufferedGraphicsManager> , które otrzymasz od klasy.</span><span class="sxs-lookup"><span data-stu-id="d57c9-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="d57c9-110">Obsługuje wszystkie alokacje pamięci i dystrybucję wystąpień domyślnych <xref:System.Drawing.BufferedGraphicsContext>. <xref:System.Drawing.BufferedGraphicsManager></span><span class="sxs-lookup"><span data-stu-id="d57c9-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="d57c9-111">W przypadku aplikacji intensywnie korzystających z wielu operacji, takich jak animacje, można czasami zwiększyć <xref:System.Drawing.BufferedGraphicsContext> wydajność przy użyciu <xref:System.Drawing.BufferedGraphicsContext> dedykowanej zamiast <xref:System.Drawing.BufferedGraphicsManager>dostarczonej przez.</span><span class="sxs-lookup"><span data-stu-id="d57c9-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="d57c9-112">Dzięki temu można tworzyć bufory grafiki i zarządzać nimi pojedynczo, bez ponoszenia kosztów wydajności związanych z zarządzaniem wszystkimi innymi, buforowanymi grafikami skojarzonymi z aplikacją, chociaż ilość pamięci używanej przez aplikację będzie większa.</span><span class="sxs-lookup"><span data-stu-id="d57c9-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="d57c9-113">Aby utworzyć dedykowany BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="d57c9-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="d57c9-114">Zadeklaruj i Utwórz nowe wystąpienie <xref:System.Drawing.BufferedGraphicsContext> klasy, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d57c9-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="d57c9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d57c9-115">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- [<span data-ttu-id="d57c9-116">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="d57c9-116">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="d57c9-117">Instrukcje: Ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="d57c9-117">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)
