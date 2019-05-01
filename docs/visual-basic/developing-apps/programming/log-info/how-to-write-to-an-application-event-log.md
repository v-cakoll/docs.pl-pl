---
title: 'Instrukcje: Zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: c3c7d350132ee6c891633141fc5c4b280989e77f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934358"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="ce98d-102">Instrukcje: Zapisywanie w rejestrze zdarzeń aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce98d-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="ce98d-103">Możesz użyć `My.Application.Log` i `My.Log` obiektów można zapisać informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce98d-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="ce98d-104">W tym przykładzie pokazano, jak Konfigurowanie odbiornika dziennika zdarzeń tak `My.Application.Log` zapisuje informacje śledzenia do dziennika zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce98d-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="ce98d-105">Nie można zapisać w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ce98d-105">You cannot write to the Security log.</span></span> <span data-ttu-id="ce98d-106">Aby można było zapisać w dzienniku systemu, musi być członkiem konta systemu lokalnego lub administratora.</span><span class="sxs-lookup"><span data-stu-id="ce98d-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="ce98d-107">Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podgląd zdarzeń Windows**.</span><span class="sxs-lookup"><span data-stu-id="ce98d-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="ce98d-108">Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="ce98d-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

### <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="ce98d-109">Aby dodać i skonfigurować odbiornika dziennika zdarzeń</span><span class="sxs-lookup"><span data-stu-id="ce98d-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="ce98d-110">Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="ce98d-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="ce98d-111">\- lub —</span><span class="sxs-lookup"><span data-stu-id="ce98d-111">\- or -</span></span>

    <span data-ttu-id="ce98d-112">Jeśli nie ma żadnego pliku app.config</span><span class="sxs-lookup"><span data-stu-id="ce98d-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="ce98d-113">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="ce98d-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="ce98d-114">Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="ce98d-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="ce98d-115">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ce98d-115">Click **Add**.</span></span>

2. <span data-ttu-id="ce98d-116">Znajdź `<listeners>` sekcji w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce98d-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="ce98d-117">Znajdziesz `<listeners>` sekcji `<source>` sekcję atrybut name "DefaultSource", który jest zagnieżdżony w `<system.diagnostics>` sekcję, co jest zagnieżdżony w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="ce98d-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="ce98d-118">Dodaj ten element, do którego `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="ce98d-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="ce98d-119">Znajdź `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="ce98d-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="ce98d-120">Dodaj ten element, do którego `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="ce98d-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="ce98d-121">Zastąp `APPLICATION_NAME` z nazwą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce98d-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ce98d-122">Zazwyczaj aplikacja zapisuje tylko błędy w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ce98d-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="ce98d-123">Więcej informacji o filtrowaniu dane wyjściowe dziennika, zobacz [instruktażu: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="ce98d-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

### <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="ce98d-124">Aby zapisać informacje o zdarzeniach w dzienniku zdarzeń</span><span class="sxs-lookup"><span data-stu-id="ce98d-124">To write event information to the event log</span></span>

- <span data-ttu-id="ce98d-125">Użyj `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` metodę, aby zapisywać informacje w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ce98d-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="ce98d-126">Aby uzyskać więcej informacji, zobacz [jak: Zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [jak: Rejestrowania wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="ce98d-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

    <span data-ttu-id="ce98d-127">Po skonfigurowaniu odbiornika dziennika zdarzeń dla zestawu, odbiera wszystkie komunikaty powodujące `My.Application.Log` zapisuje z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce98d-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce98d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce98d-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="ce98d-129">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="ce98d-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="ce98d-130">Instrukcje: Rejestruje wyjątki</span><span class="sxs-lookup"><span data-stu-id="ce98d-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="ce98d-131">Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="ce98d-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
