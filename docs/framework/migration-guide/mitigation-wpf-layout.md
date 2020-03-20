---
title: 'Ograniczenie: układ platformy WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457784"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="d8983-102">Ograniczenie: układ platformy WPF</span><span class="sxs-lookup"><span data-stu-id="d8983-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="d8983-103">Układ formantów WPF można zmienić nieznacznie.</span><span class="sxs-lookup"><span data-stu-id="d8983-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="d8983-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="d8983-104">Impact</span></span>  
 <span data-ttu-id="d8983-105">W wyniku tej zmiany:</span><span class="sxs-lookup"><span data-stu-id="d8983-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="d8983-106">Szerokość lub wysokość elementów może rosnąć lub zmniejszać się o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="d8983-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="d8983-107">Położenie obiektu może poruszać się o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="d8983-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="d8983-108">Wyśrodkowane elementy mogą być pionowo lub poziomo wyłączone do środka o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="d8983-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="d8983-109">Domyślnie ten nowy układ jest włączony tylko dla aplikacji, które są przeznaczone dla programu .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="d8983-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="d8983-110">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="d8983-110">Mitigation</span></span>  
 <span data-ttu-id="d8983-111">Ponieważ ta modyfikacja ma tendencję do wyeliminowania przycinania prawego lub dolnego poziomu formantów WPF w wysokich dpis, aplikacje, które są przeznaczone dla wcześniejszych wersji `<runtime>` programu .NET Framework, ale są uruchomione w programie .NET Framework 4.6, mogą zdecydować się na to nowe zachowanie, dodając następujący wiersz do sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="d8983-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="d8983-112">Aplikacje, które są przeznaczone dla programu .NET Framework 4.6, ale chcesz, aby formanty WPF renderowane przy użyciu poprzedniego algorytmu układu można to zrobić, dodając następujący wiersz do `<runtime>` sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="d8983-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8983-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8983-113">See also</span></span>

- [<span data-ttu-id="d8983-114">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="d8983-114">Application compatibility</span></span>](application-compatibility.md)
