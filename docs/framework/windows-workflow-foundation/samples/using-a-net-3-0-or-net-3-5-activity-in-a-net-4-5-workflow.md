---
title: Przy użyciu platformy .NET Framework 3.0 lub .NET Framework 3.5 działania w przepływie pracy .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
ms.openlocfilehash: ab2e93918617bd1ca21fb32878d446db0dd2ef16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514902"
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a><span data-ttu-id="a3bc2-102">Przy użyciu platformy .NET Framework 3.0 lub .NET Framework 3.5 działania w przepływie pracy .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="a3bc2-102">Using a .NET Framework 3.0 or .NET Framework 3.5 Activity in a .NET Framework 4.5 Workflow</span></span>
<span data-ttu-id="a3bc2-103"><xref:System.Activities.Statements.Interop> Działania umożliwia uruchamianie działania .NET Framework 3.0 Windows Workflow Foundation (WF), w ramach [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a3bc2-103">The <xref:System.Activities.Statements.Interop> activity allows you to run a .NET Framework 3.0 Windows Workflow Foundation (WF) activity within a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="a3bc2-104">W tym przykładzie przedstawiono sposób użycia <xref:System.Activities.Statements.Interop> działanie, aby przekazać ciąg jako argument do niestandardowego [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] działania.</span><span class="sxs-lookup"><span data-stu-id="a3bc2-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Interop> activity to pass a string as an argument to a custom [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] activity.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="a3bc2-105">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="a3bc2-105">To use this sample</span></span>  
  
1.  <span data-ttu-id="a3bc2-106">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania SimpleInterop.sln.</span><span class="sxs-lookup"><span data-stu-id="a3bc2-106">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the SimpleInterop.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a3bc2-107">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a3bc2-107">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a3bc2-108">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="a3bc2-108">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a3bc2-109">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a3bc2-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a3bc2-110">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a3bc2-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a3bc2-111">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a3bc2-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a3bc2-112">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a3bc2-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a><span data-ttu-id="a3bc2-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3bc2-113">See Also</span></span>
