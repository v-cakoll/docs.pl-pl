---
title: Użycie podwójnego buforowania
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: ac6c9b7f2cc1fea86a75eaaf4a2dde1ea60e4f40
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716291"
---
# <a name="using-double-buffering"></a><span data-ttu-id="22d83-102">Użycie podwójnego buforowania</span><span class="sxs-lookup"><span data-stu-id="22d83-102">Using Double Buffering</span></span>
<span data-ttu-id="22d83-103">Podwójnie buforowana grafika umożliwia zmniejszanie migotania w swoich aplikacjach, które zawierają działania złożonego rysowania.</span><span class="sxs-lookup"><span data-stu-id="22d83-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="22d83-104">.NET Framework zawiera wbudowaną obsługę podwójnego buforowania, lub możesz zarządzać i ręczne Renderowanie grafiki.</span><span class="sxs-lookup"><span data-stu-id="22d83-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22d83-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="22d83-105">In This Section</span></span>  
 [<span data-ttu-id="22d83-106">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="22d83-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="22d83-107">Wprowadzenie obsługi podwójnego buforowania pojęcia i przedstawiono .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22d83-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="22d83-108">Instrukcje: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek</span><span class="sxs-lookup"><span data-stu-id="22d83-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="22d83-109">Pokazuje, jak użyć domyślnego podwójnego buforowania pomocy technicznej w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22d83-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="22d83-110">Instrukcje: Ręczne zarządzanie buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="22d83-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="22d83-111">Pokazuje, jak zarządzać podwójnego buforowania w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="22d83-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="22d83-112">Instrukcje: Ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="22d83-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="22d83-113">Pokazuje sposób renderowania podwójnie buforowana grafika.</span><span class="sxs-lookup"><span data-stu-id="22d83-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="22d83-114">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="22d83-114">Reference</span></span>  
 <span data-ttu-id="22d83-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="22d83-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="22d83-116">Metoda kontrolki, która umożliwia podwójnego buforowania.</span><span class="sxs-lookup"><span data-stu-id="22d83-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="22d83-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="22d83-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="22d83-118">Udostępnia metody do tworzenia bufory grafiki typu.</span><span class="sxs-lookup"><span data-stu-id="22d83-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="22d83-119">Zapewnia dostęp do kontekstu buforowaną grafiką dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22d83-119">Provides access to the buffered graphics context for a application domain.</span></span>
