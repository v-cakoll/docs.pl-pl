---
ms.openlocfilehash: 72acd0029d0189de1c724856572957f111b9d18f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804758"
---
## <a name="installation-instructions"></a><span data-ttu-id="61d55-101">Instrukcje instalacji</span><span class="sxs-lookup"><span data-stu-id="61d55-101">Installation instructions</span></span> 

<span data-ttu-id="61d55-102">Istnieją dwa różne sposoby, aby znaleźć **zestawu SDK platformy kompilatora .NET** w **Instalatora programu Visual Studio**:</span><span class="sxs-lookup"><span data-stu-id="61d55-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-workloads-view"></a><span data-ttu-id="61d55-103">Instalowanie przy użyciu widoku obciążeń</span><span class="sxs-lookup"><span data-stu-id="61d55-103">Install using the Workloads view</span></span>

<span data-ttu-id="61d55-104">Zestaw SDK platformy kompilatora .NET nie jest automatycznie wybierany jako część obciążenia projektowania rozszerzenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="61d55-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="61d55-105">Musisz wybrać go jako składnik opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="61d55-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="61d55-106">Uruchom **Instalatora programu Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="61d55-106">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="61d55-107">Wybierz **zmodyfikować**</span><span class="sxs-lookup"><span data-stu-id="61d55-107">Select **Modify**</span></span> 
1. <span data-ttu-id="61d55-108">Sprawdź **programowanie rozszerzeń programu Visual Studio** obciążenia.</span><span class="sxs-lookup"><span data-stu-id="61d55-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="61d55-109">Otwórz **programowanie rozszerzeń programu Visual Studio** węzeł w drzewie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="61d55-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="61d55-110">Pole wyboru dla **zestawu SDK platformy kompilatora .NET**.</span><span class="sxs-lookup"><span data-stu-id="61d55-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="61d55-111">Znajdziesz go ostatnio w ramach opcjonalnych składników.</span><span class="sxs-lookup"><span data-stu-id="61d55-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="61d55-112">Opcjonalnie można też **Edytor DGML** do wyświetlania wykresów w wizualizatorze:</span><span class="sxs-lookup"><span data-stu-id="61d55-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="61d55-113">Otwórz **poszczególne składniki** węzeł w drzewie podsumowania.</span><span class="sxs-lookup"><span data-stu-id="61d55-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="61d55-114">Pole wyboru dla **Edytor DGML**</span><span class="sxs-lookup"><span data-stu-id="61d55-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-individual-components-tab"></a><span data-ttu-id="61d55-115">Instalowanie przy użyciu na karcie poszczególne składniki</span><span class="sxs-lookup"><span data-stu-id="61d55-115">Install using the Individual components tab</span></span>

1. <span data-ttu-id="61d55-116">Uruchom **Instalatora programu Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="61d55-116">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="61d55-117">Wybierz **zmodyfikować**</span><span class="sxs-lookup"><span data-stu-id="61d55-117">Select **Modify**</span></span> 
1. <span data-ttu-id="61d55-118">Wybierz **poszczególne składniki** kartę</span><span class="sxs-lookup"><span data-stu-id="61d55-118">Select the **Individual components** tab</span></span> 
1. <span data-ttu-id="61d55-119">Pole wyboru dla **zestawu SDK platformy kompilatora .NET**.</span><span class="sxs-lookup"><span data-stu-id="61d55-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="61d55-120">Znajdziesz ją u góry strony, w obszarze **kompilatory, narzędzia do kompilacji i środowiska uruchomieniowe** sekcji.</span><span class="sxs-lookup"><span data-stu-id="61d55-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="61d55-121">Opcjonalnie można też **Edytor DGML** do wyświetlania wykresów w wizualizatorze:</span><span class="sxs-lookup"><span data-stu-id="61d55-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="61d55-122">Pole wyboru dla **Edytor DGML**.</span><span class="sxs-lookup"><span data-stu-id="61d55-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="61d55-123">Znajdziesz go w folderze **kodu narzędzia** sekcji.</span><span class="sxs-lookup"><span data-stu-id="61d55-123">You'll find it under the **Code tools** section.</span></span>
