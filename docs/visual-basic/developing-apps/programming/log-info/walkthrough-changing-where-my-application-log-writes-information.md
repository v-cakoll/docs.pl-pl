---
title: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: bdee0a91360580b156c1734ef4c82139b18ce2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74336735"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="e0bd8-102">Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0bd8-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="e0bd8-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="e0bd8-104">W tym przewodniku pokazano, jak zastąpić ustawienia domyślne i spowodować, że obiekt do zapisu `Log` do innych detektorów dziennika.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e0bd8-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e0bd8-105">Prerequisites</span></span>

<span data-ttu-id="e0bd8-106">Obiekt `Log` może zapisywać informacje do kilku odbiorników dziennika.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="e0bd8-107">Przed zmianą konfiguracji należy określić bieżącą konfigurację odbiorników dziennika.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="e0bd8-108">Aby uzyskać więcej informacji, zobacz [Przewodnik: Określanie, gdzie my.application.log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="e0bd8-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

<span data-ttu-id="e0bd8-109">Możesz przejrzeć [jak: Zapis informacji o zdarzeniu w pliku tekstowym](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) lub [Jak: Zapis w dzienniku zdarzeń aplikacji](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="e0bd8-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>

### <a name="to-add-listeners"></a><span data-ttu-id="e0bd8-110">Aby dodać słuchaczy</span><span class="sxs-lookup"><span data-stu-id="e0bd8-110">To add listeners</span></span>

1. <span data-ttu-id="e0bd8-111">Kliknij prawym przyciskiem myszy app.config w **Eksploratorze rozwiązań** i wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="e0bd8-112">\-lub -</span><span class="sxs-lookup"><span data-stu-id="e0bd8-112">\- or -</span></span>

     <span data-ttu-id="e0bd8-113">Jeśli nie ma pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="e0bd8-113">If there is no app.config file:</span></span>

    1. <span data-ttu-id="e0bd8-114">W menu **Projekt** wybierz polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-114">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="e0bd8-115">W oknie dialogowym **Dodawanie nowego elementu** wybierz pozycję Plik konfiguracji **aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>

    3. <span data-ttu-id="e0bd8-116">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-116">Click **Add**.</span></span>

2. <span data-ttu-id="e0bd8-117">Znajdź `<listeners>` sekcję w `<source>` sekcji `name` z atrybutem "DefaultSource" w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="e0bd8-118">Sekcja `<sources>` znajduje się `<system.diagnostics>` w sekcji, w `<configuration>` sekcji najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="e0bd8-119">Dodaj te elementy `<listeners>` do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-119">Add these elements to that `<listeners>` section.</span></span>

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

4. <span data-ttu-id="e0bd8-120">Odkomentuj detektory dziennika, `Log` które chcesz odbierać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>

5. <span data-ttu-id="e0bd8-121">Zlokalizuj `<sharedListeners>` `<system.diagnostics>` sekcję w sekcji `<configuration>` w sekcji najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="e0bd8-122">Dodaj te elementy `<sharedListeners>` do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-122">Add these elements to that `<sharedListeners>` section.</span></span>

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

7. <span data-ttu-id="e0bd8-123">Zawartość pliku app.config powinna być podobna do następującej opcji XML:</span><span class="sxs-lookup"><span data-stu-id="e0bd8-123">The content of the app.config file should be similar to the following XML:</span></span>

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

### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="e0bd8-124">Aby ponownie skonfigurować odbiornik</span><span class="sxs-lookup"><span data-stu-id="e0bd8-124">To reconfigure a listener</span></span>

1. <span data-ttu-id="e0bd8-125">Znajdź element odbiornika `<add>` z `<sharedListeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>

2. <span data-ttu-id="e0bd8-126">Atrybut `type` podaje nazwę typu odbiornika.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="e0bd8-127">Ten typ musi <xref:System.Diagnostics.TraceListener> dziedziczyć z klasy.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="e0bd8-128">Użyj silnie nazwanej nazwy nazwy typu, aby upewnić się, że używany jest odpowiedni typ.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="e0bd8-129">Aby uzyskać więcej informacji, zobacz sekcję "Aby odwołać się do typu o silnie nazwanej" poniżej.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-129">For more information, see the "To reference a strongly named type" section below.</span></span>

     <span data-ttu-id="e0bd8-130">Niektóre typy, których można użyć, to:</span><span class="sxs-lookup"><span data-stu-id="e0bd8-130">Some types that you can use are:</span></span>

    - <span data-ttu-id="e0bd8-131">Odbiornik, <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> który zapisuje do dziennika plików.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>

    - <span data-ttu-id="e0bd8-132">Odbiornik, <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> który zapisuje informacje do dziennika zdarzeń `initializeData` komputera określonych przez parametr.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>

    - <span data-ttu-id="e0bd8-133">I <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników, które zapisują do `initializeData` pliku określonego w parametrze.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="e0bd8-134">Odbiornik, <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> który zapisuje do konsoli wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>

     <span data-ttu-id="e0bd8-135">Aby uzyskać informacje o tym, gdzie inne typy detektorów dziennika zapisują informacje, zapoznaj się z dokumentacją tego typu.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

3. <span data-ttu-id="e0bd8-136">Gdy aplikacja tworzy obiekt detektora dziennika, `initializeData` przekazuje atrybut jako parametr konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="e0bd8-137">Znaczenie atrybutu `initializeData` zależy od odbiornika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>

4. <span data-ttu-id="e0bd8-138">Po utworzeniu odbiornika dziennika aplikacja ustawia właściwości odbiornika.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="e0bd8-139">Te właściwości są definiowane przez `<add>` inne atrybuty w elemencie.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="e0bd8-140">Aby uzyskać więcej informacji na temat właściwości dla określonego odbiornika, zobacz dokumentację dla tego typu odbiornika.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>

### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="e0bd8-141">Aby odwołać się do typu o silnie nazwanym</span><span class="sxs-lookup"><span data-stu-id="e0bd8-141">To reference a strongly named type</span></span>

1. <span data-ttu-id="e0bd8-142">Aby upewnić się, że odpowiedni typ jest używany dla odbiornika dziennika, upewnij się, że używa się w pełni kwalifikowanej nazwy typu i silnie nazwanej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="e0bd8-143">Składnia typu o silnie nazwanym typie jest następująca:</span><span class="sxs-lookup"><span data-stu-id="e0bd8-143">The syntax of a strongly named type is as follows:</span></span>

     <span data-ttu-id="e0bd8-144">\<*nazwa typu* \<>, *> nazwy zestawu,* \< *> numeru wersji,* \<> *kultury,* \< *nazwa*></span><span class="sxs-lookup"><span data-stu-id="e0bd8-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>

2. <span data-ttu-id="e0bd8-145">W tym przykładzie kodu pokazano, jak określić nazwę typu o silnie nazwanej dla w pełni kwalifikowanego typu — "System.Diagnostics.FileLogTraceListener" w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     <span data-ttu-id="e0bd8-146">Jest to dane wyjściowe i może służyć do unikatowego odwoływania się do typu o silnie nazwanych, jak w procedurze "Aby dodać odbiorniki" powyżej.</span><span class="sxs-lookup"><span data-stu-id="e0bd8-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a><span data-ttu-id="e0bd8-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0bd8-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="e0bd8-148">Instrukcje: zapisywanie informacji o zdarzeniach w pliku tekstowym</span><span class="sxs-lookup"><span data-stu-id="e0bd8-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="e0bd8-149">Instrukcje: zapisywanie w dzienniku zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="e0bd8-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
