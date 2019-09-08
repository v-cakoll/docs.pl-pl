---
title: Środki zaradcze Obsługa dotykowa i pióra na podstawie wskaźnika
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67e41450ed69d73a4b27b0aa37974ae01be69687
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779238"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="9096a-102">Środki zaradcze Obsługa dotykowa i pióra na podstawie wskaźnika</span><span class="sxs-lookup"><span data-stu-id="9096a-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="9096a-103">Aplikacje WPF, które są przeznaczone dla .NET Framework 4,7 i działają w systemach Windows, począwszy od aktualizacji systemu Windows 10 Creators `WM_POINTER`, mogą umożliwić opcjonalny stos dotykowy/pióra WPF.</span><span class="sxs-lookup"><span data-stu-id="9096a-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="9096a-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="9096a-104">Impact</span></span>

<span data-ttu-id="9096a-105">Deweloperzy, którzy nie umożliwiają jawnie włączania obsługi dotykowej opartej na wskaźnikach, nie powinni zmieniać zachowań dotykowych i pióra WPF.</span><span class="sxs-lookup"><span data-stu-id="9096a-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="9096a-106">Poniżej przedstawiono bieżące znane problemy z opcjonalnym `WM_POINTER`stosem dotyk/piórem:</span><span class="sxs-lookup"><span data-stu-id="9096a-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="9096a-107">Brak obsługi pisma odręcznego w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="9096a-107">No support for real-time inking.</span></span>

   <span data-ttu-id="9096a-108">Podczas gdy wtyczki pisma odręcznego i pióra nadal działają, są przetwarzane w wątku interfejsu użytkownika, co może prowadzić do słabej wydajności.</span><span class="sxs-lookup"><span data-stu-id="9096a-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="9096a-109">Zmiany behawioralne spowodowane zmianami w trakcie podwyższania poziomu zdarzeń dotknięcia/piórem do zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="9096a-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="9096a-110">Manipulowanie może zachowywać się inaczej.</span><span class="sxs-lookup"><span data-stu-id="9096a-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="9096a-111">Wartość przeciągnij/upuść nie będzie zawierać odpowiedniej opinii na temat wprowadzania dotykowego.</span><span class="sxs-lookup"><span data-stu-id="9096a-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="9096a-112">(Nie ma to wpływu na wprowadzanie piórem).</span><span class="sxs-lookup"><span data-stu-id="9096a-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="9096a-113">Nie można już inicjować przeciągania/upuszczania w przypadku zdarzeń dotykowych/pióra.</span><span class="sxs-lookup"><span data-stu-id="9096a-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="9096a-114">Może to spowodować, że aplikacja przestanie odpowiadać, dopóki nie zostanie wykryta mysz.</span><span class="sxs-lookup"><span data-stu-id="9096a-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="9096a-115">Zamiast tego deweloperzy powinni inicjować przeciąganie i upuszczanie ze zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="9096a-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="9096a-116">Możliwość skorzystania z obsługi dotyku i pióra na WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="9096a-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="9096a-117">Deweloperzy, którzy chcą włączyć ten stos, mogą dodać następujące elementy do pliku App. config aplikacji:</span><span class="sxs-lookup"><span data-stu-id="9096a-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="9096a-118">Usunięcie tego wpisu lub ustawienie jego wartości powoduje `false` wyłączenie tego opcjonalnego stosu.</span><span class="sxs-lookup"><span data-stu-id="9096a-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="9096a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9096a-119">See also</span></span>

- [<span data-ttu-id="9096a-120">Przekierowywanie zmian w .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="9096a-120">Retargeting Changes in the .NET Framework 4.7</span></span>](retargeting-changes-in-the-net-framework-4-7.md)
