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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777159"
---
# <a name="using-double-buffering"></a><span data-ttu-id="13a5c-102">Użycie podwójnego buforowania</span><span class="sxs-lookup"><span data-stu-id="13a5c-102">Using Double Buffering</span></span>
<span data-ttu-id="13a5c-103">Podwójnie buforowana grafika umożliwia zmniejszanie migotania w swoich aplikacjach, które zawierają działania złożonego rysowania.</span><span class="sxs-lookup"><span data-stu-id="13a5c-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="13a5c-104">.NET Framework zawiera wbudowaną obsługę podwójnego buforowania, lub możesz zarządzać i ręczne Renderowanie grafiki.</span><span class="sxs-lookup"><span data-stu-id="13a5c-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13a5c-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="13a5c-105">In This Section</span></span>  
 [<span data-ttu-id="13a5c-106">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="13a5c-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="13a5c-107">Wprowadzenie obsługi podwójnego buforowania pojęcia i przedstawiono .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13a5c-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="13a5c-108">Instrukcje: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek</span><span class="sxs-lookup"><span data-stu-id="13a5c-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="13a5c-109">Pokazuje, jak użyć domyślnego podwójnego buforowania pomocy technicznej w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13a5c-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="13a5c-110">Instrukcje: Ręczne zarządzanie buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="13a5c-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="13a5c-111">Pokazuje, jak zarządzać podwójnego buforowania w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="13a5c-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="13a5c-112">Instrukcje: Ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="13a5c-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="13a5c-113">Pokazuje sposób renderowania podwójnie buforowana grafika.</span><span class="sxs-lookup"><span data-stu-id="13a5c-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="13a5c-114">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="13a5c-114">Reference</span></span>  
 <span data-ttu-id="13a5c-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="13a5c-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="13a5c-116">Metoda kontrolki, która umożliwia podwójnego buforowania.</span><span class="sxs-lookup"><span data-stu-id="13a5c-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="13a5c-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="13a5c-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="13a5c-118">Udostępnia metody do tworzenia bufory grafiki typu.</span><span class="sxs-lookup"><span data-stu-id="13a5c-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="13a5c-119">Zapewnia dostęp do kontekstu buforowaną grafiką dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="13a5c-119">Provides access to the buffered graphics context for a application domain.</span></span>
