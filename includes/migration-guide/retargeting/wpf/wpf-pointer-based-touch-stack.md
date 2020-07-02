---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614894"
---
### <a name="wpf-pointer-based-touch-stack"></a><span data-ttu-id="b973d-101">Stos dotykowy oparty na wskaźnikach WPF</span><span class="sxs-lookup"><span data-stu-id="b973d-101">WPF Pointer-Based Touch Stack</span></span>

#### <a name="details"></a><span data-ttu-id="b973d-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b973d-102">Details</span></span>

<span data-ttu-id="b973d-103">Ta zmiana umożliwia dodanie opcjonalnego stosu dotykowego i pióra WPF WM_POINTER.</span><span class="sxs-lookup"><span data-stu-id="b973d-103">This change adds the ability to enable an optional WM_POINTER based WPF touch/stylus stack.</span></span>  <span data-ttu-id="b973d-104">Deweloperzy, którzy nie włączą jawnie tego, powinni zobaczyć, że nie zmienią się zachowania dotykowego i pióra WPF. Bieżące znane problemy z opcjonalnym stosem WM_POINTER i dotykiem piórem:</span><span class="sxs-lookup"><span data-stu-id="b973d-104">Developers that do not explicitly enable this should see no change in WPF touch/stylus behavior.Current Known Issues With optional WM_POINTER based touch/stylus stack:</span></span>

- <span data-ttu-id="b973d-105">Brak obsługi pisma odręcznego w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="b973d-105">No support for real-time inking.</span></span>
- <span data-ttu-id="b973d-106">Podczas gdy narzędzia króla i StylusPlugIns — będą nadal działać, zostaną one przetworzone w wątku interfejsu użytkownika, co może prowadzić do słabej wydajności.</span><span class="sxs-lookup"><span data-stu-id="b973d-106">While inking and StylusPlugins will still work, they will be processed on the UI Thread which can lead to poor performance.</span></span>
- <span data-ttu-id="b973d-107">Zmiany behawioralne spowodowane zmianami w trakcie podwyższania poziomu zdarzeń dotknięcia/piórem do zdarzeń myszy</span><span class="sxs-lookup"><span data-stu-id="b973d-107">Behavioral changes due to changes in promotion from touch/stylus events to mouse events</span></span>
- <span data-ttu-id="b973d-108">Manipulowanie może zachowywać się inaczej</span><span class="sxs-lookup"><span data-stu-id="b973d-108">Manipulation may behave differently</span></span>
- <span data-ttu-id="b973d-109">Operacja przeciągania/upuszczania nie pokazuje odpowiedniej opinii na temat wprowadzania dotykowego</span><span class="sxs-lookup"><span data-stu-id="b973d-109">Drag/Drop will not show appropriate feedback for touch input</span></span>
- <span data-ttu-id="b973d-110">Nie ma to wpływu na wprowadzanie piórem</span><span class="sxs-lookup"><span data-stu-id="b973d-110">This does not affect stylus input</span></span>
- <span data-ttu-id="b973d-111">Nie można już inicjować przeciągania/upuszczania w przypadku zdarzeń dotykowych/pióra</span><span class="sxs-lookup"><span data-stu-id="b973d-111">Drag/Drop can no longer be initiated on touch/stylus events</span></span>
- <span data-ttu-id="b973d-112">Może to potencjalnie zawiesić aplikację, dopóki nie zostanie wykryta myszą.</span><span class="sxs-lookup"><span data-stu-id="b973d-112">This can potentially hang the application until mouse input is detected.</span></span>
- <span data-ttu-id="b973d-113">Zamiast tego deweloperzy powinni inicjować przeciąganie i upuszczanie ze zdarzeń myszy.</span><span class="sxs-lookup"><span data-stu-id="b973d-113">Instead, developers should initiate drag and drop from mouse events.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b973d-114">Sugestia</span><span class="sxs-lookup"><span data-stu-id="b973d-114">Suggestion</span></span>

<span data-ttu-id="b973d-115">Deweloperzy, którzy chcą włączyć ten stos, mogą dodawać i scalać następujące elementy w pliku App.config aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b973d-115">Developers who wish to enable this stack can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="b973d-116">Usunięcie tego lub ustawienie wartości false spowoduje wyłączenie tego opcjonalnego stosu. Należy zauważyć, że ten stos jest dostępny tylko w Update i nowszych wersjach systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b973d-116">Removing this or setting the value to false will turn this optional stack off.Note that this stack is available only on Windows 10 Creators Update and above.</span></span>

| <span data-ttu-id="b973d-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b973d-117">Name</span></span>    | <span data-ttu-id="b973d-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="b973d-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b973d-119">Zakres</span><span class="sxs-lookup"><span data-stu-id="b973d-119">Scope</span></span>   | <span data-ttu-id="b973d-120">Brzeg</span><span class="sxs-lookup"><span data-stu-id="b973d-120">Edge</span></span>        |
| <span data-ttu-id="b973d-121">Wersja</span><span class="sxs-lookup"><span data-stu-id="b973d-121">Version</span></span> | <span data-ttu-id="b973d-122">4,7</span><span class="sxs-lookup"><span data-stu-id="b973d-122">4.7</span></span>         |
| <span data-ttu-id="b973d-123">Typ</span><span class="sxs-lookup"><span data-stu-id="b973d-123">Type</span></span>    | <span data-ttu-id="b973d-124">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="b973d-124">Retargeting</span></span> |
