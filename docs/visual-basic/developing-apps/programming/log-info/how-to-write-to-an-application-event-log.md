---
title: 'Porady: zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: a62e1e8f6112a96935ce165e42d34c57b223cd95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590689"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="54e67-102">Porady: zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54e67-102">How to: Write to an Application Event Log (Visual Basic)</span></span>
<span data-ttu-id="54e67-103">Można użyć `My.Application.Log` i `My.Log` obiektów można zapisać informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="54e67-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="54e67-104">W tym przykładzie pokazano, jak skonfigurować odbiornik dziennika zdarzeń tak `My.Application.Log` zapisuje informacje śledzenia w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="54e67-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>  
  
 <span data-ttu-id="54e67-105">Nie można zapisać dziennika zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="54e67-105">You cannot write to the Security log.</span></span> <span data-ttu-id="54e67-106">W celu zapisu do dziennika systemu, użytkownik musi należeć do konta systemu lokalnego lub administratora.</span><span class="sxs-lookup"><span data-stu-id="54e67-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>  
  
 <span data-ttu-id="54e67-107">Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podgląd zdarzeń systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="54e67-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="54e67-108">Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="54e67-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54e67-109">Dzienniki zdarzeń nie są obsługiwane w systemie Windows 95, Windows 98 lub Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="54e67-109">Event logs are not supported on Windows 95, Windows 98, or Windows Millennium Edition.</span></span>  
  
### <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="54e67-110">Aby dodać i skonfigurować odbiornik dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="54e67-110">To add and configure the event log listener</span></span>  
  
1.  <span data-ttu-id="54e67-111">Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="54e67-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="54e67-112">\- lub -</span><span class="sxs-lookup"><span data-stu-id="54e67-112">\- or -</span></span>  
  
     <span data-ttu-id="54e67-113">Jeśli plik app.config, nie istnieje</span><span class="sxs-lookup"><span data-stu-id="54e67-113">If there is no app.config file,</span></span>  
  
    1.  <span data-ttu-id="54e67-114">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="54e67-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="54e67-115">Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="54e67-115">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="54e67-116">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="54e67-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="54e67-117">Zlokalizuj `<listeners>` sekcji w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="54e67-117">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="54e67-118">Można znaleźć `<listeners>` sekcji `<source>` sekcji o atrybut name "DefaultSource", która jest zagnieżdżona w obszarze `<system.diagnostics>` sekcję, co jest zagnieżdżony najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="54e67-118">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="54e67-119">Dodaj ten element, do którego `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="54e67-119">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="EventLog"/>  
    ```  
  
4.  <span data-ttu-id="54e67-120">Zlokalizuj `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="54e67-120">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="54e67-121">Dodaj ten element, do którego `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="54e67-121">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     <span data-ttu-id="54e67-122">Zastąp `APPLICATION_NAME` z nazwą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="54e67-122">Replace `APPLICATION_NAME` with the name of your application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54e67-123">Zwykle aplikacja zapisuje tylko błędy w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="54e67-123">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="54e67-124">Więcej informacji o filtrowaniu wpisu w dzienniku, zobacz [wskazówki: filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="54e67-124">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
### <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="54e67-125">Aby zapisać informacje dotyczące zdarzenia w dzienniku zdarzeń</span><span class="sxs-lookup"><span data-stu-id="54e67-125">To write event information to the event log</span></span>  
  
-   <span data-ttu-id="54e67-126">Użyj `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` metody, aby zapisać informacje w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="54e67-126">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="54e67-127">Aby uzyskać więcej informacji, zobacz [jak: zapisu komunikaty dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [porady: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="54e67-127">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="54e67-128">Po skonfigurowaniu odbiornika dziennika zdarzeń dla zestawu odbiera wszystkie wiadomości, które `My.Applcation.Log` zapisuje z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="54e67-128">After you configure the event log listener for an assembly, it receives all messages that `My.Applcation.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e67-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54e67-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="54e67-130">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="54e67-130">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="54e67-131">Instrukcje: wyjątki dziennika</span><span class="sxs-lookup"><span data-stu-id="54e67-131">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="54e67-132">Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="54e67-132">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
