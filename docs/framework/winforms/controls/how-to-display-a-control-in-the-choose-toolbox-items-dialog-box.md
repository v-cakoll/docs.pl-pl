---
title: 'Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86ec8f9ae76f010ebbc3be393d8d257ba5cfc6b6
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834613"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="8f1e9-102">Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="8f1e9-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>

<span data-ttu-id="8f1e9-103">Podczas opracowywania i rozpowszechniania formantów można chcieć, aby te kontrolki były wyświetlane w oknie dialogowym **Wybierz elementy przybornika** programu Visual Studio, który jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybraniu **pozycji Wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="8f1e9-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box of Visual Studio, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="8f1e9-104">Aby formant był widoczny w tym oknie dialogowym, można użyć procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="8f1e9-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>

<span data-ttu-id="8f1e9-105">Aby wyświetlić swój formant w oknie dialogowym Wybierz elementy przybornika:</span><span class="sxs-lookup"><span data-stu-id="8f1e9-105">To display your control in the Choose Toolbox Items dialog box:</span></span>

- <span data-ttu-id="8f1e9-106">Zainstaluj zestaw kontrolny w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8f1e9-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="8f1e9-107">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../app-domains/install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="8f1e9-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/install-assembly-into-gac.md).</span></span>

  <span data-ttu-id="8f1e9-108">— lub —</span><span class="sxs-lookup"><span data-stu-id="8f1e9-108">-or-</span></span>

- <span data-ttu-id="8f1e9-109">Zarejestruj swój formant i powiązane z nim zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="8f1e9-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="8f1e9-110">AssemblyFoldersEx to lokalizacja w rejestrze, w której dostawcy innych firm przechowują ścieżki dla każdej wersji obsługiwanej platformy.</span><span class="sxs-lookup"><span data-stu-id="8f1e9-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="8f1e9-111">Rozwiązanie czasu projektowania może wyszukać w tej lokalizacji rejestru, aby znaleźć zestawy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="8f1e9-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="8f1e9-112">Skrypt rejestru może określać kontrolki, które mają być wyświetlane w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="8f1e9-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f1e9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f1e9-113">See also</span></span>

- [<span data-ttu-id="8f1e9-114">Opracowywanie formantów Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="8f1e9-114">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="8f1e9-115">Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="8f1e9-115">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/install-assembly-into-gac.md)
- [<span data-ttu-id="8f1e9-116">Przewodnik: automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="8f1e9-116">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
