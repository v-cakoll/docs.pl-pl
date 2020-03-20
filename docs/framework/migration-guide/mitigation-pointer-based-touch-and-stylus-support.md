---
title: 'Łagodzenie: Obsługa dotykowa i rysików oparta na wskaźnikach'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77094478"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="ae090-102">Łagodzenie: Obsługa dotykowa i rysików oparta na wskaźnikach</span><span class="sxs-lookup"><span data-stu-id="ae090-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="ae090-103">Aplikacje WPF, które są przeznaczone dla programu .NET Framework 4.7 i są `WM_POINTER`uruchomione w systemie Windows, począwszy od aktualizacji Windows 10 Creators Update, mogą włączyć opcjonalny stos WPF touch/pisak.</span><span class="sxs-lookup"><span data-stu-id="ae090-103">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="ae090-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="ae090-104">Impact</span></span>

<span data-ttu-id="ae090-105">Deweloperzy, którzy nie jawnie włączyć wskaźnik oparte na obsłudze touch/pisaka powinny zobaczyć żadnych zmian w WPF touch/pisak zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ae090-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="ae090-106">Poniżej przedstawiono bieżące `WM_POINTER`znane problemy z opcjonalnym stosem dotykowym/pióra opartym na sobie:</span><span class="sxs-lookup"><span data-stu-id="ae090-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="ae090-107">Brak obsługi pisma oduniającego w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="ae090-107">No support for real-time inking.</span></span>

   <span data-ttu-id="ae090-108">Podczas gdy wtyczek pisma od pisma od pisma od pisma od pisającego i pisaka nadal działają, są one przetwarzane w wątku interfejsu użytkownika, co może prowadzić do niskiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="ae090-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="ae090-109">Zmiany w zachowaniu spowodowane zmianami w promocji ze zdarzeń dotykowych/pisaka na zdarzenia myszy.</span><span class="sxs-lookup"><span data-stu-id="ae090-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="ae090-110">Manipulacja może zachowywać się inaczej.</span><span class="sxs-lookup"><span data-stu-id="ae090-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="ae090-111">Przeciąganie/upuszczanie nie będzie wyświetlane odpowiednie informacje zwrotne dla wprowadzania dotykowego.</span><span class="sxs-lookup"><span data-stu-id="ae090-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="ae090-112">(Nie ma to wpływu na dane wejściowe pisaka).</span><span class="sxs-lookup"><span data-stu-id="ae090-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="ae090-113">Przeciągania/Upuszczania nie można już inicjować podczas zdarzeń dotykowych/pisaka.</span><span class="sxs-lookup"><span data-stu-id="ae090-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="ae090-114">Może to potencjalnie spowodować, że aplikacja przestanie odpowiadać, dopóki nie zostanie wykryte dane wejściowe myszy.</span><span class="sxs-lookup"><span data-stu-id="ae090-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="ae090-115">Zamiast tego deweloperzy powinni zainicjować przeciąganie i upuszczanie ze zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="ae090-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="ae090-116">Rezygnacja z obsługi WM_POINTER dotykowego/rysika</span><span class="sxs-lookup"><span data-stu-id="ae090-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="ae090-117">Deweloperzy, którzy chcą włączyć ten stos, mogą dodać następujące elementy do pliku *app.config* aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae090-117">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="ae090-118">Usunięcie tego wpisu lub `false` ustawienie jego wartości na wyłączenia tego opcjonalnego stosu.</span><span class="sxs-lookup"><span data-stu-id="ae090-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae090-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae090-119">See also</span></span>

- [<span data-ttu-id="ae090-120">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="ae090-120">Application compatibility</span></span>](application-compatibility.md)
