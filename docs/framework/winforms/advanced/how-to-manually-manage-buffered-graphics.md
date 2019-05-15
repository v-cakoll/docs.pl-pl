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
ms.openlocfilehash: 2cdcebd4e47996841ad58213d9c6252a6a3dd7b6
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591836"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="3b812-102">Instrukcje: Ręczne zarządzanie buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="3b812-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="3b812-103">Dla bardziej zaawansowanych scenariuszy buforowania double można użyć klas .NET Framework do zaimplementowania własnej logiki podwójnego buforowania.</span><span class="sxs-lookup"><span data-stu-id="3b812-103">For more advanced double buffering scenarios, you can use the .NET Framework classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="3b812-104">Jest odpowiedzialny za przydzielanie i zarządzanie bufory grafiki typu poszczególnych klasy <xref:System.Drawing.BufferedGraphicsContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="3b812-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="3b812-105">Każda aplikacja ma swój własny domyślną <xref:System.Drawing.BufferedGraphicsContext> który zarządza wszystkich domyślnych podwójnego buforowania dla tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b812-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="3b812-106">Możesz pobrać odwołanie do tego wystąpienia, wywołując <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b812-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="3b812-107">Aby uzyskać domyślne BufferedGraphicsContext — odwołanie</span><span class="sxs-lookup"><span data-stu-id="3b812-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="3b812-108">Ustaw <xref:System.Drawing.BufferedGraphicsManager.Current%2A> właściwości, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="3b812-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <span data-ttu-id="3b812-109">Nie trzeba wywoływać `Dispose` metody <xref:System.Drawing.BufferedGraphicsContext> odwołania otrzymaną od <xref:System.Drawing.BufferedGraphicsManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="3b812-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="3b812-110"><xref:System.Drawing.BufferedGraphicsManager> Obsługuje wszystkie alokacji pamięci i dystrybucji dla domyślnego <xref:System.Drawing.BufferedGraphicsContext> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="3b812-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="3b812-111">Dla aplikacji intensywnie korzystające z grafiki, takich jak animacji, może czasami poprawić wydajność za pomocą dedykowanego <xref:System.Drawing.BufferedGraphicsContext> zamiast <xref:System.Drawing.BufferedGraphicsContext> dostarczone przez <xref:System.Drawing.BufferedGraphicsManager>.</span><span class="sxs-lookup"><span data-stu-id="3b812-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="3b812-112">Dzięki temu można tworzyć i zarządzać nimi bufory grafiki typu pojedynczo, bez ponoszenia zmniejszenie wydajności zarządzania inne buforowanej grafiki skojarzony z aplikacją, chociaż pamięci używane przez aplikację będą większe.</span><span class="sxs-lookup"><span data-stu-id="3b812-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="3b812-113">Aby utworzyć dedykowane BufferedGraphicsContext —</span><span class="sxs-lookup"><span data-stu-id="3b812-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="3b812-114">Deklarowanie i Utwórz nowe wystąpienie klasy <xref:System.Drawing.BufferedGraphicsContext> klasy, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="3b812-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="3b812-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b812-115">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- [<span data-ttu-id="3b812-116">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="3b812-116">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="3b812-117">Instrukcje: Ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="3b812-117">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)
