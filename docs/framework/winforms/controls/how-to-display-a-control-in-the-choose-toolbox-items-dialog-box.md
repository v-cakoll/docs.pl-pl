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
ms.openlocfilehash: fdda72d60b0f18e76b03e9b7f05060a09763a3f7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488264"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="55079-102">Porady: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="55079-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="55079-103">Podczas tworzenia i Rozłóż kontrolki, może okazać się te kontrolki, które będą wyświetlane na **wybierz elementy przybornika** okno dialogowe, które jest wyświetlany po kliknięciu prawym przyciskiem myszy **przybornika** i wybierz  **Wybierz elementy**.</span><span class="sxs-lookup"><span data-stu-id="55079-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="55079-104">Można włączyć kontroli nad pojawią się w tym oknie dialogowym za pomocą procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="55079-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="55079-105">Aby wyświetlić formant w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="55079-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
-   <span data-ttu-id="55079-106">Zainstaluj zestaw formantu do globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="55079-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="55079-107">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="55079-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="55079-108">—lub—</span><span class="sxs-lookup"><span data-stu-id="55079-108">-or-</span></span>  
  
-   <span data-ttu-id="55079-109">Zarejestruj kontrolki i jego skojarzone zestawy czasu projektowania przy użyciu procedury rejestracji AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="55079-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="55079-110">AssemblyFoldersEx prowadzi do lokalizacji rejestru, w której inni dostawcy przechowywać ścieżki dla każdej wersji framework, które obsługują.</span><span class="sxs-lookup"><span data-stu-id="55079-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="55079-111">Podczas projektowania rozwiązania można sprawdzić w tej lokalizacji rejestru można znaleźć zestawów odwołań.</span><span class="sxs-lookup"><span data-stu-id="55079-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="55079-112">Skrypt rejestru można określić formanty, które mają być wyświetlane w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="55079-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="55079-113">Aby uzyskać więcej informacji, zobacz [wdrażania kontrolkę niestandardową i zestawy czasu projektowania (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span><span class="sxs-lookup"><span data-stu-id="55079-113">For more information, see [Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55079-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55079-114">See Also</span></span>  
 [<span data-ttu-id="55079-115">Wybierz elementy przybornika, okno dialogowe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="55079-115">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="55079-116">Wdrażanie niestandardowego formantu i zestawy czasu projektowania (Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="55079-116">Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)</span></span>](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [<span data-ttu-id="55079-117">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="55079-117">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="55079-118">Instrukcje: instalowanie zestawu w pamięci Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="55079-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="55079-119">Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi</span><span class="sxs-lookup"><span data-stu-id="55079-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
