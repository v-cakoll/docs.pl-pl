---
title: 'Instrukcje: Zapisz informacje o zdarzeniu w pliku tekstowym (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 4a34b57eb0a22dcf206456775cdd5817431292e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956825"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="b889d-102">Instrukcje: Zapisz informacje o zdarzeniu w pliku tekstowym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b889d-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="b889d-103">Za pomocą `My.Application.Log` obiektów i `My.Log` można rejestrować informacje o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b889d-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="b889d-104">Ten przykład pokazuje, `My.Application.Log.WriteEntry` jak używać metody do rejestrowania informacji o śledzeniu w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="b889d-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="b889d-105">Aby dodać i skonfigurować odbiornik dziennika plików</span><span class="sxs-lookup"><span data-stu-id="b889d-105">To add and configure the file log listener</span></span>  
  
1. <span data-ttu-id="b889d-106">Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="b889d-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="b889d-107">\- lub —</span><span class="sxs-lookup"><span data-stu-id="b889d-107">\- or -</span></span>  
  
     <span data-ttu-id="b889d-108">Jeśli nie ma pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="b889d-108">If there is no app.config file:</span></span>  
  
    1. <span data-ttu-id="b889d-109">W menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="b889d-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="b889d-110">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="b889d-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="b889d-111">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="b889d-111">Click **Add**.</span></span>  
  
2. <span data-ttu-id="b889d-112">`<listeners>` Znajdź sekcję w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b889d-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="b889d-113">W sekcji > \< \<źródłowej znajdują się > detektory z atrybutem Name "DefaultSource", który jest zagnieżdżony w sekcji System. Diagnostics >, która jest zagnieżdżona w obszarze najwyższego poziomu \< \<sekcja > konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b889d-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3. <span data-ttu-id="b889d-114">Dodaj ten element do tej `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="b889d-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. <span data-ttu-id="b889d-115">Znajdź sekcję w sekcji zagnieżdżoną w sekcji najwyższego poziomu `<configuration>`. `<system.diagnostics>` `<sharedListeners>`</span><span class="sxs-lookup"><span data-stu-id="b889d-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5. <span data-ttu-id="b889d-116">Dodaj ten element do tej `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="b889d-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="b889d-117">Zmień wartość `customlocation` atrybutu na katalog dziennika.</span><span class="sxs-lookup"><span data-stu-id="b889d-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b889d-118">Aby ustawić wartość właściwości odbiornika, Użyj atrybutu, który ma taką samą nazwę jak właściwość, z wszystkimi literami w nazwie małymi literami.</span><span class="sxs-lookup"><span data-stu-id="b889d-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="b889d-119">Na przykład `location` atrybuty <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> i `customlocation` ustawiają wartości właściwości i. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A></span><span class="sxs-lookup"><span data-stu-id="b889d-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="b889d-120">Aby zapisać informacje o zdarzeniu w dzienniku plików</span><span class="sxs-lookup"><span data-stu-id="b889d-120">To write event information to the file log</span></span>  
  
- <span data-ttu-id="b889d-121">Użyj metody `My.Application.Log.WriteException` lub, aby zapisać informacje w dzienniku plików. `My.Application.Log.WriteEntry`</span><span class="sxs-lookup"><span data-stu-id="b889d-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="b889d-122">Aby uzyskać więcej informacji, zobacz [jak: Zapisuj komunikaty](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) dziennika i [instrukcje: Wyjątki](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)dzienników.</span><span class="sxs-lookup"><span data-stu-id="b889d-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="b889d-123">Po skonfigurowaniu odbiornika dziennika plików dla zestawu otrzymuje on wszystkie komunikaty, które `My.Application.Log` zapisują z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b889d-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b889d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b889d-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="b889d-125">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="b889d-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="b889d-126">Instrukcje: Wyjątki dziennika</span><span class="sxs-lookup"><span data-stu-id="b889d-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
