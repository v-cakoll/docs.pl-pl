---
title: 'Środki zaradcze: Na podstawie wskaźnika Touch i pomocy technicznej pióro'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da7d55b34bc21f0c11f13565d017587b4276bad3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387783"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="4de32-102">Środki zaradcze: Na podstawie wskaźnika Touch i pomocy technicznej pióro</span><span class="sxs-lookup"><span data-stu-id="4de32-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="4de32-103">Aplikacje WPF, docelowa .NET Framework 4.7, które są uruchomione w systemie Windows począwszy od systemu Windows 10 twórców Update można włączyć opcjonalny `WM_POINTER`— na podstawie stosu touch/pióro WPF.</span><span class="sxs-lookup"><span data-stu-id="4de32-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="4de32-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="4de32-104">Impact</span></span>

<span data-ttu-id="4de32-105">Deweloperzy, którzy jawnie nie należy włączać obsługi opartej na wskaźnik touch/pióro powinny być widoczne nie zmiany w zachowaniu touch/pióro WPF.</span><span class="sxs-lookup"><span data-stu-id="4de32-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="4de32-106">Oto obecnie znane problemy z opcjonalnym `WM_POINTER`— na podstawie touch/pióro stosu:</span><span class="sxs-lookup"><span data-stu-id="4de32-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="4de32-107">Brak obsługi pisma odręcznego w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="4de32-107">No support for real-time inking.</span></span>

   <span data-ttu-id="4de32-108">Gdy wtyczek pisma odręcznego i Pióro nadal działać, są przetwarzane w wątku interfejsu użytkownika, co może prowadzić do niskiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="4de32-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="4de32-109">Zachowania zmian z powodu zmian w ramach podwyższenia poziomu z touch/pióro zdarzenia do zdarzenia myszy.</span><span class="sxs-lookup"><span data-stu-id="4de32-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="4de32-110">Manipulowanie może zachowywać się inaczej.</span><span class="sxs-lookup"><span data-stu-id="4de32-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="4de32-111">Przeciągnij i upuść nie zostanie wyświetlone odpowiednie opinię dotyczącą wprowadzania dotykowego.</span><span class="sxs-lookup"><span data-stu-id="4de32-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="4de32-112">(Nie dotyczy to wprowadzania danych piórem.)</span><span class="sxs-lookup"><span data-stu-id="4de32-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="4de32-113">Nie można zainicjować przeciągnij i upuść zdarzeń touch/pióra.</span><span class="sxs-lookup"><span data-stu-id="4de32-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="4de32-114">To potencjalnie zawieszenie aplikacji, dopóki nie zostanie wykryty wejście myszy.</span><span class="sxs-lookup"><span data-stu-id="4de32-114">This can potentially hang the application until mouse input is detected.</span></span> <span data-ttu-id="4de32-115">Zamiast tego deweloperzy należy zainicjować przeciągnij i upuść z zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="4de32-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="4de32-116">Zgody na korzystanie z pomocy technicznej na podstawie WM_POINTER touch/pióra</span><span class="sxs-lookup"><span data-stu-id="4de32-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="4de32-117">Deweloperów, którzy chcą włączyć ten stos można dodać następujące do pliku app.config ich aplikacji:</span><span class="sxs-lookup"><span data-stu-id="4de32-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="4de32-118">Usunięcie tego wpisu lub ustawienie jej wartość `false` wyłącza to opcjonalne stosu.</span><span class="sxs-lookup"><span data-stu-id="4de32-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="4de32-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4de32-119">See also</span></span>

[<span data-ttu-id="4de32-120">Zmiany w przekierowywaniu w programie .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="4de32-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
