---
title: Zapisywanie w projektach przeznaczonych dla programu .NET Framework 3.0 i 3.5 w programie Visual Studio 2010
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc6657bad5cc11eaa723c733319673468749b79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a><span data-ttu-id="69d39-102">Zapisywanie w projektach przeznaczonych dla programu .NET Framework 3.0 i 3.5 w programie Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="69d39-102">Writing Projects Targeting the .NET Framework 3.0 and 3.5 in Visual Studio 2010</span></span>
<span data-ttu-id="69d39-103">Można użyć [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] do tworzenia projektów przeznaczonych [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 3.0 lub 3.5.</span><span class="sxs-lookup"><span data-stu-id="69d39-103">You can use [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] to create projects that target the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 3.0 or 3.5.</span></span> <span data-ttu-id="69d39-104">W tym temacie opisano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="69d39-104">This topic describes how to do this.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69d39-105">Podczas dodawania działań, upewnij się, że żądanej wersji [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="69d39-105">When adding activities, make sure that the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] is set.</span></span> <span data-ttu-id="69d39-106">Zmiana wersji docelowej przepływu pracy, po dodaniu działania spowoduje niepowodzenie sprawdzania poprawności przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="69d39-106">Changing the target version of the workflow after activities are added will cause the workflow to fail validation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="69d39-107">Otwieranie istniejących przepływów pracy w [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] zawierających .net Framework 3.5 działania spowoduje, że wystąpił błąd w `this.SetValue()`.</span><span class="sxs-lookup"><span data-stu-id="69d39-107">Opening existing workflows in [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] that have .Net Framework 3.5 activities will cause an error at `this.SetValue()`.</span></span> <span data-ttu-id="69d39-108">Aby można było otworzyć projektów utworzonych w poprzednich wersjach programu .net Framework, najpierw otwórz pusty przepływu pracy w Projektancie i Dodaj .net Framework 3.5 działania.</span><span class="sxs-lookup"><span data-stu-id="69d39-108">In order to open projects created with previous versions of the .Net Framework, first open a blank workflow in the designer and add a .Net Framework 3.5 activity.</span></span>  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a><span data-ttu-id="69d39-109">Aby utworzyć środowiska .NET Framework 3.0 lub 3.5 projektu za pomocą programu Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="69d39-109">To create a .NET Framework  3.0 or 3.5 project with Visual Studio 2010</span></span>  
  
1.  <span data-ttu-id="69d39-110">Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69d39-110">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="69d39-111">Wybierz **pliku**, **nowe**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="69d39-111">Select **File**, **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="69d39-112">Na liście rozwijanej w górnej części okna dialogowego wybierz żądaną wersję [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69d39-112">In the drop-down list at the top of the dialog box, select the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a><span data-ttu-id="69d39-113">Aby uaktualnić wersję docelową programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="69d39-113">To upgrade the targeted version of the .NET Framework</span></span>  
  
1.  <span data-ttu-id="69d39-114">Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="69d39-114">Right-click the project in Solution Explorer, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="69d39-115">W **platformy docelowej** listy rozwijanej wybierz odpowiednią wersję.</span><span class="sxs-lookup"><span data-stu-id="69d39-115">In the **Target Framework** drop-down list, select the desired version.</span></span>
