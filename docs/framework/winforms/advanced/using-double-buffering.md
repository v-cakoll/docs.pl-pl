---
title: Użycie podwójnego buforowania
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169918"
---
# <a name="using-double-buffering"></a><span data-ttu-id="42488-102">Użycie podwójnego buforowania</span><span class="sxs-lookup"><span data-stu-id="42488-102">Using Double Buffering</span></span>
<span data-ttu-id="42488-103">Podwójnie buforowana grafika umożliwia zmniejszanie migotania w swoich aplikacjach, które zawierają działania złożonego rysowania.</span><span class="sxs-lookup"><span data-stu-id="42488-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="42488-104">.NET Framework zawiera wbudowaną obsługę podwójnego buforowania, lub możesz zarządzać i ręczne Renderowanie grafiki.</span><span class="sxs-lookup"><span data-stu-id="42488-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42488-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="42488-105">In This Section</span></span>  
 [<span data-ttu-id="42488-106">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="42488-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="42488-107">Wprowadzenie obsługi podwójnego buforowania pojęcia i przedstawiono .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="42488-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="42488-108">Instrukcje: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek</span><span class="sxs-lookup"><span data-stu-id="42488-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="42488-109">Pokazuje, jak użyć domyślnego podwójnego buforowania pomocy technicznej w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="42488-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="42488-110">Instrukcje: Ręczne zarządzanie buforowaną grafiką</span><span class="sxs-lookup"><span data-stu-id="42488-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="42488-111">Pokazuje, jak zarządzać podwójnego buforowania w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="42488-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="42488-112">Instrukcje: Ręczne renderowanie buforowanej grafiki</span><span class="sxs-lookup"><span data-stu-id="42488-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="42488-113">Pokazuje sposób renderowania podwójnie buforowana grafika.</span><span class="sxs-lookup"><span data-stu-id="42488-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="42488-114">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="42488-114">Reference</span></span>  
 <span data-ttu-id="42488-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Metoda kontrolki, która umożliwia podwójnego buforowania.</span><span class="sxs-lookup"><span data-stu-id="42488-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="42488-116"><xref:System.Drawing.BufferedGraphicsContext> Udostępnia metody do tworzenia bufory grafiki typu.</span><span class="sxs-lookup"><span data-stu-id="42488-116"><xref:System.Drawing.BufferedGraphicsContext> Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="42488-117">Zapewnia dostęp do kontekstu buforowaną grafiką dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42488-117">Provides access to the buffered graphics context for a application domain.</span></span>
