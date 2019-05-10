---
title: 'Instrukcje: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: 4ed3f6ffdf8a86d050b81311c9211767d8b179b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623596"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="8cf80-102">Instrukcje: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="8cf80-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="8cf80-103">Podczas tworzenia i Rozłóż kontrolki, może okazać się te kontrolki, które będą wyświetlane na **wybierz elementy przybornika** okno dialogowe, które jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybierz  **Wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="8cf80-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="8cf80-104">Można włączyć kontroli nad pojawią się w tym oknie dialogowym za pomocą procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="8cf80-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="8cf80-105">Aby wyświetlić formant w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="8cf80-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
- <span data-ttu-id="8cf80-106">Zainstaluj zestaw formantu do globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8cf80-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="8cf80-107">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="8cf80-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="8cf80-108">—lub—</span><span class="sxs-lookup"><span data-stu-id="8cf80-108">-or-</span></span>  
  
- <span data-ttu-id="8cf80-109">Zarejestruj kontrolki i jego skojarzone zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="8cf80-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="8cf80-110">AssemblyFoldersEx prowadzi do lokalizacji rejestru, w której inni dostawcy przechowywać ścieżki dla każdej wersji framework, które obsługują.</span><span class="sxs-lookup"><span data-stu-id="8cf80-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="8cf80-111">Podczas projektowania rozwiązania można sprawdzić w tej lokalizacji rejestru można znaleźć zestawów odwołań.</span><span class="sxs-lookup"><span data-stu-id="8cf80-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="8cf80-112">Skrypt rejestru można określić formanty, które mają być wyświetlane w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="8cf80-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="8cf80-113">Aby uzyskać więcej informacji, zobacz [wdrażania kontrolkę niestandardową i zestawy czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8cf80-113">For more information, see [Deploying a Custom Control and Design-time Assemblies](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cf80-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cf80-114">See also</span></span>

- <span data-ttu-id="8cf80-115">[Wybierz elementy przybornika, okno dialogowe (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8cf80-115">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- <span data-ttu-id="8cf80-116">[Wdrażanie niestandardowego formantu i zestawy czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8cf80-116">[Deploying a Custom Control and Design-time Assemblies](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))</span></span>
- [<span data-ttu-id="8cf80-117">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="8cf80-117">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="8cf80-118">Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8cf80-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [<span data-ttu-id="8cf80-119">Przewodnik: Automatyczne zapełnianie przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="8cf80-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
