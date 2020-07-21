---
title: 'Ograniczenie: renderowanie okien WPF'
description: Dowiedz się więcej na temat wpływu i łagodzenia renderowania okien WPF w .NET Framework 4,6 uruchomiony w systemie Windows 8 lub nowszym.
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: d624478d17a4076107438f71b0a86eeb6d9f3ea4
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475336"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="b33db-103">Ograniczenie: renderowanie okien WPF</span><span class="sxs-lookup"><span data-stu-id="b33db-103">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="b33db-104">W .NET Framework 4,6 działający w systemie Windows 8 i nowszych całe okno jest renderowane bez przycinania, gdy rozciąga się poza pojedynczym ekranem w scenariuszu z obsługą kilku monitorów.</span><span class="sxs-lookup"><span data-stu-id="b33db-104">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="b33db-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="b33db-105">Impact</span></span>

<span data-ttu-id="b33db-106">Ogólnie rzecz biorąc, renderowanie całego okna na wielu monitorach bez wycinków jest oczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="b33db-106">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="b33db-107">Jednak w systemie Windows 7 i starszych wersjach Okna WPF są przycinane po przekroczeniu jednego ekranu, ponieważ renderowanie części okna na drugim monitorze ma znaczny wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="b33db-107">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="b33db-108">Dokładny wpływ renderowania systemu Windows WPF na monitory w systemie Windows 8 i nowszych nie jest precyzyjnie wymierny, ponieważ zależy on od dużej liczby czynników.</span><span class="sxs-lookup"><span data-stu-id="b33db-108">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="b33db-109">W niektórych przypadkach może to spowodować niepożądane wpływ na wydajność, szczególnie w przypadku użytkowników, którzy uruchamiają aplikacje intensywnie korzystające z grafiki i mają monitory międzystrefowe systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b33db-109">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="b33db-110">W innych przypadkach można po prostu chcieć mieć spójne zachowanie w wersjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b33db-110">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="b33db-111">Ograniczanie ryzyka</span><span class="sxs-lookup"><span data-stu-id="b33db-111">Mitigation</span></span>

<span data-ttu-id="b33db-112">Tę zmianę można wyłączyć i przywrócić poprzednie zachowanie przycinania okna WPF, gdy wykracza poza pojedynczy ekran.</span><span class="sxs-lookup"><span data-stu-id="b33db-112">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="b33db-113">Istnieją dwa sposoby wykonania tej czynności:</span><span class="sxs-lookup"><span data-stu-id="b33db-113">There are two ways to do this:</span></span>

- <span data-ttu-id="b33db-114">Dodając `<EnableMultiMonitorDisplayClipping>` element do `<appSettings>` sekcji pliku konfiguracyjnego aplikacji, możesz wyłączyć lub włączyć to zachowanie w aplikacjach uruchomionych w systemie Windows 8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="b33db-114">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="b33db-115">Na przykład następująca sekcja konfiguracyjna wyłącza renderowanie bez przycinania:</span><span class="sxs-lookup"><span data-stu-id="b33db-115">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="b33db-116">`<EnableMultiMonitorDisplayClipping>`Ustawienie konfiguracji może mieć jedną z dwóch wartości:</span><span class="sxs-lookup"><span data-stu-id="b33db-116">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="b33db-117">`true`, aby włączyć przycinanie systemu Windows do monitorowania granic podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="b33db-117">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="b33db-118">`false`, aby wyłączyć przycinanie okien do monitorowania granic podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="b33db-118">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="b33db-119">Ustawiając <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> Właściwość na wartość `true` przy uruchamianiu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b33db-119">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="b33db-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b33db-120">See also</span></span>

- [<span data-ttu-id="b33db-121">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="b33db-121">Application compatibility</span></span>](application-compatibility.md)
