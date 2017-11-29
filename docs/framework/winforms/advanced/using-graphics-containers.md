---
title: "Używanie kontenerów grafiki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 337057e10e03712aa93b00d9c687374e53f8dd03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="using-graphics-containers"></a><span data-ttu-id="f18ad-102">Używanie kontenerów grafiki</span><span class="sxs-lookup"><span data-stu-id="f18ad-102">Using Graphics Containers</span></span>
<span data-ttu-id="f18ad-103">A <xref:System.Drawing.Graphics> obiekt zapewnia metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, i <xref:System.Drawing.Graphics.DrawString%2A> do wyświetlania obrazów wektora, obrazy rastrowe i tekstu.</span><span class="sxs-lookup"><span data-stu-id="f18ad-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="f18ad-104">A <xref:System.Drawing.Graphics> obiekt ma również kilka właściwości wpływające na jakości i orientację elementów, które są rysowane.</span><span class="sxs-lookup"><span data-stu-id="f18ad-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="f18ad-105">Na przykład właściwość tryb wygładzania Określa, czy zastosowano antyaliasingu do linii i krzywych i właściwości transformacji świata wpływa na pozycji i obracania elementów, które są rysowane.</span><span class="sxs-lookup"><span data-stu-id="f18ad-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="f18ad-106">A <xref:System.Drawing.Graphics> obiekt jest skojarzony z urządzeniem określony ekran.</span><span class="sxs-lookup"><span data-stu-id="f18ad-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="f18ad-107">Jeśli używasz <xref:System.Drawing.Graphics> obiektu do rysowania w oknie <xref:System.Drawing.Graphics> obiektu jest także powiązany z tym poszczególnego okna.</span><span class="sxs-lookup"><span data-stu-id="f18ad-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="f18ad-108">A <xref:System.Drawing.Graphics> obiektu można traktować jako kontener ponieważ posiada zbiór właściwości, które wpływają na rysunku i jest on połączony informacje specyficzne dla danego urządzenia.</span><span class="sxs-lookup"><span data-stu-id="f18ad-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="f18ad-109">Możesz utworzyć kontener dodatkowej w ramach istniejącej <xref:System.Drawing.Graphics> obiektu przez wywołanie metody <xref:System.Drawing.Graphics.BeginContainer%2A> metoda tego <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f18ad-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f18ad-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f18ad-110">In This Section</span></span>  
 [<span data-ttu-id="f18ad-111">Zarządzaniu stanem obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="f18ad-111">Managing the State of a Graphics Object</span></span>](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="f18ad-112">W tym artykule opisano sposób zarządzania ustawieniami jakości, obszar przycinania i transformacje <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f18ad-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="f18ad-113">Używanie zagnieżdżonych kontenerów grafiki</span><span class="sxs-lookup"><span data-stu-id="f18ad-113">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 <span data-ttu-id="f18ad-114">Przedstawia sposób użycia kontenerów do sterowania stanem <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f18ad-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
