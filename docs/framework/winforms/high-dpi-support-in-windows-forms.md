---
title: Wysoka obsługa rozdzielczości DPI w formularzach Windows Forms
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c591aa19a13af2f5b38c46a886b8e0ee2f76c38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540653"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="9afc7-102">Wysoka obsługa rozdzielczości DPI w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9afc7-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="9afc7-103">Począwszy od programu .NET Framework 4.7 formularzy Windows zawiera ulepszenia dla typowych o wysokiej rozdzielczości i dynamiczne scenariuszy DPI.</span><span class="sxs-lookup"><span data-stu-id="9afc7-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="9afc7-104">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9afc7-104">These include:</span></span> 

- <span data-ttu-id="9afc7-105">Ulepszenia skalowanie i układ liczby formularzy Windows Forms kontroluje, takich jak <xref:System.Windows.Forms.MonthCalendar> kontroli i <xref:System.Windows.Forms.CheckedListBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9afc7-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> 

- <span data-ttu-id="9afc7-106">Jednego przebiegu skalowania.</span><span class="sxs-lookup"><span data-stu-id="9afc7-106">Single-pass scaling.</span></span>  <span data-ttu-id="9afc7-107">W .NET Framework 4.6 i wcześniejszych wersjach skalowania została wykonana przy użyciu wielu przebiegów, które spowodowało niektóre formanty, które można skalować więcej niż było konieczne.</span><span class="sxs-lookup"><span data-stu-id="9afc7-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="9afc7-108">Obsługa dynamicznego scenariuszy DPI, w których użytkownik zmieni współczynnik skalowania lub DPI po aplikacji Windows Forms została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="9afc7-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="9afc7-109">W wersjach programu .NET Framework, począwszy od programu .NET Framework 4.7 rozszerzoną obsługę w wysokiej rozdzielczości DPI to funkcja opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="9afc7-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="9afc7-110">Należy skonfigurować aplikację, aby z niej korzystać.</span><span class="sxs-lookup"><span data-stu-id="9afc7-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="9afc7-111">Konfigurowanie aplikacji Windows Forms o wysokiej rozdzielczości DPI pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="9afc7-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="9afc7-112">Nowe funkcje Windows Forms, które obsługują wysokiej świadomości DPI są dostępne tylko w aplikacjach docelowych programu .NET Framework 4.7, które są uruchomione w systemach operacyjnych Windows, począwszy od systemu Windows 10 dla kreatywnych.</span><span class="sxs-lookup"><span data-stu-id="9afc7-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span> 

<span data-ttu-id="9afc7-113">Ponadto aby skonfigurować obsługa wysokiej rozdzielczości DPI w aplikacji Windows Forms, możesz wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9afc7-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="9afc7-114">Zadeklaruj zgodności z systemem Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9afc7-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="9afc7-115">Aby to zrobić, Dodaj do pliku manifestu:</span><span class="sxs-lookup"><span data-stu-id="9afc7-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="9afc7-116">Włączanie rozpoznawanie wartości DPI monitora w *app.config* pliku.</span><span class="sxs-lookup"><span data-stu-id="9afc7-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="9afc7-117">Windows Forms wprowadzono nowy [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element do obsługi nowych funkcji i dodać dostosowania, począwszy od programu .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="9afc7-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="9afc7-118">Aby móc korzystać z nowych funkcji, które obsługują o wysokiej rozdzielczości, Dodaj następujący element do pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9afc7-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > <span data-ttu-id="9afc7-119">W poprzednich wersjach programu .NET Framework manifest jest służy do dodawania obsługa wysokiej rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="9afc7-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="9afc7-120">To podejście nie jest już zalecany, ponieważ zastępuje ona ustawień zdefiniowanych w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="9afc7-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>
   
- <span data-ttu-id="9afc7-121">Wywołaj statyczną <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9afc7-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>
   
  <span data-ttu-id="9afc7-122">Powinna to być to pierwsze wywołanie metody w punktem wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9afc7-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="9afc7-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="9afc7-123">For example:</span></span>
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="9afc7-124">Rezygnacja z poszczególnych funkcji DPI wysoka</span><span class="sxs-lookup"><span data-stu-id="9afc7-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="9afc7-125">Ustawienie `DpiAwareness` wartość `PerMonitorV2` włącza wszystkie wysokiej funkcji świadomości DPI, są obsługiwane przez wersje programu .NET Framework, począwszy od programu .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="9afc7-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="9afc7-126">Zazwyczaj jest to odpowiednie dla większości aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9afc7-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="9afc7-127">Można jednak zrezygnować z co najmniej jeden poszczególnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="9afc7-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="9afc7-128">Najważniejszą przyczyną takiego postępowania jest, że istniejący kod aplikacji już obsługuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="9afc7-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="9afc7-129">Na przykład jeśli aplikacja obsługuje automatyczne skalowanie, możesz chcieć wyłączyć funkcję automatycznej zmiany rozmiaru w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9afc7-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

<span data-ttu-id="9afc7-130">Aby uzyskać listę poszczególnych kluczy i ich wartości, zobacz [elementu Dodawanie konfiguracji w programie Windows Forms](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="9afc7-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="9afc7-131">Nowe zdarzenia Zmiana rozdzielczości DPI</span><span class="sxs-lookup"><span data-stu-id="9afc7-131">New DPI change events</span></span>

<span data-ttu-id="9afc7-132">Począwszy od programu .NET Framework 4.7, trzy nowe zdarzenia umożliwiają programowe obsługi dynamicznej zmian rozdzielczości:</span><span class="sxs-lookup"><span data-stu-id="9afc7-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="9afc7-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, który uruchamiane, gdy ustawienie DPI dla formantu jest programistycznej zmiany po wystąpieniu zdarzenia zmiany DPI do jego kontrolki nadrzędnej lub formularza wystąpił.</span><span class="sxs-lookup"><span data-stu-id="9afc7-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="9afc7-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, którego uruchamiane, gdy ustawienie DPI dla formantu jest programistycznej zmiany przed DPI zdarzenia zmiany, do kontrolki nadrzędnej lub formularza wystąpił.</span><span class="sxs-lookup"><span data-stu-id="9afc7-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="9afc7-135"><xref:System.Windows.Forms.Form.DpiChanged>, którego uruchamiane, gdy zmieni się ustawienie DPI na urządzeniu wyświetlana, gdy formularz jest aktualnie wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="9afc7-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="9afc7-136">Nowy Pomocnik metody i właściwości</span><span class="sxs-lookup"><span data-stu-id="9afc7-136">New helper methods and properties</span></span>

<span data-ttu-id="9afc7-137">.NET Framework 4.7 również dodaje nowe metody pomocnicze i właściwości, które zawierają informacje dotyczące skalowania DPI i umożliwiają wykonywanie, Skalowanie DPI.</span><span class="sxs-lookup"><span data-stu-id="9afc7-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="9afc7-138">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9afc7-138">These include:</span></span>

- <span data-ttu-id="9afc7-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, która konwertuje wartość z logiczną pikseli urządzenia.</span><span class="sxs-lookup"><span data-stu-id="9afc7-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="9afc7-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, która skaluje się obrazu mapy bitowej do logicznego DPI dla urządzenia.</span><span class="sxs-lookup"><span data-stu-id="9afc7-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="9afc7-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, która zwraca DPI dla bieżącego urządzenia.</span><span class="sxs-lookup"><span data-stu-id="9afc7-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="9afc7-142">Uwagi dotyczące wersji</span><span class="sxs-lookup"><span data-stu-id="9afc7-142">Versioning considerations</span></span>

<span data-ttu-id="9afc7-143">Oprócz uruchamiania na .NET Framework 4.7 i systemu Windows 10 dla kreatywnych, aplikacji mogą być wykonywane w środowisku, w którym nie jest zgodny z wysokiej rozdzielczości DPI ulepszenia.</span><span class="sxs-lookup"><span data-stu-id="9afc7-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="9afc7-144">W takim przypadku należy tworzyć rezerwowych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9afc7-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="9afc7-145">Można to zrobić przeprowadzić [Rysowanie niestandardowe](./controls/user-drawn-controls.md) do obsługi skalowania.</span><span class="sxs-lookup"><span data-stu-id="9afc7-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="9afc7-146">Aby to zrobić, należy także określić systemu operacyjnego, na którym uruchomiona jest aplikacja.</span><span class="sxs-lookup"><span data-stu-id="9afc7-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="9afc7-147">Możesz to zrobić przy użyciu kodu, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="9afc7-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="9afc7-148">Należy pamiętać, że aplikacja nie będzie pomyślnie wykryć systemu Windows 10, jeśli nie został wymieniony jako obsługiwany system operacyjny w manifeście aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9afc7-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="9afc7-149">Możesz również sprawdzić wersji programu .NET Framework, która została skompilowana aplikacja:</span><span class="sxs-lookup"><span data-stu-id="9afc7-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="9afc7-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9afc7-150">See also</span></span>

- [<span data-ttu-id="9afc7-151">Windows Forms, Dodaj Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9afc7-151">Windows Forms Add Configuration Element</span></span>](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="9afc7-152">Dostosowywanie rozmiaru i skali formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9afc7-152">Adjusting the Size and Scale of Windows Forms</span></span>](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
