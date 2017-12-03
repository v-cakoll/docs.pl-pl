---
title: "Określanie czasu trwania operacji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24f1bc22e088c0198ec8a8f8183611d2b43941b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="55704-102">Określanie czasu trwania operacji usługi</span><span class="sxs-lookup"><span data-stu-id="55704-102">Determining service operation duration</span></span>
<span data-ttu-id="55704-103">Jeśli włączono śledzenie analityczne w [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] łatwo można ustalić czas realizacji dla operacji usługi, sprawdzając dziennik zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55704-103">If analytic tracing is enabled in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="55704-104">W tym temacie przedstawiono sposób określania ilości czas do ukończenia operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="55704-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="55704-105">Określanie czasu wykonywania operacji usługi</span><span class="sxs-lookup"><span data-stu-id="55704-105">Determining service operation execution duration</span></span>  
  
1.  <span data-ttu-id="55704-106">Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="55704-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="55704-107">Jeśli nie włączono śledzenie analityczne, rozwiń węzeł **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji serwera aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="55704-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="55704-108">Wybierz **widoku**, **wyświetlanie analityczne i debugowania dzienniki**.</span><span class="sxs-lookup"><span data-stu-id="55704-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="55704-109">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="55704-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="55704-110">Pozostaw otwarte Podgląd zdarzeń, dzięki czemu można wyświetlać danych śledzenia po uruchomieniu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="55704-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3.  <span data-ttu-id="55704-111">Następnie otwórz folder [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikacja, która zawiera projekt usługi i projekt klienta, który współdziała z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="55704-111">Next, open a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="55704-112">Można tworzyć z takich aplikacji, wykonując [Wprowadzenie — samouczek](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="55704-112">You can create such an application by following the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  <span data-ttu-id="55704-113">Jeśli masz [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zainstalowanych przykładów, możesz otworzyć [wprowadzenie](../../../../../docs/framework/wcf/samples/getting-started-sample.md), zawierającą ukończone projekt utworzony w samouczku.</span><span class="sxs-lookup"><span data-stu-id="55704-113">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="55704-114">Wykonanie tych aplikacji serwera, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="55704-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="55704-115">Uruchom aplikację klienta przez kliknięcie prawym przyciskiem myszy **klienta** projekt i wybierając **debugowania**, **uruchomić nowe wystąpienie**.</span><span class="sxs-lookup"><span data-stu-id="55704-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5.  <span data-ttu-id="55704-116">W Podglądzie zdarzeń Odśwież dziennika analityczne i posortuj zdarzenia według identyfikatora zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="55704-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="55704-117">Poszukaj zdarzeń o identyfikatorze zdarzenia [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span><span class="sxs-lookup"><span data-stu-id="55704-117">Look for events with Event ID [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span></span>  <span data-ttu-id="55704-118">Te zdarzenia zostaną wyświetlone, jakie operacje zostały wykonane, a czas trwania operacji został.</span><span class="sxs-lookup"><span data-stu-id="55704-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="55704-119">Następujące zdarzenie zawiera czas trwania operacji dodawania.</span><span class="sxs-lookup"><span data-stu-id="55704-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
