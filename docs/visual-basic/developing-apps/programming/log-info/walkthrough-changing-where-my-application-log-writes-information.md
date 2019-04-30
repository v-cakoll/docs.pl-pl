---
title: Zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: 56fef77448f3523732e755f57e8cdabe6ad71379
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755301"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="5c88c-102">Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c88c-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="5c88c-103">Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c88c-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="5c88c-104">W tym instruktażu przedstawiono sposób zastępują ustawienia domyślne i spowodować, że `Log` obiektu do zapisania do innych nasłuchujących dziennika.</span><span class="sxs-lookup"><span data-stu-id="5c88c-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5c88c-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5c88c-105">Prerequisites</span></span>  
 <span data-ttu-id="5c88c-106">`Log` Obiektu można zapisać informacji do kilku odbiorniki logu.</span><span class="sxs-lookup"><span data-stu-id="5c88c-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="5c88c-107">Należy określić bieżącą konfigurację odbiorniki logu przed zmianą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5c88c-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="5c88c-108">Aby uzyskać więcej informacji, zobacz [instruktażu: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="5c88c-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="5c88c-109">Warto przejrzeć [jak: Zapisywanie informacji o pliku tekstowego zdarzeniach](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) lub [jak: Zapisywanie w rejestrze zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="5c88c-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>  
  
### <a name="to-add-listeners"></a><span data-ttu-id="5c88c-110">Aby dodać obiekty nasłuchujące</span><span class="sxs-lookup"><span data-stu-id="5c88c-110">To add listeners</span></span>  
  
1. <span data-ttu-id="5c88c-111">Kliknij prawym przyciskiem myszy pliku app.config w **Eksploratora rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="5c88c-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="5c88c-112">\- lub —</span><span class="sxs-lookup"><span data-stu-id="5c88c-112">\- or -</span></span>  
  
     <span data-ttu-id="5c88c-113">Jeśli nie ma żadnego pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="5c88c-113">If there is no app.config file:</span></span>  
  
    1. <span data-ttu-id="5c88c-114">Na **projektu** menu, wybierz **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="5c88c-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="5c88c-115">Z **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="5c88c-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="5c88c-116">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="5c88c-116">Click **Add**.</span></span>  
  
2. <span data-ttu-id="5c88c-117">Znajdź `<listeners>` sekcji w obszarze `<source>` sekcji z `name` atrybutu "DefaultSource" w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="5c88c-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="5c88c-118">`<sources>` Znajduje się w sekcji `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="5c88c-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3. <span data-ttu-id="5c88c-119">Dodaj te elementy, `<listeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="5c88c-119">Add these elements to that `<listeners>` section.</span></span>  
  
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
  
4. <span data-ttu-id="5c88c-120">Usuń znaczniki komentarza odbiorniki logu, które chcesz otrzymywać `Log` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5c88c-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>  
  
5. <span data-ttu-id="5c88c-121">Znajdź `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="5c88c-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6. <span data-ttu-id="5c88c-122">Dodaj te elementy, `<sharedListeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="5c88c-122">Add these elements to that `<sharedListeners>` section.</span></span>  
  
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
  
7. <span data-ttu-id="5c88c-123">Zawartość pliku app.config powinien wyglądać podobnie jak następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="5c88c-123">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="5c88c-124">Aby zmienić konfigurację odbiornika</span><span class="sxs-lookup"><span data-stu-id="5c88c-124">To reconfigure a listener</span></span>  
  
1. <span data-ttu-id="5c88c-125">Znajdź odbiornika `<add>` elementu z `<sharedListeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="5c88c-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>  
  
2. <span data-ttu-id="5c88c-126">`type` Atrybut zawiera nazwę typu odbiornika.</span><span class="sxs-lookup"><span data-stu-id="5c88c-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="5c88c-127">Ten typ musi dziedziczyć <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="5c88c-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="5c88c-128">Aby upewnić się, że właściwego typu jest używany, należy użyć nazwy o silnej nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="5c88c-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="5c88c-129">Aby uzyskać więcej informacji zobacz "Aby odwołać się do typu o silnej nazwie" sekcji poniżej.</span><span class="sxs-lookup"><span data-stu-id="5c88c-129">For more information, see the "To reference a strongly named type" section below.</span></span>  
  
     <span data-ttu-id="5c88c-130">Niektóre typy, które są dostępne są:</span><span class="sxs-lookup"><span data-stu-id="5c88c-130">Some types that you can use are:</span></span>  
  
    - <span data-ttu-id="5c88c-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje je do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="5c88c-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>  
  
    - <span data-ttu-id="5c88c-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje informacje w dzienniku zdarzeń komputera, które są określone przez `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="5c88c-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>  
  
    - <span data-ttu-id="5c88c-133"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników, które zapis do pliku określonego w `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="5c88c-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>  
  
    - <span data-ttu-id="5c88c-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> odbiornika, który zapisuje je w wiersza polecenia konsoli.</span><span class="sxs-lookup"><span data-stu-id="5c88c-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>  
  
     <span data-ttu-id="5c88c-135">Uzyskać informacji o tym, gdzie innych rodzajów odbiorniki logu wpisać informacje zapoznaj się dokumentacją tego typu.</span><span class="sxs-lookup"><span data-stu-id="5c88c-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
3. <span data-ttu-id="5c88c-136">Gdy aplikacja tworzy obiekt odbiornika dziennika, przekazuje on `initializeData` atrybutu jako parametr konstruktora.</span><span class="sxs-lookup"><span data-stu-id="5c88c-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="5c88c-137">Znaczenie `initializeData` atrybutu jest zależna od odbiornika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5c88c-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>  
  
4. <span data-ttu-id="5c88c-138">Po utworzeniu odbiornika dziennika, aplikacja ustawia właściwości odbiornika.</span><span class="sxs-lookup"><span data-stu-id="5c88c-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="5c88c-139">Te właściwości są definiowane przez inne atrybuty `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="5c88c-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="5c88c-140">Aby uzyskać więcej informacji na właściwości określonego odbiornika zobacz dokumentację dla tego odbiornika typu.</span><span class="sxs-lookup"><span data-stu-id="5c88c-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>  
  
### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="5c88c-141">Aby odwołać się do typu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="5c88c-141">To reference a strongly named type</span></span>  
  
1. <span data-ttu-id="5c88c-142">Aby upewnić się, że właściwego typu jest używany do z odbiornikiem dziennika, upewnij się użyć w pełni kwalifikowana nazwa typu i nazwy zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="5c88c-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="5c88c-143">Składnia typu o silnej nazwie jest w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5c88c-143">The syntax of a strongly named type is as follows:</span></span>  
  
     <span data-ttu-id="5c88c-144">\<*Nazwa typu*>, \< *nazwy zestawu*>, \< *numer wersji*>, \< *kultury*>, \< *silnej nazwy*></span><span class="sxs-lookup"><span data-stu-id="5c88c-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>  
  
2. <span data-ttu-id="5c88c-145">Ten przykład kodu pokazuje, jak można ustalić nazwy typu o silnej nazwie do w pełni kwalifikowaną type—"System.Diagnostics.FileLogTraceListener" w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="5c88c-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]  
  
     <span data-ttu-id="5c88c-146">Jest to dane wyjściowe i może służyć do unikatowego odwołać się do typu o silnej nazwie, jak procedury "Aby dodać obiekty nasłuchujące" powyżej.</span><span class="sxs-lookup"><span data-stu-id="5c88c-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a><span data-ttu-id="5c88c-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c88c-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="5c88c-148">Instrukcje: Zapisywanie informacji zdarzeniach w pliku tekstowym</span><span class="sxs-lookup"><span data-stu-id="5c88c-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="5c88c-149">Instrukcje: Zapisywanie w rejestrze zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="5c88c-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
