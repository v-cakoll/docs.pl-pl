---
title: 'Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: c3c81e331eb3d8ee450ba0cac38e57976846ee63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352070"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="f0807-102">Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0807-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="f0807-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0807-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="f0807-104">W tym przykładzie `My.Application.Log.WriteEntry` pokazano, jak użyć metody do rejestrowania informacji śledzenia do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="f0807-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="f0807-105">Aby dodać i skonfigurować odbiornik dziennika plików</span><span class="sxs-lookup"><span data-stu-id="f0807-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="f0807-106">Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="f0807-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="f0807-107">\-lub -</span><span class="sxs-lookup"><span data-stu-id="f0807-107">\- or -</span></span>

     <span data-ttu-id="f0807-108">Jeśli nie ma pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="f0807-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="f0807-109">W menu **Projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="f0807-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="f0807-110">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="f0807-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="f0807-111">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="f0807-111">Click **Add**.</span></span>

2. <span data-ttu-id="f0807-112">Zlokalizuj sekcję `<listeners>` w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0807-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="f0807-113">\<Odsłuchaczy> sekcji w sekcji \<> źródłowej z atrybutem nazwa "DefaultSource", który jest \<zagnieżdżony w sekcji> system.diagnostics, \<która jest zagnieżdżona w sekcji> konfiguracji najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="f0807-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="f0807-114">Dodaj ten element `<listeners>` do tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="f0807-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="f0807-115">Znajdź `<sharedListeners>` sekcję `<system.diagnostics>` w sekcji zagnieżdżonej w sekcji najwyższego poziomu. `<configuration>`</span><span class="sxs-lookup"><span data-stu-id="f0807-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="f0807-116">Dodaj ten element `<sharedListeners>` do tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="f0807-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="f0807-117">Zmień wartość atrybutu na `customlocation` katalog dziennika.</span><span class="sxs-lookup"><span data-stu-id="f0807-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f0807-118">Aby ustawić wartość właściwości odbiornika, należy użyć atrybutu, który ma taką samą nazwę jak właściwość, ze wszystkimi literami w małych literach.</span><span class="sxs-lookup"><span data-stu-id="f0807-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="f0807-119">Na przykład `location` atrybuty i `customlocation` ustawić <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> wartości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> i właściwości.</span><span class="sxs-lookup"><span data-stu-id="f0807-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="f0807-120">Aby zapisać informacje o zdarzeniach w dzienniku plików</span><span class="sxs-lookup"><span data-stu-id="f0807-120">To write event information to the file log</span></span>

<span data-ttu-id="f0807-121">Użyj `My.Application.Log.WriteEntry` metody `My.Application.Log.WriteException` lub do zapisywania informacji w dzienniku plików.</span><span class="sxs-lookup"><span data-stu-id="f0807-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="f0807-122">Aby uzyskać więcej informacji, zobacz [Jak: Pisanie komunikatów dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [jak: Rejestrowanie wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="f0807-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="f0807-123">Po skonfigurowaniu odbiornika dziennika plików dla zestawu, odbiera `My.Application.Log` wszystkie komunikaty, które zapisuje z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f0807-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0807-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0807-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="f0807-125">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="f0807-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="f0807-126">Porady: wyjątki rejestru</span><span class="sxs-lookup"><span data-stu-id="f0807-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
