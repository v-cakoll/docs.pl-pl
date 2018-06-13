---
title: 'Porady: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: 7e452c3d3be131b891ee26555e3085fc31b04517
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531508"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="9b3e1-102">Porady: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="9b3e1-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="9b3e1-103">Jak należy opracować i rozpowszechnić formantów, może być tych kontrolek w wynikach **wybierz elementy przybornika** okno dialogowe, w którym jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybierz  **Wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="9b3e1-104">Można włączyć formantu pojawią się w tym oknie dialogowym przy użyciu procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="9b3e1-105">Aby wyświetlić formantu w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="9b3e1-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
-   <span data-ttu-id="9b3e1-106">Zainstaluj z zestawu formantu do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="9b3e1-107">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="9b3e1-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="9b3e1-108">—lub—</span><span class="sxs-lookup"><span data-stu-id="9b3e1-108">-or-</span></span>  
  
-   <span data-ttu-id="9b3e1-109">Zarejestruj formantu i jego skojarzone zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="9b3e1-110">AssemblyFoldersEx jest lokalizacji rejestru, w którym dostawców innych firm przechowywać ścieżki dla każdej wersji platformy, które obsługują.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="9b3e1-111">Podczas projektowania rozwiązania mogą zobaczyć w tej lokalizacji rejestru, aby znaleźć zestawów odwołań.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="9b3e1-112">Skrypt rejestru można określić formanty, które mają być wyświetlane w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="9b3e1-113">Aby uzyskać więcej informacji, zobacz [wdrażanie formant niestandardowy i czasu projektowania zestawy (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span><span class="sxs-lookup"><span data-stu-id="9b3e1-113">For more information, see [Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b3e1-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b3e1-114">See Also</span></span>  
 [<span data-ttu-id="9b3e1-115">Wybierz elementy przybornika, okno dialogowe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="9b3e1-115">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="9b3e1-116">Wdrażanie kontrolkę niestandardową oraz czasu projektowania zestawy (Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="9b3e1-116">Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)</span></span>](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [<span data-ttu-id="9b3e1-117">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="9b3e1-117">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="9b3e1-118">Instrukcje: instalowanie zestawu w pamięci Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="9b3e1-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="9b3e1-119">Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="9b3e1-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
