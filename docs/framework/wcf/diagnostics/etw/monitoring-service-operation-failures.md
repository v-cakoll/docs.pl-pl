---
title: Monitorowanie niepowodzeń operacji usługi
ms.date: 03/30/2017
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
ms.openlocfilehash: 3d708b537789c8d0decf75df780300c1e185c4c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="monitoring-service-operation-failures"></a><span data-ttu-id="b17cd-102">Monitorowanie niepowodzeń operacji usługi</span><span class="sxs-lookup"><span data-stu-id="b17cd-102">Monitoring Service Operation Failures</span></span>
<span data-ttu-id="b17cd-103">Jeśli śledzenie analityczne jest włączony dla aplikacji, błędów usługi łatwo można monitorować w Podglądzie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b17cd-103">If analytic tracing is enabled for an application, service failures can easily be monitored in the event viewer.</span></span>  <span data-ttu-id="b17cd-104">W tym temacie przedstawiono sposób określania, kiedy operacji usługi nie powiedzie się i sposób określenia, jakie spowodował błąd.</span><span class="sxs-lookup"><span data-stu-id="b17cd-104">This topic demonstrates how to determine when a service operation fails, and how to determine what caused the failure.</span></span>  
  
### <a name="determining-service-operation-failure-information"></a><span data-ttu-id="b17cd-105">Określanie informacji niepowodzenia operacji usługi</span><span class="sxs-lookup"><span data-stu-id="b17cd-105">Determining service operation failure information</span></span>  
  
1.  <span data-ttu-id="b17cd-106">Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="b17cd-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="b17cd-107">Jeśli nie włączono śledzenie analityczne, rozwiń węzeł **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji serwera aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="b17cd-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="b17cd-108">Wybierz **widoku**, **wyświetlanie analityczne i debugowania dzienniki**.</span><span class="sxs-lookup"><span data-stu-id="b17cd-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="b17cd-109">Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="b17cd-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="b17cd-110">Pozostaw otwarte Podgląd zdarzeń, dzięki czemu można będzie wyświetlić dane śledzenia, po operacji usługi nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="b17cd-110">Leave Event Viewer open so that traces can be viewed after the service operation fails.</span></span>  
  
3.  <span data-ttu-id="b17cd-111">Następnie otwórz folder próbki utworzone w [Wprowadzenie — samouczek](../../../../../docs/framework/wcf/getting-started-tutorial.md) w [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] należy pamiętać, że trzeba uruchomić [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] jako administrator, dzięki czemu można utworzyć usługi.</span><span class="sxs-lookup"><span data-stu-id="b17cd-111">Next, open the sample created in the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md) in [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Note that you must run [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] as an administrator so that the service can be created.</span></span> <span data-ttu-id="b17cd-112">Jeśli masz zainstalowanych przykładów WCF, możesz otworzyć [wprowadzenie](../../../../../docs/framework/wcf/samples/getting-started-sample.md), zawierającą ukończone projekt utworzony w samouczku.</span><span class="sxs-lookup"><span data-stu-id="b17cd-112">If you have the WCF samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="b17cd-113">W pliku Program.cs w projekcie serwera, Dodaj następujący wiersz kodu na początku `Divide` metoda `CalculatorService` klasy:</span><span class="sxs-lookup"><span data-stu-id="b17cd-113">In the Program.cs file in the Server project, add the following line of code to the start of the `Divide` method in the `CalculatorService` class:</span></span>  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  <span data-ttu-id="b17cd-114">W pliku Program.cs w projekcie klienta należy zmienić wartość przypisana do wartość2 od zera:</span><span class="sxs-lookup"><span data-stu-id="b17cd-114">In the Program.cs file in the Client project, change the value assigned to value2 to zero:</span></span>  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  <span data-ttu-id="b17cd-115">Uruchom aplikację serwera bez debugowania, naciskając klawisz **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b17cd-115">Execute the server application without debugging by pressing **Ctrl+F5**.</span></span>  
  
7.  <span data-ttu-id="b17cd-116">Otwórz wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b17cd-116">Open a Visual Studio command prompt.</span></span>  <span data-ttu-id="b17cd-117">Przejdź do katalogu klienta i wykonywania przez klienta z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b17cd-117">Navigate to the client directory and execute the client from the command line.</span></span>  
  
8.  <span data-ttu-id="b17cd-118">W Podglądzie zdarzeń Wyłącz i Odśwież dziennika analityczne i posortuj zdarzenia według identyfikatora zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b17cd-118">In Event Viewer, disable and refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="b17cd-119">Znajdź zdarzenie o identyfikatorze zdarzenia [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), która opisuje błąd usługi.</span><span class="sxs-lookup"><span data-stu-id="b17cd-119">Look for an event with Event ID [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), which describes the service failure.</span></span>  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b17cd-120">Zdarzenia są buforowane, gdy są wysyłane do podglądu zdarzeń; zdarzenia błędu nie może występować od razu.</span><span class="sxs-lookup"><span data-stu-id="b17cd-120">Events are buffered when being sent to the event viewer; the failure event may not appear right away.</span></span>
