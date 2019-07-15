---
ms.openlocfilehash: dab6b435a885d862d08f94dd31de79625f19bcc0
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870509"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="35e9d-101">Instrukcje dotyczące instalacji — Instalatora programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35e9d-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="35e9d-102">Istnieją dwa różne sposoby, aby znaleźć **zestawu SDK platformy kompilatora .NET** w **Instalatora programu Visual Studio**:</span><span class="sxs-lookup"><span data-stu-id="35e9d-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="35e9d-103">Instalowanie przy użyciu Instalatora programu Visual Studio — Wyświetlanie obciążeń</span><span class="sxs-lookup"><span data-stu-id="35e9d-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="35e9d-104">Zestaw SDK platformy kompilatora .NET nie jest automatycznie wybierany jako część obciążenia projektowania rozszerzenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35e9d-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="35e9d-105">Musisz wybrać go jako składnik opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="35e9d-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="35e9d-106">Uruchom **Instalatora programu Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="35e9d-106">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="35e9d-107">Wybierz **zmodyfikować**</span><span class="sxs-lookup"><span data-stu-id="35e9d-107">Select **Modify**</span></span> 
1. <span data-ttu-id="35e9d-108">Sprawdź **programowanie rozszerzeń programu Visual Studio** obciążenia.</span><span class="sxs-lookup"><span data-stu-id="35e9d-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="35e9d-109">Otwórz **programowanie rozszerzeń programu Visual Studio** węzeł w drzewie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="35e9d-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="35e9d-110">Pole wyboru dla **zestawu SDK platformy kompilatora .NET**.</span><span class="sxs-lookup"><span data-stu-id="35e9d-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="35e9d-111">Znajdziesz go ostatnio w ramach opcjonalnych składników.</span><span class="sxs-lookup"><span data-stu-id="35e9d-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="35e9d-112">Opcjonalnie można też **Edytor DGML** do wyświetlania wykresów w wizualizatorze:</span><span class="sxs-lookup"><span data-stu-id="35e9d-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="35e9d-113">Otwórz **poszczególne składniki** węzeł w drzewie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="35e9d-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="35e9d-114">Pole wyboru dla **Edytor DGML**</span><span class="sxs-lookup"><span data-stu-id="35e9d-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="35e9d-115">Instalowanie przy użyciu Instalatora programu Visual Studio — karcie poszczególne składniki</span><span class="sxs-lookup"><span data-stu-id="35e9d-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="35e9d-116">Uruchom **Instalatora programu Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="35e9d-116">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="35e9d-117">Wybierz **zmodyfikować**</span><span class="sxs-lookup"><span data-stu-id="35e9d-117">Select **Modify**</span></span> 
1. <span data-ttu-id="35e9d-118">Wybierz **poszczególne składniki** kartę</span><span class="sxs-lookup"><span data-stu-id="35e9d-118">Select the **Individual components** tab</span></span> 
1. <span data-ttu-id="35e9d-119">Pole wyboru dla **zestawu SDK platformy kompilatora .NET**.</span><span class="sxs-lookup"><span data-stu-id="35e9d-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="35e9d-120">Znajdziesz ją u góry strony, w obszarze **kompilatory, narzędzia do kompilacji i środowiska uruchomieniowe** sekcji.</span><span class="sxs-lookup"><span data-stu-id="35e9d-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="35e9d-121">Opcjonalnie można też **Edytor DGML** do wyświetlania wykresów w wizualizatorze:</span><span class="sxs-lookup"><span data-stu-id="35e9d-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="35e9d-122">Pole wyboru dla **Edytor DGML**.</span><span class="sxs-lookup"><span data-stu-id="35e9d-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="35e9d-123">Znajdziesz go w folderze **kodu narzędzia** sekcji.</span><span class="sxs-lookup"><span data-stu-id="35e9d-123">You'll find it under the **Code tools** section.</span></span>
