---
title: 'Ograniczenie: renderowanie okien WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: 42d6abf1ba6ed7c17a5a5604e98b5ee46d0c3ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457768"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="e989f-102">Ograniczenie: renderowanie okien WPF</span><span class="sxs-lookup"><span data-stu-id="e989f-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="e989f-103">W programie .NET Framework 4.6 działającym w systemie Windows 8 i wyższym całe okno jest renderowane bez przycinania, gdy rozciąga się poza pojedynczym ekranem w scenariuszu z wieloma monitorami.</span><span class="sxs-lookup"><span data-stu-id="e989f-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="e989f-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="e989f-104">Impact</span></span>

<span data-ttu-id="e989f-105">Ogólnie rzecz biorąc renderowanie całego okna na wielu monitorach bez przycinania jest oczekiwanym zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="e989f-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="e989f-106">Jednak w systemie Windows 7 i wcześniejszych wersjach okna WPF są przycinane, gdy wykraczają poza jeden ekran, ponieważ renderowanie części okna na drugim monitorze ma znaczący wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="e989f-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="e989f-107">Dokładny wpływ renderowania okien WPF na monitorach w systemie Windows 8 i powyżej nie jest dokładnie wymierny, ponieważ zależy od dużej liczby czynników.</span><span class="sxs-lookup"><span data-stu-id="e989f-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="e989f-108">W niektórych przypadkach może nadal powodować niepożądany wpływ na wydajność, szczególnie dla użytkowników, którzy uruchamiają aplikacje wymagające dużej ilości grafiki i mają monitory międzystrefowe systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e989f-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="e989f-109">W innych przypadkach może po prostu chcesz spójne zachowanie w wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e989f-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="e989f-110">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="e989f-110">Mitigation</span></span>

<span data-ttu-id="e989f-111">Można wyłączyć tę zmianę i przywrócić poprzednie zachowanie przycinania okna WPF, gdy wykracza poza jeden ekran.</span><span class="sxs-lookup"><span data-stu-id="e989f-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="e989f-112">Istnieją dwa sposoby wykonania tej czynności:</span><span class="sxs-lookup"><span data-stu-id="e989f-112">There are two ways to do this:</span></span>

- <span data-ttu-id="e989f-113">Dodając `<EnableMultiMonitorDisplayClipping>` element do `<appSettings>` sekcji pliku konfiguracji aplikacji, można wyłączyć lub włączyć to zachowanie w aplikacjach działających w systemie Windows 8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="e989f-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="e989f-114">Na przykład następująca sekcja konfiguracji wyłącza renderowanie bez przycinania:</span><span class="sxs-lookup"><span data-stu-id="e989f-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="e989f-115">Ustawienie `<EnableMultiMonitorDisplayClipping>` konfiguracji może mieć jedną z dwóch wartości:</span><span class="sxs-lookup"><span data-stu-id="e989f-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="e989f-116">`true`, aby umożliwić przycinanie okien w celu monitorowania granic podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="e989f-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="e989f-117">`false`, aby wyłączyć przycinanie okien w celu monitorowania granic podczas renderowania.</span><span class="sxs-lookup"><span data-stu-id="e989f-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="e989f-118">Ustawiając <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> właściwość `true` przy uruchamianiu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e989f-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="e989f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e989f-119">See also</span></span>

- [<span data-ttu-id="e989f-120">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="e989f-120">Application compatibility</span></span>](application-compatibility.md)
