---
title: Środki zaradcze Układ WPF
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d266ad33110d2bda8f7911d89981c372624c3f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779065"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="42eb5-102">Środki zaradcze Układ WPF</span><span class="sxs-lookup"><span data-stu-id="42eb5-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="42eb5-103">Układ formantów WPF może się nieco zmieniać.</span><span class="sxs-lookup"><span data-stu-id="42eb5-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="42eb5-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="42eb5-104">Impact</span></span>  
 <span data-ttu-id="42eb5-105">W wyniku tej zmiany:</span><span class="sxs-lookup"><span data-stu-id="42eb5-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="42eb5-106">Szerokość lub wysokość elementów może wzrosnąć lub zmniejszyć o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="42eb5-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="42eb5-107">Położenie obiektu może zostać przeniesione o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="42eb5-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="42eb5-108">Wyśrodkowane elementy mogą być przesunięte w pionie lub w poziomie o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="42eb5-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="42eb5-109">Domyślnie ten nowy układ jest włączony tylko dla aplikacji przeznaczonych dla .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="42eb5-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="42eb5-110">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="42eb5-110">Mitigation</span></span>  
 <span data-ttu-id="42eb5-111">Ponieważ ta modyfikacja ma na celu wyeliminowanie wycinków prawej lub dolnej części formantów WPF o wysokiej rozdzielczościami, aplikacje, które są przeznaczone dla wcześniejszych wersji .NET Framework ale działają na .NET Framework 4,6, mogą przystąpić do tego nowego zachowania, dodając następujący wiersz do `<runtime>` sekcja pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="42eb5-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="42eb5-112">Aplikacje, które są przeznaczone dla .NET Framework 4,6, ale chcą, aby formanty WPF mogły być renderowane przy użyciu poprzedniego algorytmu układu, można to zrobić `<runtime>` , dodając następujący wiersz do sekcji pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="42eb5-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="42eb5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42eb5-113">See also</span></span>

- [<span data-ttu-id="42eb5-114">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="42eb5-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
