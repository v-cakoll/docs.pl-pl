---
title: "Użycie podwójnego buforowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5ad51e27c3d31ece1d11831c953023bedba3a97
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="using-double-buffering"></a><span data-ttu-id="29b11-102">Użycie podwójnego buforowania</span><span class="sxs-lookup"><span data-stu-id="29b11-102">Using Double Buffering</span></span>
<span data-ttu-id="29b11-103">Podwójnie buforowana grafika służy do zmniejszenia migotania w aplikacjach zawierające operacji malowania złożonego.</span><span class="sxs-lookup"><span data-stu-id="29b11-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="29b11-104">.NET Framework zawiera wbudowaną obsługę podwójnego buforowania lub zarządzać i ręczne Renderowanie grafiki.</span><span class="sxs-lookup"><span data-stu-id="29b11-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="29b11-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="29b11-105">In This Section</span></span>  
 [<span data-ttu-id="29b11-106">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="29b11-106">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="29b11-107">Wprowadza obsługi podwójnego buforowania pojęcia i przedstawiono .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29b11-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="29b11-108">Porady: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek</span><span class="sxs-lookup"><span data-stu-id="29b11-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="29b11-109">Demonstracja korzysta z domyślnego podwójnego buforowania pomocy technicznej w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29b11-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="29b11-110">Porady: ręczne zarządzanie buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="29b11-110">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="29b11-111">Pokazuje, jak zarządzać podwójnego buforowania w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="29b11-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="29b11-112">Porady: ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="29b11-112">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="29b11-113">Przedstawia sposób renderowania podwójnie buforowana grafika.</span><span class="sxs-lookup"><span data-stu-id="29b11-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="29b11-114">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="29b11-114">Reference</span></span>  
 <span data-ttu-id="29b11-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="29b11-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="29b11-116">Metoda kontrolki, która umożliwia podwójnego buforowania.</span><span class="sxs-lookup"><span data-stu-id="29b11-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="29b11-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="29b11-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="29b11-118">Udostępnia metody do tworzenia buforów grafiki.</span><span class="sxs-lookup"><span data-stu-id="29b11-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="29b11-119">Zapewnia dostęp do buforowanej grafiki kontekstu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29b11-119">Provides access to the buffered graphics context for a application domain.</span></span>
