---
title: 'Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 511bb8fb16851872c1a16ae7627ed0fc6594337c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352047"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="9f961-102">Porady: zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f961-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="9f961-103">Za pomocą obiektów `My.Application.Log` i `My.Log` można pisać informacje o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f961-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="9f961-104">Ten przykład pokazuje, jak skonfigurować odbiornik dziennika zdarzeń, co `My.Application.Log` spowoduje zapisanie informacji o śledzeniu w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f961-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="9f961-105">Nie można zapisać w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9f961-105">You cannot write to the Security log.</span></span> <span data-ttu-id="9f961-106">Aby można było zapisywać dane w dzienniku systemu, musisz być członkiem konta LocalSystem lub administratora.</span><span class="sxs-lookup"><span data-stu-id="9f961-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="9f961-107">Aby wyświetlić dziennik zdarzeń, można użyć **Eksplorator serwera** lub **Podgląd zdarzeń systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="9f961-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="9f961-108">Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="9f961-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="9f961-109">Aby dodać i skonfigurować odbiornik dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="9f961-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="9f961-110">Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="9f961-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="9f961-111">\-oraz</span><span class="sxs-lookup"><span data-stu-id="9f961-111">\- or -</span></span>

    <span data-ttu-id="9f961-112">Jeśli nie ma pliku App. config,</span><span class="sxs-lookup"><span data-stu-id="9f961-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="9f961-113">W menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9f961-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="9f961-114">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="9f961-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="9f961-115">Kliknij pozycję **Add** (Dodaj).</span><span class="sxs-lookup"><span data-stu-id="9f961-115">Click **Add**.</span></span>

2. <span data-ttu-id="9f961-116">Znajdź `<listeners>` sekcję w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f961-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="9f961-117">`<listeners>` Sekcja `<source>` w sekcji ma atrybut name "DefaultSource", który jest zagnieżdżony w `<system.diagnostics>` sekcji, która jest zagnieżdżona w sekcji najwyższego poziomu `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="9f961-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="9f961-118">Dodaj ten element do tej `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="9f961-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="9f961-119">Znajdź `<sharedListeners>` sekcję `<system.diagnostics>` w sekcji, w sekcji najwyższego poziomu `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="9f961-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="9f961-120">Dodaj ten element do tej `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="9f961-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="9f961-121">Zamień `APPLICATION_NAME` na nazwę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f961-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9f961-122">Zazwyczaj aplikacja zapisuje tylko błędy w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9f961-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="9f961-123">Aby uzyskać informacje o filtrowaniu danych wyjściowych dziennika, zobacz [Przewodnik: filtrowanie danych wyjściowych my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="9f961-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="9f961-124">Aby zapisać informacje o zdarzeniach w dzienniku zdarzeń</span><span class="sxs-lookup"><span data-stu-id="9f961-124">To write event information to the event log</span></span>

<span data-ttu-id="9f961-125">Użyj metody `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` , aby zapisać informacje w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9f961-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="9f961-126">Aby uzyskać więcej informacji, zobacz [How to: Write log messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="9f961-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="9f961-127">Po skonfigurowaniu odbiornika dziennika zdarzeń dla zestawu otrzymuje on wszystkie komunikaty, które `My.Application.Log` zapisują z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9f961-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f961-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f961-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="9f961-129">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="9f961-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="9f961-130">Instrukcje: rejestrowanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="9f961-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="9f961-131">Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="9f961-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
