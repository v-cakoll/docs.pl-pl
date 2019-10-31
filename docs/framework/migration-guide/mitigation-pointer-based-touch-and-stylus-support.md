---
title: 'Środki zaradcze: Obsługa dotykowa i pióra oparta na wskaźnikach'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 41a587b343e4774a27e9ddc39080de6939839d93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126201"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="6c292-102">Środki zaradcze: Obsługa dotykowa i pióra oparta na wskaźnikach</span><span class="sxs-lookup"><span data-stu-id="6c292-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="6c292-103">Aplikacje WPF, które są przeznaczone dla .NET Framework 4,7 i działają w systemach Windows, począwszy od aktualizacji systemu Windows 10 Creators, mogą włączyć opcjonalny stos dotykowy/pióra WPF oparty na `WM_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="6c292-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="6c292-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="6c292-104">Impact</span></span>

<span data-ttu-id="6c292-105">Deweloperzy, którzy nie umożliwiają jawnie włączania obsługi dotykowej opartej na wskaźnikach, nie powinni zmieniać zachowań dotykowych i pióra WPF.</span><span class="sxs-lookup"><span data-stu-id="6c292-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="6c292-106">Poniżej znajdują się obecnie znane problemy z opcjonalnym stosem dotykowy/piórem na `WM_POINTER`:</span><span class="sxs-lookup"><span data-stu-id="6c292-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="6c292-107">Brak obsługi pisma odręcznego w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="6c292-107">No support for real-time inking.</span></span>

   <span data-ttu-id="6c292-108">Podczas gdy wtyczki pisma odręcznego i pióra nadal działają, są przetwarzane w wątku interfejsu użytkownika, co może prowadzić do słabej wydajności.</span><span class="sxs-lookup"><span data-stu-id="6c292-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="6c292-109">Zmiany behawioralne spowodowane zmianami w trakcie podwyższania poziomu zdarzeń dotknięcia/piórem do zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="6c292-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="6c292-110">Manipulowanie może zachowywać się inaczej.</span><span class="sxs-lookup"><span data-stu-id="6c292-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="6c292-111">Wartość przeciągnij/upuść nie będzie zawierać odpowiedniej opinii na temat wprowadzania dotykowego.</span><span class="sxs-lookup"><span data-stu-id="6c292-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="6c292-112">(Nie ma to wpływu na wprowadzanie piórem).</span><span class="sxs-lookup"><span data-stu-id="6c292-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="6c292-113">Nie można już inicjować przeciągania/upuszczania w przypadku zdarzeń dotykowych/pióra.</span><span class="sxs-lookup"><span data-stu-id="6c292-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="6c292-114">Może to spowodować, że aplikacja przestanie odpowiadać, dopóki nie zostanie wykryta mysz.</span><span class="sxs-lookup"><span data-stu-id="6c292-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="6c292-115">Zamiast tego deweloperzy powinni inicjować przeciąganie i upuszczanie ze zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="6c292-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="6c292-116">Możliwość skorzystania z obsługi dotyku i pióra na WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="6c292-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="6c292-117">Deweloperzy, którzy chcą włączyć ten stos, mogą dodać następujące elementy do pliku App. config aplikacji:</span><span class="sxs-lookup"><span data-stu-id="6c292-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="6c292-118">Usunięcie tego wpisu lub ustawienie jego wartości `false` powoduje wyłączenie tego opcjonalnego stosu.</span><span class="sxs-lookup"><span data-stu-id="6c292-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c292-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c292-119">See also</span></span>

- [<span data-ttu-id="6c292-120">Przekierowywanie zmian w .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="6c292-120">Retargeting Changes in the .NET Framework 4.7</span></span>](retargeting-changes-in-the-net-framework-4-7.md)
