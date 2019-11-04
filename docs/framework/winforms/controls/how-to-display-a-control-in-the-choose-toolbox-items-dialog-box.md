---
title: 'Porady: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db4b3ac020e967a6a0c291103d825ac71cebda23
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458281"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="ef2c1-102">Porady: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="ef2c1-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>

<span data-ttu-id="ef2c1-103">Podczas opracowywania i rozpowszechniania formantów można chcieć, aby te kontrolki były wyświetlane w oknie dialogowym **Wybierz elementy przybornika** programu Visual Studio, który jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybraniu **pozycji Wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="ef2c1-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box of Visual Studio, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="ef2c1-104">Aby formant był widoczny w tym oknie dialogowym, można użyć procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="ef2c1-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>

<span data-ttu-id="ef2c1-105">Aby wyświetlić swój formant w oknie dialogowym Wybierz elementy przybornika:</span><span class="sxs-lookup"><span data-stu-id="ef2c1-105">To display your control in the Choose Toolbox Items dialog box:</span></span>

- <span data-ttu-id="ef2c1-106">Zainstaluj zestaw kontrolny w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ef2c1-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="ef2c1-107">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../app-domains/install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="ef2c1-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/install-assembly-into-gac.md).</span></span>

  <span data-ttu-id="ef2c1-108">—lub—</span><span class="sxs-lookup"><span data-stu-id="ef2c1-108">-or-</span></span>

- <span data-ttu-id="ef2c1-109">Zarejestruj swój formant i powiązane z nim zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="ef2c1-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="ef2c1-110">AssemblyFoldersEx to lokalizacja w rejestrze, w której dostawcy innych firm przechowują ścieżki dla każdej wersji obsługiwanej platformy.</span><span class="sxs-lookup"><span data-stu-id="ef2c1-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="ef2c1-111">Rozwiązanie czasu projektowania może wyszukać w tej lokalizacji rejestru, aby znaleźć zestawy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="ef2c1-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="ef2c1-112">Skrypt rejestru może określać kontrolki, które mają być wyświetlane w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="ef2c1-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef2c1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef2c1-113">See also</span></span>

- [<span data-ttu-id="ef2c1-114">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="ef2c1-114">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="ef2c1-115">Instrukcje: instalowanie zestawu w pamięci Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="ef2c1-115">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/install-assembly-into-gac.md)
- [<span data-ttu-id="ef2c1-116">Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="ef2c1-116">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
