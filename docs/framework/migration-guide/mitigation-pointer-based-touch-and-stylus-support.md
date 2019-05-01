---
title: 'Środki zaradcze: Oparte na wskaźnikach Dotyk i pomocy technicznej pióra'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d750087cc000ad31a24d91411c0885a75d59e74f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871349"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="15309-102">Środki zaradcze: Oparte na wskaźnikach Dotyk i pomocy technicznej pióra</span><span class="sxs-lookup"><span data-stu-id="15309-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="15309-103">Aplikacje WPF, docelowych programu .NET Framework 4.7, które są uruchomione w systemach Windows, począwszy od systemu Windows 10 Creators Update można włączyć opcjonalnie `WM_POINTER`— na podstawie stosu dotyk/pióro WPF.</span><span class="sxs-lookup"><span data-stu-id="15309-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="15309-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="15309-104">Impact</span></span>

<span data-ttu-id="15309-105">Deweloperzy, którzy nie jawnie włączyć obsługę dotyku/pióro oparte na wskaźnikach powinien zostać wyświetlony bez zmian w zachowaniu dotyk/pióro WPF.</span><span class="sxs-lookup"><span data-stu-id="15309-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="15309-106">Poniżej przedstawiono obecnie znane problemy z opcjonalnym `WM_POINTER`— na podstawie dotyk/pióro stosu:</span><span class="sxs-lookup"><span data-stu-id="15309-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="15309-107">Brak obsługi pisma odręcznego w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="15309-107">No support for real-time inking.</span></span>

   <span data-ttu-id="15309-108">Gdy wtyczek pisma odręcznego i Pióro nadal działać, są przetwarzane w wątku interfejsu użytkownika, co może prowadzić do pogorszenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="15309-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="15309-109">Zachowania zmian z powodu zmian w ramach podwyższenia poziomu dotyk/pióro zdarzeń do zdarzenia myszy.</span><span class="sxs-lookup"><span data-stu-id="15309-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="15309-110">Manipulowanie może zachowywać się inaczej.</span><span class="sxs-lookup"><span data-stu-id="15309-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="15309-111">Przeciągania i upuszczania nie będzie widoczna odpowiednią opinię dotyczącą wprowadzania dotykowego.</span><span class="sxs-lookup"><span data-stu-id="15309-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="15309-112">(Nie wpływa to wejście pióra.)</span><span class="sxs-lookup"><span data-stu-id="15309-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="15309-113">Już nie można zainicjować przeciągania i upuszczania zdarzeń dotyk/pióra.</span><span class="sxs-lookup"><span data-stu-id="15309-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="15309-114">To potencjalnie zawieszanie aplikacji, dopóki nie zostanie wykryte wejście myszy.</span><span class="sxs-lookup"><span data-stu-id="15309-114">This can potentially hang the application until mouse input is detected.</span></span> <span data-ttu-id="15309-115">Zamiast tego deweloperów należy zainicjować przeciągnij i upuść z zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="15309-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="15309-116">Zgody na korzystanie z pomocy technicznej na podstawie WM_POINTER dotyk/pióra</span><span class="sxs-lookup"><span data-stu-id="15309-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="15309-117">Deweloperzy, którzy chcą włączyć ten stos może Dodaj następujący element do pliku app.config swoich aplikacji:</span><span class="sxs-lookup"><span data-stu-id="15309-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="15309-118">Usunięcie tego wpisu lub ustawiając jej wartość na `false` wyłącza ten stos opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="15309-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="15309-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15309-119">See also</span></span>

- [<span data-ttu-id="15309-120">Zmiany retargetingu w programie .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="15309-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
