---
title: Używanie kontenerów grafiki
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: cfad7254057a31ea8268784cd4b6849850f3e2aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766158"
---
# <a name="using-graphics-containers"></a><span data-ttu-id="154b8-102">Używanie kontenerów grafiki</span><span class="sxs-lookup"><span data-stu-id="154b8-102">Using Graphics Containers</span></span>
<span data-ttu-id="154b8-103">A <xref:System.Drawing.Graphics> obiekt zapewnia metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, i <xref:System.Drawing.Graphics.DrawString%2A> do wyświetlania obrazy wektorowe, rastrowych obrazów i tekstu.</span><span class="sxs-lookup"><span data-stu-id="154b8-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="154b8-104">A <xref:System.Drawing.Graphics> obiekt ma również kilka właściwości, które mają wpływ na jakość i orientację elementów, które są rysowane.</span><span class="sxs-lookup"><span data-stu-id="154b8-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="154b8-105">Na przykład właściwość tryb wygładzania Określa, czy dotyczy antyaliasingu do linii i krzywych i właściwości transformacji świata ma wpływ na położenie i obracania elementów, które są rysowane.</span><span class="sxs-lookup"><span data-stu-id="154b8-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="154b8-106">A <xref:System.Drawing.Graphics> obiekt jest skojarzony z urządzeniem określony ekran.</span><span class="sxs-lookup"><span data-stu-id="154b8-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="154b8-107">Kiedy używasz <xref:System.Drawing.Graphics> obiektu, aby narysować w oknie <xref:System.Drawing.Graphics> obiektu jest również skojarzony z tym konkretnym oknie.</span><span class="sxs-lookup"><span data-stu-id="154b8-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="154b8-108">Element <xref:System.Drawing.Graphics> obiektu można traktować jako kontener, ponieważ posiada zbiór właściwości, które wpływają na rysunku i prowadzi do informacji specyficznych dla urządzenia.</span><span class="sxs-lookup"><span data-stu-id="154b8-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="154b8-109">Można utworzyć pomocniczego kontener w ramach istniejącego <xref:System.Drawing.Graphics> obiektu przez wywołanie metody <xref:System.Drawing.Graphics.BeginContainer%2A> metodę, która <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="154b8-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="154b8-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="154b8-110">In This Section</span></span>  
 [<span data-ttu-id="154b8-111">Zarządzanie stanem obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="154b8-111">Managing the State of a Graphics Object</span></span>](managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="154b8-112">W tym artykule opisano sposób Zarządzanie ustawieniami jakości, obszar przycinania i przekształcanie <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="154b8-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="154b8-113">Używanie zagnieżdżonych kontenerów grafiki</span><span class="sxs-lookup"><span data-stu-id="154b8-113">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)  
 <span data-ttu-id="154b8-114">Pokazuje, jak używać kontenerów do sterowania stanem <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="154b8-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
