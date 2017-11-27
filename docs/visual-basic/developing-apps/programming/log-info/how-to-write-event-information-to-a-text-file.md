---
title: 'Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 944d874de5c3872f9efe5e287e5354c94c792b95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="2ee99-102">Porady: zapisywanie informacji o zdarzeniach w pliku tekstowym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ee99-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="2ee99-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2ee99-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="2ee99-104">Ten przykład przedstawia sposób użycia `My.Application.Log.WriteEntry` metody do rejestrowania informacji śledzenia w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="2ee99-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="2ee99-105">Aby dodać i skonfigurować odbiornik pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="2ee99-105">To add and configure the file log listener</span></span>  
  
1.  <span data-ttu-id="2ee99-106">Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="2ee99-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="2ee99-107">\-lub -</span><span class="sxs-lookup"><span data-stu-id="2ee99-107">\- or -</span></span>  
  
     <span data-ttu-id="2ee99-108">Jeśli plik app.config, nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="2ee99-108">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="2ee99-109">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="2ee99-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="2ee99-110">Z **Dodaj nowy element** oknie dialogowym wybierz **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="2ee99-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="2ee99-111">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="2ee99-111">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="2ee99-112">Zlokalizuj `<listeners>` sekcji w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2ee99-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="2ee99-113">Można znaleźć \<odbiorników > w sekcji \<źródło > sekcji, atrybut name "DefaultSource", która jest zagnieżdżona w obszarze \<system.diagnostics > sekcji, która jest zagnieżdżona w obszarze najwyższegopoziomu\<konfiguracji > sekcji.</span><span class="sxs-lookup"><span data-stu-id="2ee99-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3.  <span data-ttu-id="2ee99-114">Dodaj ten element, do którego `<listeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="2ee99-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4.  <span data-ttu-id="2ee99-115">Zlokalizuj `<sharedListeners>` sekcji `<system.diagnostics>` sekcji zagnieżdżone najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="2ee99-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="2ee99-116">Dodaj ten element, do którego `<sharedListeners>` sekcji:</span><span class="sxs-lookup"><span data-stu-id="2ee99-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="2ee99-117">Zmień wartość `customlocation` atrybutu do katalogu dziennika.</span><span class="sxs-lookup"><span data-stu-id="2ee99-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ee99-118">Aby ustawić wartość właściwości odbiornika, użyj atrybut, który ma taką samą nazwę jak właściwości, w których wszystkie litery w małych nazwy.</span><span class="sxs-lookup"><span data-stu-id="2ee99-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="2ee99-119">Na przykład `location` i `customlocation` atrybuty ustawione wartości <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> i <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ee99-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="2ee99-120">Można zapisać informacji o zdarzeniach w pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="2ee99-120">To write event information to the file log</span></span>  
  
-   <span data-ttu-id="2ee99-121">Użyj `My.Application.Log.WriteEntry` lub `My.Application.Log.WriteException` metody, aby zapisać informacje o pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="2ee99-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="2ee99-122">Aby uzyskać więcej informacji, zobacz [jak: zapisu komunikaty dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) i [porady: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="2ee99-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="2ee99-123">Po skonfigurowaniu odbiornika plik dziennika dla zestawu odbiera wszystkie wiadomości, które `My.Application.Log` zapisuje z tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2ee99-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee99-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ee99-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="2ee99-125">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="2ee99-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="2ee99-126">Porady: wyjątki rejestru</span><span class="sxs-lookup"><span data-stu-id="2ee99-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
