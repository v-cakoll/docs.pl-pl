---
title: 'Ograniczenie: układ platformy WPF'
description: Dowiedz się, jak wyeliminować problemy, które wynikają z zmiany w układzie formantów WPF, jak umieszczanie obiektu w pikselach.
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: e4e4612f7b39eefbf0e76ac86c8eb644c257ba75
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475349"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="f83f0-103">Ograniczenie: układ platformy WPF</span><span class="sxs-lookup"><span data-stu-id="f83f0-103">Mitigation: WPF Layout</span></span>
<span data-ttu-id="f83f0-104">Układ formantów WPF może się nieco zmieniać.</span><span class="sxs-lookup"><span data-stu-id="f83f0-104">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f83f0-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="f83f0-105">Impact</span></span>  
 <span data-ttu-id="f83f0-106">W wyniku tej zmiany:</span><span class="sxs-lookup"><span data-stu-id="f83f0-106">As a result of this change:</span></span>  
  
- <span data-ttu-id="f83f0-107">Szerokość lub wysokość elementów może wzrosnąć lub zmniejszyć o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="f83f0-107">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="f83f0-108">Położenie obiektu może zostać przeniesione o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="f83f0-108">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="f83f0-109">Wyśrodkowane elementy mogą być przesunięte w pionie lub w poziomie o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="f83f0-109">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="f83f0-110">Domyślnie ten nowy układ jest włączony tylko dla aplikacji przeznaczonych dla .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="f83f0-110">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f83f0-111">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="f83f0-111">Mitigation</span></span>  
 <span data-ttu-id="f83f0-112">Ponieważ ta modyfikacja ma na celu wyeliminowanie wycinków prawej lub dolnej części formantów WPF o wysokiej rozdzielczościami, aplikacje, które są przeznaczone dla wcześniejszych wersji .NET Framework ale działają na .NET Framework 4,6, mogą przystąpić do tego nowego zachowania, dodając następujący wiersz do `<runtime>` sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="f83f0-112">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="f83f0-113">Aplikacje, które są przeznaczone dla .NET Framework 4,6, ale chcą, aby formanty WPF mogły być renderowane przy użyciu poprzedniego algorytmu układu, można to zrobić, dodając następujący wiersz do `<runtime>` sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="f83f0-113">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="f83f0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f83f0-114">See also</span></span>

- [<span data-ttu-id="f83f0-115">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="f83f0-115">Application compatibility</span></span>](application-compatibility.md)
