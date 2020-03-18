---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72526766"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="8407d-101">Instrukcje instalacji — Instalator programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8407d-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="8407d-102">Istnieją dwa różne sposoby znajdowania **sdk platformy kompilatora .NET** w **Instalatorze programu Visual Studio:**</span><span class="sxs-lookup"><span data-stu-id="8407d-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="8407d-103">Instalowanie przy użyciu widoku Instalator programu Visual Studio — obciążenia</span><span class="sxs-lookup"><span data-stu-id="8407d-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="8407d-104">Zestaw SDK platformy kompilatora .NET nie jest automatycznie wybierany jako część obciążenia programistycznego rozszerzenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8407d-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="8407d-105">Należy wybrać go jako komponent opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8407d-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="8407d-106">Uruchamianie **Instalatora programu Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="8407d-106">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="8407d-107">Wybierz **pozycję Modyfikuj**</span><span class="sxs-lookup"><span data-stu-id="8407d-107">Select **Modify**</span></span>
1. <span data-ttu-id="8407d-108">Sprawdź obciążenie **programistyczne rozszerzenia programu Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="8407d-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="8407d-109">Otwórz węzeł **rozwoju rozszerzenia programu Visual Studio** w drzewie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="8407d-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="8407d-110">Zaznacz pole wyboru Dla **sdk platformy kompilatora .NET**.</span><span class="sxs-lookup"><span data-stu-id="8407d-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="8407d-111">Znajdziesz go ostatnio pod opcjonalnymi składnikami.</span><span class="sxs-lookup"><span data-stu-id="8407d-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="8407d-112">Opcjonalnie należy również edytor **DGML** wyświetlać wykresy w wizualizatoru:</span><span class="sxs-lookup"><span data-stu-id="8407d-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="8407d-113">Otwórz węzeł **Poszczególne składniki** w drzewie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="8407d-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="8407d-114">Zaznacz pole wyboru **edytora DGML**</span><span class="sxs-lookup"><span data-stu-id="8407d-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="8407d-115">Instalowanie przy użyciu karty Instalator programu Visual Studio — poszczególne składniki</span><span class="sxs-lookup"><span data-stu-id="8407d-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="8407d-116">Uruchamianie **Instalatora programu Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="8407d-116">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="8407d-117">Wybierz **pozycję Modyfikuj**</span><span class="sxs-lookup"><span data-stu-id="8407d-117">Select **Modify**</span></span>
1. <span data-ttu-id="8407d-118">Wybieranie karty **Poszczególne komponenty**</span><span class="sxs-lookup"><span data-stu-id="8407d-118">Select the **Individual components** tab</span></span>
1. <span data-ttu-id="8407d-119">Zaznacz pole wyboru Dla **sdk platformy kompilatora .NET**.</span><span class="sxs-lookup"><span data-stu-id="8407d-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="8407d-120">Znajdziesz go u góry w sekcji **Kompilatory, narzędzia kompilacji i czas wykonywania.**</span><span class="sxs-lookup"><span data-stu-id="8407d-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="8407d-121">Opcjonalnie należy również edytor **DGML** wyświetlać wykresy w wizualizatoru:</span><span class="sxs-lookup"><span data-stu-id="8407d-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="8407d-122">Zaznacz pole **wyboru edytora DGML**.</span><span class="sxs-lookup"><span data-stu-id="8407d-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="8407d-123">Znajdziesz go w sekcji **Narzędzia kodu.**</span><span class="sxs-lookup"><span data-stu-id="8407d-123">You'll find it under the **Code tools** section.</span></span>
