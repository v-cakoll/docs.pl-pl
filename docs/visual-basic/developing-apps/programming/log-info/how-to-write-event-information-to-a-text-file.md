---
title: 'Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 54169f1133ed4f77026c4332493a7b5f4532aec0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583284"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="20ed3-102">Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20ed3-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="20ed3-103">Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="20ed3-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="20ed3-104">W tym przykładzie pokazano, jak za pomocą metody `My.Application.Log.WriteEntry` rejestrować informacje o śledzeniu do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="20ed3-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="20ed3-105">Aby dodać i skonfigurować odbiornik dziennika plików</span><span class="sxs-lookup"><span data-stu-id="20ed3-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="20ed3-106">Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="20ed3-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="20ed3-107">\- lub-</span><span class="sxs-lookup"><span data-stu-id="20ed3-107">\- or -</span></span>

     <span data-ttu-id="20ed3-108">Jeśli nie ma pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="20ed3-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="20ed3-109">W menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="20ed3-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="20ed3-110">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="20ed3-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="20ed3-111">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="20ed3-111">Click **Add**.</span></span>

2. <span data-ttu-id="20ed3-112">Znajdź sekcję `<listeners>` w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="20ed3-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="20ed3-113">Sekcja \<listeners >a znajduje się w sekcji \<source > z atrybutem Name "DefaultSource", który jest zagnieżdżony w sekcji \<system. Diagnostics >, która jest zagnieżdżona w obszarze \<configuration najwyższego poziomu > Paragraf.</span><span class="sxs-lookup"><span data-stu-id="20ed3-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="20ed3-114">Dodaj ten element do `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="20ed3-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="20ed3-115">Znajdź sekcję `<sharedListeners>` w sekcji `<system.diagnostics>` zagnieżdżoną w sekcji `<configuration>` najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="20ed3-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="20ed3-116">Dodaj ten element do `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="20ed3-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="20ed3-117">Zmień wartość atrybutu `customlocation` na katalog dziennika.</span><span class="sxs-lookup"><span data-stu-id="20ed3-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="20ed3-118">Aby ustawić wartość właściwości odbiornika, Użyj atrybutu, który ma taką samą nazwę jak właściwość, z wszystkimi literami w nazwie małymi literami.</span><span class="sxs-lookup"><span data-stu-id="20ed3-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="20ed3-119">Na przykład atrybuty `location` i `customlocation` ustawiają wartości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> i <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="20ed3-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="20ed3-120">Aby zapisać informacje o zdarzeniu w dzienniku plików</span><span class="sxs-lookup"><span data-stu-id="20ed3-120">To write event information to the file log</span></span>

<span data-ttu-id="20ed3-121">Użyj metody `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` w celu zapisania informacji w dzienniku plików.</span><span class="sxs-lookup"><span data-stu-id="20ed3-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="20ed3-122">Aby uzyskać więcej informacji, zobacz [How to: Write log messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="20ed3-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="20ed3-123">Po skonfigurowaniu odbiornika dziennika plików dla zestawu otrzymuje on wszystkie komunikaty, które `My.Application.Log` zapisu z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="20ed3-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="20ed3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20ed3-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="20ed3-125">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="20ed3-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="20ed3-126">Instrukcje: wyjątki dziennika</span><span class="sxs-lookup"><span data-stu-id="20ed3-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
