---
title: Środki zaradcze Renderowanie okna WPF
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13091c06561da24d2fc03f810fd8b8687b21d9a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789791"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="8a7f6-102">Środki zaradcze Renderowanie okna WPF</span><span class="sxs-lookup"><span data-stu-id="8a7f6-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="8a7f6-103">W .NET Framework 4,6 działający w systemie Windows 8 i nowszych całe okno jest renderowane bez przycinania, gdy rozciąga się poza pojedynczym ekranem w scenariuszu z obsługą kilku monitorów.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="8a7f6-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="8a7f6-104">Impact</span></span>

<span data-ttu-id="8a7f6-105">Ogólnie rzecz biorąc, renderowanie całego okna na wielu monitorach bez wycinków jest oczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="8a7f6-106">Jednak w systemie Windows 7 i starszych wersjach Okna WPF są przycinane po przekroczeniu jednego ekranu, ponieważ renderowanie części okna na drugim monitorze ma znaczny wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="8a7f6-107">Dokładny wpływ renderowania systemu Windows WPF na monitory w systemie Windows 8 i nowszych nie jest precyzyjnie wymierny, ponieważ zależy on od dużej liczby czynników.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="8a7f6-108">W niektórych przypadkach może to spowodować niepożądane wpływ na wydajność, szczególnie w przypadku użytkowników, którzy uruchamiają aplikacje intensywnie korzystające z grafiki i mają monitory międzystrefowe systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="8a7f6-109">W innych przypadkach można po prostu chcieć mieć spójne zachowanie w wersjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="8a7f6-110">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="8a7f6-110">Mitigation</span></span>

<span data-ttu-id="8a7f6-111">Tę zmianę można wyłączyć i przywrócić poprzednie zachowanie przycinania okna WPF, gdy wykracza poza pojedynczy ekran.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="8a7f6-112">Istnieją dwa sposoby wykonania tej czynności:</span><span class="sxs-lookup"><span data-stu-id="8a7f6-112">There are two ways to do this:</span></span>

- <span data-ttu-id="8a7f6-113">Dodając `<EnableMultiMonitorDisplayClipping>` element `<appSettings>` do sekcji pliku konfiguracyjnego aplikacji, możesz wyłączyć lub włączyć to zachowanie w aplikacjach uruchomionych w systemie Windows 8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="8a7f6-114">Na przykład następująca sekcja konfiguracyjna wyłącza renderowanie bez przycinania:</span><span class="sxs-lookup"><span data-stu-id="8a7f6-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="8a7f6-115">Ustawienie `<EnableMultiMonitorDisplayClipping>` konfiguracji może mieć jedną z dwóch wartości:</span><span class="sxs-lookup"><span data-stu-id="8a7f6-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="8a7f6-116">`true`, aby włączyć przycinanie systemu Windows do monitorowania granic podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="8a7f6-117">`false`, aby wyłączyć przycinanie okien do monitorowania granic podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="8a7f6-118">Ustawiając <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> właściwość na `true` wartość przy uruchamianiu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a7f6-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a7f6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a7f6-119">See also</span></span>

- [<span data-ttu-id="8a7f6-120">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8a7f6-120">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
