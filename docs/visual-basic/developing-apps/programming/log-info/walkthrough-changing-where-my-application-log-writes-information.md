---
title: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: f9e45cdf4507840f62e32678f4c0a7be2c0be054
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398295"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="9ce55-102">Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ce55-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="9ce55-103">Za pomocą `My.Application.Log` obiektów i można `My.Log` rejestrować informacje o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9ce55-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="9ce55-104">W tym instruktażu pokazano, jak zastąpić ustawienia domyślne i spowodować, że `Log` obiekt ma być zapisany w innych detektorach dzienników.</span><span class="sxs-lookup"><span data-stu-id="9ce55-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ce55-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9ce55-105">Prerequisites</span></span>

<span data-ttu-id="9ce55-106">`Log`Obiekt może zapisywać informacje w kilku detektorach dzienników.</span><span class="sxs-lookup"><span data-stu-id="9ce55-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="9ce55-107">Przed zmianą konfiguracji należy określić bieżącą konfigurację odbiorników dziennika.</span><span class="sxs-lookup"><span data-stu-id="9ce55-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="9ce55-108">Aby uzyskać więcej informacji, zobacz [Przewodnik: Określanie, gdzie my. Application. Log zapisuje informacje](walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="9ce55-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

<span data-ttu-id="9ce55-109">Warto zapoznać się z [tematem: zapisywanie informacji o zdarzeniach w pliku tekstowym](how-to-write-event-information-to-a-text-file.md) lub [instrukcje: zapisywanie w dzienniku zdarzeń aplikacji](how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="9ce55-109">You may want to review [How to: Write Event Information to a Text File](how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](how-to-write-to-an-application-event-log.md).</span></span>

### <a name="to-add-listeners"></a><span data-ttu-id="9ce55-110">Aby dodać detektory</span><span class="sxs-lookup"><span data-stu-id="9ce55-110">To add listeners</span></span>

1. <span data-ttu-id="9ce55-111">Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="9ce55-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="9ce55-112">\-oraz</span><span class="sxs-lookup"><span data-stu-id="9ce55-112">\- or -</span></span>

     <span data-ttu-id="9ce55-113">Jeśli nie ma pliku App. config:</span><span class="sxs-lookup"><span data-stu-id="9ce55-113">If there is no app.config file:</span></span>

    1. <span data-ttu-id="9ce55-114">W menu **projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="9ce55-114">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="9ce55-115">W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik konfiguracji aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="9ce55-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>

    3. <span data-ttu-id="9ce55-116">Kliknij pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="9ce55-116">Click **Add**.</span></span>

2. <span data-ttu-id="9ce55-117">Znajdź sekcję w sekcji `<listeners>` `<source>` z `name` atrybutem "DefaultSource" w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="9ce55-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="9ce55-118">`<sources>`Sekcja znajduje się w sekcji `<system.diagnostics>` najwyższego poziomu `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="9ce55-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="9ce55-119">Dodaj te elementy do tej `<listeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="9ce55-119">Add these elements to that `<listeners>` section.</span></span>

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

4. <span data-ttu-id="9ce55-120">Usuń znaczniki komentarza z odbiorników dziennika, dla których chcesz otrzymywać `Log` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9ce55-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>

5. <span data-ttu-id="9ce55-121">Znajdź sekcję w sekcji `<sharedListeners>` `<system.diagnostics>` , w sekcji najwyższego poziomu `<configuration>` .</span><span class="sxs-lookup"><span data-stu-id="9ce55-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="9ce55-122">Dodaj te elementy do tej `<sharedListeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="9ce55-122">Add these elements to that `<sharedListeners>` section.</span></span>

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

7. <span data-ttu-id="9ce55-123">Zawartość pliku App. config powinna wyglądać podobnie do następującego kodu XML:</span><span class="sxs-lookup"><span data-stu-id="9ce55-123">The content of the app.config file should be similar to the following XML:</span></span>

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

### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="9ce55-124">Aby zmienić konfigurację odbiornika</span><span class="sxs-lookup"><span data-stu-id="9ce55-124">To reconfigure a listener</span></span>

1. <span data-ttu-id="9ce55-125">Znajdź `<add>` element odbiornika z `<sharedListeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="9ce55-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>

2. <span data-ttu-id="9ce55-126">`type`Atrybut zawiera nazwę typu odbiornika.</span><span class="sxs-lookup"><span data-stu-id="9ce55-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="9ce55-127">Ten typ musi dziedziczyć po <xref:System.Diagnostics.TraceListener> klasie.</span><span class="sxs-lookup"><span data-stu-id="9ce55-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="9ce55-128">Użyj silnie nazwanego typu, aby upewnić się, że jest używany właściwy typ.</span><span class="sxs-lookup"><span data-stu-id="9ce55-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="9ce55-129">Aby uzyskać więcej informacji, zobacz sekcję "Aby odwołać się do silnie nazwanego typu" poniżej.</span><span class="sxs-lookup"><span data-stu-id="9ce55-129">For more information, see the "To reference a strongly named type" section below.</span></span>

     <span data-ttu-id="9ce55-130">Niektóre typy, których można użyć, to:</span><span class="sxs-lookup"><span data-stu-id="9ce55-130">Some types that you can use are:</span></span>

    - <span data-ttu-id="9ce55-131"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>Odbiornik, który zapisuje dane w dzienniku plików.</span><span class="sxs-lookup"><span data-stu-id="9ce55-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>

    - <span data-ttu-id="9ce55-132"><xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>Odbiornik, który zapisuje informacje do dziennika zdarzeń komputera określonego przez `initializeData` parametr.</span><span class="sxs-lookup"><span data-stu-id="9ce55-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>

    - <span data-ttu-id="9ce55-133"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> Detektory i, które zapisują w pliku określonym w `initializeData` parametrze.</span><span class="sxs-lookup"><span data-stu-id="9ce55-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="9ce55-134"><xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>Odbiornik, który zapisuje dane w konsoli wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9ce55-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>

     <span data-ttu-id="9ce55-135">Aby uzyskać informacje o tym, gdzie inne typy odbiorników dzienników zapisują informacje, zapoznaj się z dokumentacją tego typu.</span><span class="sxs-lookup"><span data-stu-id="9ce55-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

3. <span data-ttu-id="9ce55-136">Gdy aplikacja tworzy obiekt odbiornika log, przekazuje `initializeData` atrybut jako parametr konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9ce55-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="9ce55-137">Znaczenie `initializeData` atrybutu zależy od odbiornika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9ce55-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>

4. <span data-ttu-id="9ce55-138">Po utworzeniu odbiornika dziennika aplikacja ustawia właściwości odbiornika.</span><span class="sxs-lookup"><span data-stu-id="9ce55-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="9ce55-139">Te właściwości są definiowane przez inne atrybuty w `<add>` elemencie.</span><span class="sxs-lookup"><span data-stu-id="9ce55-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="9ce55-140">Aby uzyskać więcej informacji na temat właściwości określonego odbiornika, zapoznaj się z dokumentacją typu tego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="9ce55-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>

### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="9ce55-141">Aby odwołać się do silnie nazwanego typu</span><span class="sxs-lookup"><span data-stu-id="9ce55-141">To reference a strongly named type</span></span>

1. <span data-ttu-id="9ce55-142">Aby upewnić się, że odpowiedni typ jest używany dla odbiornika dzienników, upewnij się, że używasz w pełni kwalifikowanej nazwy typu i silnie nazwanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9ce55-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="9ce55-143">Składnia silnie nazwanego typu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="9ce55-143">The syntax of a strongly named type is as follows:</span></span>

     <span data-ttu-id="9ce55-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span><span class="sxs-lookup"><span data-stu-id="9ce55-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>

2. <span data-ttu-id="9ce55-145">Ten przykład kodu pokazuje, jak w tym przypadku określić silnie nazwanego typu dla w pełni kwalifikowanego typu — "System. Diagnostics. FileLogTraceListener".</span><span class="sxs-lookup"><span data-stu-id="9ce55-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     <span data-ttu-id="9ce55-146">Jest to dane wyjściowe i mogą być używane do unikatowego odwoływania się do silnie nazwanego typu, tak jak w powyższej procedurze "Dodaj odbiorniki".</span><span class="sxs-lookup"><span data-stu-id="9ce55-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a><span data-ttu-id="9ce55-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ce55-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="9ce55-148">Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym</span><span class="sxs-lookup"><span data-stu-id="9ce55-148">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="9ce55-149">Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="9ce55-149">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)
