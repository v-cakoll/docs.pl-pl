---
title: Przykładowe działanie kompensacyjne
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557655"
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="f51b2-102">Przykładowe działanie kompensacyjne</span><span class="sxs-lookup"><span data-stu-id="f51b2-102">Compensable Activity Sample</span></span>
<span data-ttu-id="f51b2-103">W tym przykładzie przedstawiono sposób użycia `CompensableActivity` działania do definiowania zadań do wykonania dla danej akcji podczas wykonywania normalnych i pracy, które są niezbędne do wykonania celu kompensacji tę akcję, jeśli to konieczne w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="f51b2-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="f51b2-104">Pierwsza część przykład pokazuje, jak jednostki pracy kompensacyjne mogą być definiowane w Windows Workflow Foundation (WF) przy użyciu `CompensableActivity` działanie i jak są one wykonywane w pomyślnym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="f51b2-104">The first part of the sample shows how units of compensable work can be defined in Windows Workflow Foundation (WF) using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="f51b2-105">Druga część przykład pokazuje, jak te same jednostki pracy kompensacyjne automatycznie zajmie się rekompensaty po osiągnięciu nieoczekiwane zdarzenie, a wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="f51b2-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f51b2-106">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="f51b2-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f51b2-107">Za pomocą programu Visual Studio 2010, otwórz CompensableActivity.sln.</span><span class="sxs-lookup"><span data-stu-id="f51b2-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="f51b2-108">Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f51b2-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f51b2-109">Uruchom aplikację, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="f51b2-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f51b2-110">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f51b2-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f51b2-111">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f51b2-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f51b2-112">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="f51b2-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f51b2-113">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f51b2-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`