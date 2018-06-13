---
title: Zapisywanie w projektach przeznaczonych dla programu .NET Framework 3.0 i 3.5 w programie Visual Studio 2010
ms.date: 03/30/2017
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
ms.openlocfilehash: 1469ce2906c1101bae4098cbcabd4a10a64c1c7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513830"
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a><span data-ttu-id="2685e-102">Zapisywanie w projektach przeznaczonych dla programu .NET Framework 3.0 i 3.5 w programie Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="2685e-102">Writing Projects Targeting the .NET Framework 3.0 and 3.5 in Visual Studio 2010</span></span>
<span data-ttu-id="2685e-103">Można użyć [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] do tworzenia projektów przeznaczonych [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 3.0 lub 3.5.</span><span class="sxs-lookup"><span data-stu-id="2685e-103">You can use [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] to create projects that target the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 3.0 or 3.5.</span></span> <span data-ttu-id="2685e-104">W tym temacie opisano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="2685e-104">This topic describes how to do this.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2685e-105">Podczas dodawania działań, upewnij się, że żądanej wersji [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="2685e-105">When adding activities, make sure that the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] is set.</span></span> <span data-ttu-id="2685e-106">Zmiana wersji docelowej przepływu pracy, po dodaniu działania spowoduje niepowodzenie sprawdzania poprawności przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2685e-106">Changing the target version of the workflow after activities are added will cause the workflow to fail validation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2685e-107">Otwieranie istniejących przepływów pracy w [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] zawierających .net Framework 3.5 działania spowoduje, że wystąpił błąd w `this.SetValue()`.</span><span class="sxs-lookup"><span data-stu-id="2685e-107">Opening existing workflows in [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] that have .Net Framework 3.5 activities will cause an error at `this.SetValue()`.</span></span> <span data-ttu-id="2685e-108">Aby można było otworzyć projektów utworzonych w poprzednich wersjach programu .net Framework, najpierw otwórz pusty przepływu pracy w Projektancie i Dodaj .net Framework 3.5 działania.</span><span class="sxs-lookup"><span data-stu-id="2685e-108">In order to open projects created with previous versions of the .Net Framework, first open a blank workflow in the designer and add a .Net Framework 3.5 activity.</span></span>  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a><span data-ttu-id="2685e-109">Aby utworzyć środowiska .NET Framework 3.0 lub 3.5 projektu za pomocą programu Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="2685e-109">To create a .NET Framework  3.0 or 3.5 project with Visual Studio 2010</span></span>  
  
1.  <span data-ttu-id="2685e-110">Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2685e-110">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="2685e-111">Wybierz **pliku**, **nowe**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="2685e-111">Select **File**, **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="2685e-112">Na liście rozwijanej w górnej części okna dialogowego wybierz żądaną wersję [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2685e-112">In the drop-down list at the top of the dialog box, select the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a><span data-ttu-id="2685e-113">Aby uaktualnić wersję docelową programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2685e-113">To upgrade the targeted version of the .NET Framework</span></span>  
  
1.  <span data-ttu-id="2685e-114">Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2685e-114">Right-click the project in Solution Explorer, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2685e-115">W **platformy docelowej** listy rozwijanej wybierz odpowiednią wersję.</span><span class="sxs-lookup"><span data-stu-id="2685e-115">In the **Target Framework** drop-down list, select the desired version.</span></span>
