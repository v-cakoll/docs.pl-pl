---
title: Wysokie DPI pomocy technicznej w formularzach systemu Windows
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbf2d7b61b34a2cd4641a77ee1f2fcdff7f3c3fe
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="fad1a-102">Wysokie DPI pomocy technicznej w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fad1a-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="fad1a-103">Począwszy od .NET Framework 4.7, formularze systemu Windows zawiera rozszerzenia dla typowych wysokiej rozdzielczości i dynamicznych scenariuszach rozdzielczości.</span><span class="sxs-lookup"><span data-stu-id="fad1a-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="fad1a-104">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="fad1a-104">These include:</span></span> 

- <span data-ttu-id="fad1a-105">Formanty ulepszenia skalowanie i układu liczby formularzy systemu Windows, takich jak <xref:System.Windows.Forms.MonthCalendar> kontroli i <xref:System.Windows.Forms.CheckedListBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="fad1a-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> 

- <span data-ttu-id="fad1a-106">Jednego przebiegu skalowania.</span><span class="sxs-lookup"><span data-stu-id="fad1a-106">Single-pass scaling.</span></span>  <span data-ttu-id="fad1a-107">W programie .NET Framework 4.6 i wcześniejszych wersjach skalowanie została wykonana za pomocą wielu przebiegi, które spowodowało niektóre formanty skalowania ponad konieczne było.</span><span class="sxs-lookup"><span data-stu-id="fad1a-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="fad1a-108">Obsługa dynamicznego DPI scenariusze, w których użytkownik zmieni współczynnik DPI lub skalę po uruchomieniu aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fad1a-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="fad1a-109">W wersjach programu .NET Framework w programie .NET Framework 4.7 rozszerzoną obsługę wysokiej rozdzielczości jest funkcji opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="fad1a-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="fad1a-110">Należy skonfigurować aplikację, aby móc korzystać z niego.</span><span class="sxs-lookup"><span data-stu-id="fad1a-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="fad1a-111">Konfigurowanie obsługi wysokiej rozdzielczości DPI aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fad1a-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="fad1a-112">Nowe funkcje formularzy systemu Windows, które obsługują wysokiej rozdzielczości DPI pogłębianie wiedzy na temat są dostępne tylko w aplikacji, które docelową .NET Framework 4.7 i działają w systemach operacyjnych Windows, począwszy od aktualizacji twórców systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="fad1a-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span> 

<span data-ttu-id="fad1a-113">Ponadto Konfigurowanie wysokiej obsługi DPI w aplikacji formularzy systemu Windows, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fad1a-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="fad1a-114">Deklarowanie zgodności z systemem Windows 10.</span><span class="sxs-lookup"><span data-stu-id="fad1a-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="fad1a-115">Aby to zrobić, należy dodać następujące do pliku manifestu:</span><span class="sxs-lookup"><span data-stu-id="fad1a-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="fad1a-116">Włącz świadomości rozdzielczości monitora w *app.config* pliku.</span><span class="sxs-lookup"><span data-stu-id="fad1a-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="fad1a-117">Formularze systemu Windows wprowadzono nowy [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element do obsługi nowych funkcji i dostosowania począwszy .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="fad1a-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="fad1a-118">Aby móc korzystać z nowych funkcji, które obsługują wysokiej rozdzielczości, dodaj następującą wartość do pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fad1a-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > <span data-ttu-id="fad1a-119">W poprzednich wersjach programu .NET Framework manifestu jest służy do dodawania wysokiej rozdzielczości DPI pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="fad1a-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="fad1a-120">Tej metody nie jest zalecane, ponieważ zastępuje ustawienia zdefiniowane w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="fad1a-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>
   
- <span data-ttu-id="fad1a-121">Wywołaj statycznych <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fad1a-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>
   
  <span data-ttu-id="fad1a-122">Powinno to być pierwsze wywołanie metody w punktu wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fad1a-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="fad1a-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="fad1a-123">For example:</span></span>
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="fad1a-124">Rezygnacja z poszczególnych funkcji wysokiej rozdzielczości</span><span class="sxs-lookup"><span data-stu-id="fad1a-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="fad1a-125">Ustawienie `DpiAwareness` do wartości `PerMonitorV2` włącza wszystkie wysokiej DPI świadomości funkcje obsługiwane przez wersje programu .NET Framework w programie .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="fad1a-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="fad1a-126">Zazwyczaj jest to odpowiednie dla większości aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fad1a-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="fad1a-127">Można jednak zrezygnować z jedną lub więcej poszczególnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="fad1a-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="fad1a-128">Najważniejsze przyczyny w ten sposób jest już obsługi tej funkcji przez istniejący kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fad1a-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="fad1a-129">Na przykład jeśli aplikacja obsługuje automatyczne skalowanie, możesz wyłączyć funkcję automatycznej zmiany rozmiaru w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="fad1a-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

<span data-ttu-id="fad1a-130">Aby uzyskać listę poszczególnych kluczy i ich wartości, zobacz [formularzy systemu Windows Dodaj Element konfiguracji](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="fad1a-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="fad1a-131">Nowe zdarzenia zmiany DPI</span><span class="sxs-lookup"><span data-stu-id="fad1a-131">New DPI change events</span></span>

<span data-ttu-id="fad1a-132">Począwszy od .NET Framework 4.7, trzech nowych zdarzeń umożliwiają programowe obsługi dynamicznej zmiany DPI:</span><span class="sxs-lookup"><span data-stu-id="fad1a-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="fad1a-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, które uruchamiane, gdy ustawienie DPI w formancie zostanie zmieniona programowo po zdarzeniu zmiany DPI, jego kontrolki nadrzędnej lub formularza wystąpił.</span><span class="sxs-lookup"><span data-stu-id="fad1a-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="fad1a-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, które uruchamiane, gdy ustawienie DPI w formancie zostanie zmieniona programowo przed zdarzeniem zmiany DPI dla kontrolki nadrzędnej lub formularza wystąpił.</span><span class="sxs-lookup"><span data-stu-id="fad1a-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="fad1a-135"><xref:System.Windows.Forms.Form.DpiChanged>, które jest wywoływane po zmianie ustawienia DPI na urządzeniu wyświetlana, gdy formularz jest aktualnie wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="fad1a-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="fad1a-136">Nowe metody pomocnicze i właściwości</span><span class="sxs-lookup"><span data-stu-id="fad1a-136">New helper methods and properties</span></span>

<span data-ttu-id="fad1a-137">.NET Framework 4.7 dodaje również nowe metody pomocnicze i właściwości, które zawierają informacje na temat skalowania DPI i zezwalają na wykonanie skalowania DPI.</span><span class="sxs-lookup"><span data-stu-id="fad1a-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="fad1a-138">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="fad1a-138">These include:</span></span>

- <span data-ttu-id="fad1a-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, który konwertuje wartość z logiczną na następującą liczbę pikseli urządzenia.</span><span class="sxs-lookup"><span data-stu-id="fad1a-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="fad1a-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, które skaluje obraz mapy bitowej do logicznego DPI dla urządzenia.</span><span class="sxs-lookup"><span data-stu-id="fad1a-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="fad1a-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, która zwraca wartość DPI dla bieżącego urządzenia.</span><span class="sxs-lookup"><span data-stu-id="fad1a-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="fad1a-142">Zagadnienia dotyczące kontroli wersji</span><span class="sxs-lookup"><span data-stu-id="fad1a-142">Versioning considerations</span></span>

<span data-ttu-id="fad1a-143">Oprócz systemem .NET Framework 4.7 lub Windows 10 twórców aktualizacji, aplikacji mogą być wykonywane w środowisku, w którym nie jest zgodny z wysokiej rozdzielczości DPI ulepszenia.</span><span class="sxs-lookup"><span data-stu-id="fad1a-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="fad1a-144">W takim przypadku należy opracowanie używane dla danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fad1a-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="fad1a-145">Należy przeprowadzić [Rysowanie niestandardowe](./controls/user-drawn-controls.md) do obsługi skalowania.</span><span class="sxs-lookup"><span data-stu-id="fad1a-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="fad1a-146">Aby to zrobić, należy również określić systemu operacyjnego, na którym jest uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="fad1a-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="fad1a-147">Możesz to zrobić z kodem podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="fad1a-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="fad1a-148">Należy pamiętać, że aplikacja pomyślnie nie wykryć systemu Windows 10, jeśli go nie został wymieniony jako obsługiwany system operacyjny w manifeście aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fad1a-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="fad1a-149">Możesz również sprawdzić wersji programu .NET Framework, która aplikacja została skompilowana przed:</span><span class="sxs-lookup"><span data-stu-id="fad1a-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="fad1a-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fad1a-150">See also</span></span>

[<span data-ttu-id="fad1a-151">Formularze systemu Windows, Dodaj Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fad1a-151">Windows Forms Add Configuration Element</span></span>](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[<span data-ttu-id="fad1a-152">Dostosowywanie rozmiaru i skali formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fad1a-152">Adjusting the Size and Scale of Windows Forms</span></span>](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
