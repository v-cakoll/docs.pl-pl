---
title: 'Środki zaradcze: Układ platformy WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c261a025548b2d22f6df3051dbcdb637723d4324
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599470"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="9e4ab-102">Środki zaradcze: Układ platformy WPF</span><span class="sxs-lookup"><span data-stu-id="9e4ab-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="9e4ab-103">Nieco zmienić układ kontrolek WPF.</span><span class="sxs-lookup"><span data-stu-id="9e4ab-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9e4ab-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="9e4ab-104">Impact</span></span>  
 <span data-ttu-id="9e4ab-105">W wyniku tej zmiany:</span><span class="sxs-lookup"><span data-stu-id="9e4ab-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="9e4ab-106">Szerokość lub wysokość elementów może zwiększać i zmniejszać co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="9e4ab-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="9e4ab-107">Położenie obiektu można przenieść co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="9e4ab-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="9e4ab-108">Wyśrodkowany elementy mogą być w pionie lub w poziomie, od środka co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="9e4ab-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="9e4ab-109">Domyślnie ten nowy układ jest włączona tylko dla aplikacji przeznaczonych dla platformy .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="9e4ab-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9e4ab-110">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="9e4ab-110">Mitigation</span></span>  
 <span data-ttu-id="9e4ab-111">Ponieważ ta modyfikacja zwykle wyeliminować wycinka elementu po prawej stronie lub u dołu okna kontrolki WPF w dużych wysokiej, aplikacje docelowe wcześniejszych wersji programu .NET Framework, które są uruchomione na platformie .NET Framework 4.6 mogą wyrazić zgodę to nowe zachowanie, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="9e4ab-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="9e4ab-112">Aplikacje, które docelowych programu .NET Framework 4.6, ale chcesz kontrolek WPF do renderowania przy użyciu poprzednich algorytmu układu można to zrobić, dodając następujący wiersz do `<runtime>` sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="9e4ab-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e4ab-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e4ab-113">See also</span></span>

- [<span data-ttu-id="9e4ab-114">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="9e4ab-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
