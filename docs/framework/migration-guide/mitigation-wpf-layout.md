---
title: "Ograniczenie: układ platformy WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3ba5ac792169cc076f9621025f35444281cec6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="03e4b-102">Ograniczenie: układ platformy WPF</span><span class="sxs-lookup"><span data-stu-id="03e4b-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="03e4b-103">Układ formantów WPF mogą się nieznacznie zmieniać.</span><span class="sxs-lookup"><span data-stu-id="03e4b-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="03e4b-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="03e4b-104">Impact</span></span>  
 <span data-ttu-id="03e4b-105">W wyniku tej zmiany:</span><span class="sxs-lookup"><span data-stu-id="03e4b-105">As a result of this change:</span></span>  
  
-   <span data-ttu-id="03e4b-106">Szerokość lub wysokość elementów może zwiększać i zmniejszać co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="03e4b-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
-   <span data-ttu-id="03e4b-107">Umieszczanie obiektu można przenieść co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="03e4b-107">The placement of an object can move by at most one pixel.</span></span>  
  
-   <span data-ttu-id="03e4b-108">Elementy wyśrodkowany można pionie lub poziomie od środka co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="03e4b-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="03e4b-109">Domyślnie ten nowy układ jest włączone tylko dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="03e4b-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="03e4b-110">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="03e4b-110">Mitigation</span></span>  
 <span data-ttu-id="03e4b-111">Ponieważ ta modyfikacja zwykle wyeliminować wycinka prawej lub dolnej formantów WPF w DPIs wysoki, aplikacje docelowe wcześniejszych wersji programu .NET Framework, które są uruchomione na .NET Framework 4.6 włączyć do tego nowe zachowanie, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="03e4b-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="03e4b-112">Aplikacje docelowe .NET Framework 4.6, które mają formantów WPF do renderowania przy użyciu poprzedniej algorytmu układu można to zrobić, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="03e4b-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="03e4b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03e4b-113">See Also</span></span>  
 [<span data-ttu-id="03e4b-114">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="03e4b-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
