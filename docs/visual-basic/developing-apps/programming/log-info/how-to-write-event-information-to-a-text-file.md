---
title: 'Instrukcje: Zapisywanie informacji zdarzeniach w pliku tekstowym (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: e696ccb7327197c2f3a2468d30085dc6d390e034
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312721"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="fb5f6-102">Instrukcje: Zapisywanie informacji zdarzeniach w pliku tekstowym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb5f6-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="fb5f6-103">Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="fb5f6-104">W tym przykładzie pokazano, jak używać `My.Application.Log.WriteEntry` metodę, aby rejestrować informacje śledzenia do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="fb5f6-105">Aby dodać i skonfigurować odbiornika dziennika plików</span><span class="sxs-lookup"><span data-stu-id="fb5f6-105">To add and configure the file log listener</span></span>  
  
1. <span data-ttu-id="fb5f6-106">Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="fb5f6-107">\- lub —</span><span class="sxs-lookup"><span data-stu-id="fb5f6-107">\- or -</span></span>  
  
     <span data-ttu-id="fb5f6-108">Jeśli nie ma żadnego pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="fb5f6-108">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="fb5f6-109">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="fb5f6-110">Z **Dodaj nowy element** okna dialogowego wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="fb5f6-111">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-111">Click **Add**.</span></span>  
  
2. <span data-ttu-id="fb5f6-112">Znajdź `<listeners>` sekcji w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="fb5f6-113">Znajdziesz \<odbiorników > sekcji \<źródło > sekcji atrybut name "DefaultSource", który jest zagnieżdżony w \<system.diagnostics > sekcji, która jest zagnieżdżony w najwyższegopoziomu\<konfiguracji > sekcji.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3. <span data-ttu-id="fb5f6-114">Dodaj ten element, do którego `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="fb5f6-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4. <span data-ttu-id="fb5f6-115">Znajdź `<sharedListeners>` sekcji `<system.diagnostics>` sekcji zagnieżdżone najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5. <span data-ttu-id="fb5f6-116">Dodaj ten element, do którego `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="fb5f6-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="fb5f6-117">Zmień wartość właściwości `customlocation` atrybutu do katalogu dziennika.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb5f6-118">Aby ustawić wartość właściwości odbiornika, użyj atrybutu, który ma taką samą nazwę jak właściwości, za pomocą wszystkie znaki w małą nazwie.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="fb5f6-119">Na przykład `location` i `customlocation` atrybuty ustawione wartości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> i <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="fb5f6-120">Można zapisać informacji o zdarzeniach do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="fb5f6-120">To write event information to the file log</span></span>  
  
-   <span data-ttu-id="fb5f6-121">Użyj `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` metody, aby zapisać informacje o dzienniku plików.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="fb5f6-122">Aby uzyskać więcej informacji, zobacz [jak: Zapisywanie wiadomości rejestru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [jak: Rejestrowania wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="fb5f6-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="fb5f6-123">Po skonfigurowaniu odbiornika plik dziennika dla zestawu, odbiera wszystkie komunikaty powodujące `My.Application.Log` zapisuje z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="fb5f6-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb5f6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb5f6-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="fb5f6-125">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="fb5f6-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="fb5f6-126">Instrukcje: rejestrowanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="fb5f6-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
