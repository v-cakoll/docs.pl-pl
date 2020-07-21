---
title: 'Środki zaradcze: Obsługa dotykowa i pióra oparta na wskaźnikach'
description: Dowiedz się więcej na temat skutków włączenia opcjonalnego stosu dotykowego/pióra WPF dla aplikacji WPF przeznaczonych dla .NET Framework 4,7.
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475427"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="57a9c-103">Środki zaradcze: Obsługa dotykowa i pióra oparta na wskaźnikach</span><span class="sxs-lookup"><span data-stu-id="57a9c-103">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="57a9c-104">Aplikacje WPF, które są przeznaczone dla .NET Framework 4,7 i działają w systemie Windows, począwszy od aktualizacji systemu Windows 10 Creators, mogą umożliwić opcjonalny `WM_POINTER` stos dotykowy/pióra WPF.</span><span class="sxs-lookup"><span data-stu-id="57a9c-104">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="57a9c-105">Wpływ</span><span class="sxs-lookup"><span data-stu-id="57a9c-105">Impact</span></span>

<span data-ttu-id="57a9c-106">Deweloperzy, którzy nie umożliwiają jawnie włączania obsługi dotykowej opartej na wskaźnikach, nie powinni zmieniać zachowań dotykowych i pióra WPF.</span><span class="sxs-lookup"><span data-stu-id="57a9c-106">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="57a9c-107">Poniżej przedstawiono bieżące znane problemy z opcjonalnym `WM_POINTER` stosem dotyk/piórem:</span><span class="sxs-lookup"><span data-stu-id="57a9c-107">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="57a9c-108">Brak obsługi pisma odręcznego w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="57a9c-108">No support for real-time inking.</span></span>

   <span data-ttu-id="57a9c-109">Podczas gdy wtyczki pisma odręcznego i pióra nadal działają, są przetwarzane w wątku interfejsu użytkownika, co może prowadzić do słabej wydajności.</span><span class="sxs-lookup"><span data-stu-id="57a9c-109">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="57a9c-110">Zmiany behawioralne spowodowane zmianami w trakcie podwyższania poziomu zdarzeń dotknięcia/piórem do zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="57a9c-110">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="57a9c-111">Manipulowanie może zachowywać się inaczej.</span><span class="sxs-lookup"><span data-stu-id="57a9c-111">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="57a9c-112">Wartość przeciągnij/upuść nie będzie zawierać odpowiedniej opinii na temat wprowadzania dotykowego.</span><span class="sxs-lookup"><span data-stu-id="57a9c-112">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="57a9c-113">(Nie ma to wpływu na wprowadzanie piórem).</span><span class="sxs-lookup"><span data-stu-id="57a9c-113">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="57a9c-114">Nie można już inicjować przeciągania/upuszczania w przypadku zdarzeń dotykowych/pióra.</span><span class="sxs-lookup"><span data-stu-id="57a9c-114">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="57a9c-115">Może to spowodować, że aplikacja przestanie odpowiadać, dopóki nie zostanie wykryta mysz.</span><span class="sxs-lookup"><span data-stu-id="57a9c-115">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="57a9c-116">Zamiast tego deweloperzy powinni inicjować przeciąganie i upuszczanie ze zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="57a9c-116">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="57a9c-117">Możliwość wypróbowania obsługi dotyku i pióra opartego na WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="57a9c-117">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="57a9c-118">Deweloperzy, którzy chcą włączyć ten stos, mogą dodać następujące elementy do pliku *app.config* aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57a9c-118">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="57a9c-119">Usunięcie tego wpisu lub ustawienie jego wartości powoduje `false` wyłączenie tego opcjonalnego stosu.</span><span class="sxs-lookup"><span data-stu-id="57a9c-119">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="57a9c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57a9c-120">See also</span></span>

- [<span data-ttu-id="57a9c-121">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="57a9c-121">Application compatibility</span></span>](application-compatibility.md)
