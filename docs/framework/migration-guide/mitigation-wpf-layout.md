---
title: 'Ograniczenie: układ platformy WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 3e08a2d11e815248d0fe73f804e9ef7edb7c04da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126112"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="c04ae-102">Ograniczenie: układ platformy WPF</span><span class="sxs-lookup"><span data-stu-id="c04ae-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="c04ae-103">Układ formantów WPF może się nieco zmieniać.</span><span class="sxs-lookup"><span data-stu-id="c04ae-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c04ae-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="c04ae-104">Impact</span></span>  
 <span data-ttu-id="c04ae-105">W wyniku tej zmiany:</span><span class="sxs-lookup"><span data-stu-id="c04ae-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="c04ae-106">Szerokość lub wysokość elementów może wzrosnąć lub zmniejszyć o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="c04ae-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="c04ae-107">Położenie obiektu może zostać przeniesione o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="c04ae-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="c04ae-108">Wyśrodkowane elementy mogą być przesunięte w pionie lub w poziomie o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="c04ae-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="c04ae-109">Domyślnie ten nowy układ jest włączony tylko dla aplikacji przeznaczonych dla .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="c04ae-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c04ae-110">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="c04ae-110">Mitigation</span></span>  
 <span data-ttu-id="c04ae-111">Ponieważ ta modyfikacja ma na celu wyeliminowanie wycinków prawej lub dolnej części formantów WPF o wysokiej rozdzielczościami, aplikacje, które są przeznaczone dla wcześniejszych wersji .NET Framework ale działają na .NET Framework 4,6, mogą przystąpić do tego nowego zachowania, dodając następujący wiersz do @no Sekcja __t_0_ pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="c04ae-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="c04ae-112">Aplikacje przeznaczone dla .NET Framework 4,6, ale chcą, aby formanty WPF mogły być renderowane przy użyciu poprzedniego algorytmu układu, można to zrobić, dodając następujący wiersz do sekcji `<runtime>` pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="c04ae-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c04ae-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c04ae-113">See also</span></span>

- [<span data-ttu-id="c04ae-114">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="c04ae-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
