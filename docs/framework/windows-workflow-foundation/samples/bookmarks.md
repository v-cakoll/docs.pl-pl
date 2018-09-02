---
title: Bookmarks2
ms.date: 03/30/2017
ms.assetid: 035fadb2-49fa-4ac7-b398-daf138f66e87
ms.openlocfilehash: 6bcc4e27566b9c8553e0792558c281a6b1f1caf4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387392"
---
# <a name="bookmarks"></a><span data-ttu-id="110c5-102">Zakładki</span><span class="sxs-lookup"><span data-stu-id="110c5-102">Bookmarks</span></span>
<span data-ttu-id="110c5-103">Niniejszy przykład pokazuje, jak pisać niestandardowe działanie, które tworzy zakładki dla danych wejściowych zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="110c5-103">This sample demonstrates how to write a custom activity that creates a bookmark to receive external input.</span></span> <span data-ttu-id="110c5-104">Przykład obejmuje również podstawowa Aplikacja konsoli używa niestandardowego działania w przepływie pracy, który pokazuje, jak odnaleźć i wznowienie zakładki skojarzone z uruchomionego wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="110c5-104">The sample also includes a basic console application that uses the custom activity in a workflow and shows how to discover and resume bookmarks associated with a running workflow instance.</span></span> <span data-ttu-id="110c5-105">Aby uzyskać więcej informacji na temat zakładek, zobacz [zakładki](../../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="110c5-105">For more information about bookmarks, see [Bookmarks](../../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="110c5-106">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="110c5-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="110c5-107">Otwórz rozwiązanie przykładowe Bookmarks.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="110c5-107">Open the Bookmarks.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="110c5-108">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="110c5-108">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="110c5-109">Aby uruchomić przykład, naciśnij klawisze CTRLl + F5.</span><span class="sxs-lookup"><span data-stu-id="110c5-109">To run the sample, press CTRLl + F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="110c5-110">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="110c5-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="110c5-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="110c5-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="110c5-112">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="110c5-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="110c5-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="110c5-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CodeBodied\Bookmarks`