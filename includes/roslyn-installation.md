---
ms.openlocfilehash: 2872c5909b382e01fdd231019a12970caa3b77d2
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72526766"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="87184-101">Instrukcje dotyczące instalacji — Instalator programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="87184-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="87184-102">Istnieją dwa różne sposoby znajdowania **zestawu SDK .NET compiler platform** w **Instalator programu Visual Studio**:</span><span class="sxs-lookup"><span data-stu-id="87184-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="87184-103">Instalowanie przy użyciu widoku Instalator programu Visual Studio — obciążenia</span><span class="sxs-lookup"><span data-stu-id="87184-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="87184-104">Zestaw .NET Compiler Platform SDK nie jest automatycznie wybierany jako część obciążenia programowania rozszerzeń programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87184-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="87184-105">Należy zaznaczyć go jako składnik opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="87184-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="87184-106">Uruchom **Instalator programu Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="87184-106">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="87184-107">Wybieranie opcji **Modyfikuj**</span><span class="sxs-lookup"><span data-stu-id="87184-107">Select **Modify**</span></span>
1. <span data-ttu-id="87184-108">Sprawdź obciążenie **programowanie rozszerzenia programu Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="87184-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="87184-109">Otwórz węzeł **programowanie rozszerzeń programu Visual Studio** w drzewie podsumowującym.</span><span class="sxs-lookup"><span data-stu-id="87184-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="87184-110">Zaznacz pole wyboru **.NET COMPILER Platform SDK**.</span><span class="sxs-lookup"><span data-stu-id="87184-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="87184-111">Znajdziesz go jako ostatni w obszarze opcjonalnych składników.</span><span class="sxs-lookup"><span data-stu-id="87184-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="87184-112">Opcjonalnie, aby **Edytor DGML** wyświetlał wykresy w wizualizatorze:</span><span class="sxs-lookup"><span data-stu-id="87184-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="87184-113">Otwórz węzeł **poszczególne składniki** w drzewie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="87184-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="87184-114">Zaznacz pole wyboru dla **edytora DGML**</span><span class="sxs-lookup"><span data-stu-id="87184-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="87184-115">Instalowanie przy użyciu karty Instalator programu Visual Studio poszczególnych składników</span><span class="sxs-lookup"><span data-stu-id="87184-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="87184-116">Uruchom **Instalator programu Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="87184-116">Run **Visual Studio Installer**</span></span>
1. <span data-ttu-id="87184-117">Wybieranie opcji **Modyfikuj**</span><span class="sxs-lookup"><span data-stu-id="87184-117">Select **Modify**</span></span>
1. <span data-ttu-id="87184-118">Wybierz kartę **poszczególne składniki**</span><span class="sxs-lookup"><span data-stu-id="87184-118">Select the **Individual components** tab</span></span>
1. <span data-ttu-id="87184-119">Zaznacz pole wyboru **.NET COMPILER Platform SDK**.</span><span class="sxs-lookup"><span data-stu-id="87184-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="87184-120">Znajdziesz go u góry w sekcji **kompilatory, narzędzia kompilacji i środowiska uruchomieniowe** .</span><span class="sxs-lookup"><span data-stu-id="87184-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="87184-121">Opcjonalnie, aby **Edytor DGML** wyświetlał wykresy w wizualizatorze:</span><span class="sxs-lookup"><span data-stu-id="87184-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="87184-122">Zaznacz pole wyboru **Edytor DGML**.</span><span class="sxs-lookup"><span data-stu-id="87184-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="87184-123">Znajdziesz go w sekcji **Narzędzia kodu** .</span><span class="sxs-lookup"><span data-stu-id="87184-123">You'll find it under the **Code tools** section.</span></span>
