---
title: Zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: ab46f192f2e9549d0568737236742a366ce7b3a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="bbb40-102">Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbb40-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="bbb40-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbb40-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="bbb40-104">W tym przewodniku przedstawiono sposób zastępują ustawienia domyślne i spowodować `Log` obiektu do zapisania do innych odbiorniki dzienników.</span><span class="sxs-lookup"><span data-stu-id="bbb40-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bbb40-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bbb40-105">Prerequisites</span></span>  
 <span data-ttu-id="bbb40-106">`Log` Obiektu można zapisać informacji do kilku odbiorniki dzienników.</span><span class="sxs-lookup"><span data-stu-id="bbb40-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="bbb40-107">Musisz określić bieżącą konfigurację odbiorników dziennika przed zmianą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bbb40-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="bbb40-108">Aby uzyskać więcej informacji, zobacz [wskazówki: Ustalanie gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="bbb40-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="bbb40-109">Warto przejrzeć [porady: zapis informacji o zdarzeniu do pliku tekstowego](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) lub [jak: zapisu do dziennika zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="bbb40-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>  
  
### <a name="to-add-listeners"></a><span data-ttu-id="bbb40-110">Aby dodać obiekty nasłuchujące</span><span class="sxs-lookup"><span data-stu-id="bbb40-110">To add listeners</span></span>  
  
1.  <span data-ttu-id="bbb40-111">Kliknij prawym przyciskiem myszy app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="bbb40-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="bbb40-112">\- lub -</span><span class="sxs-lookup"><span data-stu-id="bbb40-112">\- or -</span></span>  
  
     <span data-ttu-id="bbb40-113">Jeśli plik app.config, nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="bbb40-113">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="bbb40-114">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="bbb40-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="bbb40-115">Z **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="bbb40-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="bbb40-116">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="bbb40-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="bbb40-117">Zlokalizuj `<listeners>` w obszarze `<source>` sekcji z `name` atrybutu "DefaultSource" w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="bbb40-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="bbb40-118">`<sources>` Znajduje się w sekcji `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="bbb40-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="bbb40-119">Dodaj te elementy w tym `<listeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="bbb40-119">Add these elements to that `<listeners>` section.</span></span>  
  
    ```xml  
    <!-- Uncomment to connect the application file log. -->  
    <!-- <add name="FileLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="EventLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="Delimited" /> -->  
    <!-- Uncomment to connect the XML log. -->  
    <!-- <add name="XmlWriter" /> -->  
    <!-- Uncomment to connect the console log. -->  
    <!-- <add name="Console" /> -->  
    ```  
  
4.  <span data-ttu-id="bbb40-120">Usuń znaczniki komentarza odbiorniki dzienników, które chcesz otrzymywać `Log` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bbb40-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>  
  
5.  <span data-ttu-id="bbb40-121">Zlokalizuj `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="bbb40-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="bbb40-122">Dodaj te elementy w tym `<sharedListeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="bbb40-122">Add these elements to that `<sharedListeners>` section.</span></span>  
  
    ```xml  
    <add name="FileLog"  
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
               Microsoft.VisualBasic, Version=8.0.0.0,   
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
         initializeData="FileLogWriter" />  
    <add name="EventLog"  
         type="System.Diagnostics.EventLogTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="sample application"/>  
    <add name="Delimited"   
         type="System.Diagnostics.DelimitedListTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleDelimitedFile.txt"  
         traceOutputOptions="DateTime" />  
    <add name="XmlWriter"  
         type="System.Diagnostics.XmlWriterTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleLogFile.xml" />  
    <add name="Console"  
         type="System.Diagnostics.ConsoleTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="true" />  
    ```  
  
7.  <span data-ttu-id="bbb40-123">Zawartość pliku app.config powinny być podobne do następującego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="bbb40-123">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Uncomment to connect the application file log. -->  
              <!-- <add name="FileLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="EventLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="Delimited" /> -->  
              <!-- Uncomment to connect the XML log. -->  
              <!-- <add name="XmlWriter" /> -->  
              <!-- Uncomment to connect the console log. -->  
              <!-- <add name="Console" /> -->  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
               initializeData="FileLogWriter" />  
          <add name="EventLog"  
               type="System.Diagnostics.EventLogTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="sample application"/>  
          <add name="Delimited"   
               type="System.Diagnostics.DelimitedListTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleDelimitedFile.txt"  
               traceOutputOptions="DateTime" />  
          <add name="XmlWriter"  
               type="System.Diagnostics.XmlWriterTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleLogFile.xml" />  
          <add name="Console"  
               type="System.Diagnostics.ConsoleTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="true" />  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="bbb40-124">Aby ponownie skonfigurować odbiornik</span><span class="sxs-lookup"><span data-stu-id="bbb40-124">To reconfigure a listener</span></span>  
  
1.  <span data-ttu-id="bbb40-125">Zlokalizuj odbiornika `<add>` element z `<sharedListeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="bbb40-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>  
  
2.  <span data-ttu-id="bbb40-126">`type` Atrybut nadaje nazwę typu odbiornika.</span><span class="sxs-lookup"><span data-stu-id="bbb40-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="bbb40-127">Ten typ musi dziedziczyć z <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="bbb40-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="bbb40-128">Aby upewnić się, że jest używany nieprawidłowy typ, użyj nazwy typu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="bbb40-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="bbb40-129">Aby uzyskać więcej informacji zobacz "Aby odwoływać się do typu o silnej nazwie" sekcji poniżej.</span><span class="sxs-lookup"><span data-stu-id="bbb40-129">For more information, see the "To reference a strongly named type" section below.</span></span>  
  
     <span data-ttu-id="bbb40-130">Niektóre typy, które są dostępne są:</span><span class="sxs-lookup"><span data-stu-id="bbb40-130">Some types that you can use are:</span></span>  
  
    -   <span data-ttu-id="bbb40-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="bbb40-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>  
  
    -   <span data-ttu-id="bbb40-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje informacje w dzienniku zdarzeń komputera określona przez `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="bbb40-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="bbb40-133"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników, które zapisać do pliku określonego w `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="bbb40-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="bbb40-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje do wiersza polecenia konsoli.</span><span class="sxs-lookup"><span data-stu-id="bbb40-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>  
  
     <span data-ttu-id="bbb40-135">Aby dowiedzieć się, w którym innych typów odbiorniki logu zapisywać informacje zapoznaj się dokumentacją tego typu.</span><span class="sxs-lookup"><span data-stu-id="bbb40-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
3.  <span data-ttu-id="bbb40-136">Gdy aplikacja tworzy obiekt dziennika odbiornika, przekazuje `initializeData` atrybut jako parametru konstruktora.</span><span class="sxs-lookup"><span data-stu-id="bbb40-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="bbb40-137">Znaczenie `initializeData` atrybutu jest zależny od obiektu nasłuchującego śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bbb40-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>  
  
4.  <span data-ttu-id="bbb40-138">Po utworzeniu odbiornika dziennika, aplikacja ustawia właściwości odbiornika.</span><span class="sxs-lookup"><span data-stu-id="bbb40-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="bbb40-139">Te właściwości są definiowane przez inne atrybuty w `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="bbb40-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="bbb40-140">Więcej informacji dotyczących właściwości dla określonego odbiornika w dokumentacji dla tego odbiornika typu.</span><span class="sxs-lookup"><span data-stu-id="bbb40-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>  
  
### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="bbb40-141">Aby odwołać się do typu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="bbb40-141">To reference a strongly named type</span></span>  
  
1.  <span data-ttu-id="bbb40-142">Aby upewnić się, że nieprawidłowy typ jest używany przez odbiornik sieci dziennika, upewnij się, że nazwa FQDN typu i nazwa zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="bbb40-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="bbb40-143">O silnej nazwie typu ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="bbb40-143">The syntax of a strongly named type is as follows:</span></span>  
  
     <span data-ttu-id="bbb40-144">\<*Nazwa typu*>, \< *nazwy zestawu*>, \< *numer wersji*>, \< *kultury*>, \< *silnej nazwy*></span><span class="sxs-lookup"><span data-stu-id="bbb40-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>  
  
2.  <span data-ttu-id="bbb40-145">Ten przykładowy kod przedstawia sposób określić nazwę typu o silnej nazwie FQDN type—"System.Diagnostics.FileLogTraceListener" w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="bbb40-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     <span data-ttu-id="bbb40-146">Jest to dane wyjściowe, i może służyć do unikatowego odwoływać się do typu o silnej nazwie, jak procedury "Aby dodać odbiorników" powyżej.</span><span class="sxs-lookup"><span data-stu-id="bbb40-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a><span data-ttu-id="bbb40-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbb40-147">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>  
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>  
 [<span data-ttu-id="bbb40-148">Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym</span><span class="sxs-lookup"><span data-stu-id="bbb40-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)  
 [<span data-ttu-id="bbb40-149">Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="bbb40-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
