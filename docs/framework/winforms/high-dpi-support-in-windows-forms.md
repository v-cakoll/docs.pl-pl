---
title: Obsługa wysokiej rozdzielczości DPI
description: Dowiedz się więcej na temat pomocy technicznej w Windows Forms na potrzeby typowych scenariuszy o wysokiej rozdzielczości DPI i rozdzielczości DPI. Dowiedz się również, jak skonfigurować aplikacje Windows Forms na potrzeby obsługi wysokiej rozdzielczości DPI.
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a9e0766307095da447c772de5a3065c18b7b7154
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325647"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="46585-104">Obsługa wysokiej rozdzielczości DPI w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46585-104">High DPI support in Windows Forms</span></span>

<span data-ttu-id="46585-105">Począwszy od .NET Framework 4,7, Windows Forms zawiera usprawnienia dla typowych scenariuszy o wysokiej rozdzielczości DPI i rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="46585-105">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="46585-106">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="46585-106">These include:</span></span>

- <span data-ttu-id="46585-107">Ulepszenia skalowania i układu wielu kontrolek Windows Forms, takich jak <xref:System.Windows.Forms.MonthCalendar> kontrolka i <xref:System.Windows.Forms.CheckedListBox> kontrolka.</span><span class="sxs-lookup"><span data-stu-id="46585-107">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span>

- <span data-ttu-id="46585-108">Skalowanie pojedynczej karty.</span><span class="sxs-lookup"><span data-stu-id="46585-108">Single-pass scaling.</span></span>  <span data-ttu-id="46585-109">W .NET Framework 4,6 i wcześniejszych wersjach skalowanie było wykonywane przez wiele przebiegów, co spowodowało, że niektóre kontrolki są skalowane więcej niż jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="46585-109">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="46585-110">Obsługa dynamicznych scenariuszy DPI, w których użytkownik zmienia współczynnik DPI lub skalowania po uruchomieniu aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="46585-110">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="46585-111">W wersjach .NET Framework rozpoczynających się od .NET Framework 4,7 Ulepszona obsługa wysokiej rozdzielczości DPI jest funkcją wyboru.</span><span class="sxs-lookup"><span data-stu-id="46585-111">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="46585-112">Musisz skonfigurować aplikację, aby korzystać z niej.</span><span class="sxs-lookup"><span data-stu-id="46585-112">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="46585-113">Konfigurowanie aplikacji Windows Forms na potrzeby obsługi wysokiej rozdzielczości DPI</span><span class="sxs-lookup"><span data-stu-id="46585-113">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="46585-114">Nowe funkcje Windows Forms obsługujące rozpoznawanie wysokiej rozdzielczości DPI są dostępne tylko w aplikacjach przeznaczonych dla .NET Framework 4,7 i działają w systemach operacyjnych Windows, począwszy od aktualizacji systemu Windows 10 dla twórców.</span><span class="sxs-lookup"><span data-stu-id="46585-114">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span>

<span data-ttu-id="46585-115">Ponadto w celu skonfigurowania obsługi wysokiej rozdzielczości DPI w aplikacji Windows Forms należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="46585-115">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="46585-116">Zadeklaruj zgodność z systemem Windows 10.</span><span class="sxs-lookup"><span data-stu-id="46585-116">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="46585-117">Aby to zrobić, Dodaj następujący plik do pliku manifestu:</span><span class="sxs-lookup"><span data-stu-id="46585-117">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="46585-118">Włącz świadomość rozdzielczości DPI dla monitora w pliku *app.config* .</span><span class="sxs-lookup"><span data-stu-id="46585-118">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="46585-119">Windows Forms wprowadza nowy [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element do obsługi nowych funkcji i dostosowanych dostosowań, zaczynając od .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="46585-119">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="46585-120">Aby skorzystać z nowych funkcji, które obsługują wysoką wartość DPI, Dodaj następujące elementy do pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46585-120">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > <span data-ttu-id="46585-121">W poprzednich wersjach .NET Framework użyto manifestu w celu dodania obsługi wysokiej rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="46585-121">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="46585-122">Takie podejście nie jest już zalecane, ponieważ zastępuje ustawienia zdefiniowane w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="46585-122">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>

- <span data-ttu-id="46585-123">Wywołaj metodę statyczną <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> .</span><span class="sxs-lookup"><span data-stu-id="46585-123">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>

  <span data-ttu-id="46585-124">Powinno to być pierwsze wywołanie metody w punkcie wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46585-124">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="46585-125">Przykład:</span><span class="sxs-lookup"><span data-stu-id="46585-125">For example:</span></span>

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="46585-126">Rezygnacja z pojedynczych funkcji wysokiej rozdzielczości DPI</span><span class="sxs-lookup"><span data-stu-id="46585-126">Opting out of individual high DPI features</span></span>

<span data-ttu-id="46585-127">Ustawienie `DpiAwareness` wartości, aby `PerMonitorV2` włączyć wszystkie funkcje rozpoznawania o wysokiej rozdzielczości DPI obsługiwane przez .NET Framework wersje, począwszy od .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="46585-127">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="46585-128">Zwykle jest to odpowiednie dla większości aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="46585-128">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="46585-129">Można jednak zrezygnować z jednej lub kilku poszczególnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="46585-129">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="46585-130">Najważniejszym powodem tego jest to, że istniejący kod aplikacji już obsługuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="46585-130">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="46585-131">Na przykład jeśli aplikacja obsługuje automatyczne skalowanie, można wyłączyć funkcję automatycznego zmieniania rozmiarów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="46585-131">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

<span data-ttu-id="46585-132">Aby uzyskać listę poszczególnych kluczy i ich wartości, zobacz [Windows Forms dodawania elementu konfiguracji](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="46585-132">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="46585-133">Nowe zdarzenia zmiany DPI</span><span class="sxs-lookup"><span data-stu-id="46585-133">New DPI change events</span></span>

<span data-ttu-id="46585-134">Począwszy od .NET Framework 4,7, trzy nowe zdarzenia pozwalają programowo obsługiwać dynamiczne zmiany DPI:</span><span class="sxs-lookup"><span data-stu-id="46585-134">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="46585-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, który jest uruchamiany, gdy ustawienie DPI dla kontrolki jest zmieniane programowo po wystąpieniu zdarzenia zmiany DPI dla jego formantu nadrzędnego lub formularza.</span><span class="sxs-lookup"><span data-stu-id="46585-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="46585-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, który jest uruchamiany, gdy ustawienie DPI dla kontrolki jest zmieniane programowo przed wystąpieniem zdarzenia zmiany DPI dla jego kontrolki nadrzędnej lub formularza.</span><span class="sxs-lookup"><span data-stu-id="46585-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="46585-137"><xref:System.Windows.Forms.Form.DpiChanged>, który jest uruchamiany, gdy ustawienie DPI zostanie zmienione na urządzeniu wyświetlającym, w którym formularz jest aktualnie wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="46585-137"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="46585-138">Nowe metody i właściwości pomocnika</span><span class="sxs-lookup"><span data-stu-id="46585-138">New helper methods and properties</span></span>

<span data-ttu-id="46585-139">.NET Framework 4,7 dodaje także nowe metody pomocnika i właściwości, które zawierają informacje na temat skalowania DPI i umożliwiają skalowanie DPI.</span><span class="sxs-lookup"><span data-stu-id="46585-139">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="46585-140">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="46585-140">These include:</span></span>

- <span data-ttu-id="46585-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, która konwertuje wartość z logicznego na piksele urządzenia.</span><span class="sxs-lookup"><span data-stu-id="46585-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="46585-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, które skaluje obraz mapy bitowej do logicznej rozdzielczości DPI urządzenia.</span><span class="sxs-lookup"><span data-stu-id="46585-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="46585-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, która zwraca wartość DPI dla bieżącego urządzenia.</span><span class="sxs-lookup"><span data-stu-id="46585-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="46585-144">Zagadnienia dotyczące wersji</span><span class="sxs-lookup"><span data-stu-id="46585-144">Versioning considerations</span></span>

<span data-ttu-id="46585-145">Oprócz uruchamiania w systemie .NET Framework 4,7 i aktualizacji systemu Windows 10 dla twórców aplikacja może również działać w środowisku, w którym nie jest zgodna z ulepszeniami o wysokiej rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="46585-145">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="46585-146">W takim przypadku należy opracować rezerwę dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46585-146">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="46585-147">Można to zrobić, aby przeprowadzić [Niestandardowe Rysowanie](./controls/user-drawn-controls.md) w celu obsługi skalowania.</span><span class="sxs-lookup"><span data-stu-id="46585-147">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="46585-148">W tym celu należy również określić system operacyjny, w którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="46585-148">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="46585-149">Można to zrobić z kodem podobnym do następującego:</span><span class="sxs-lookup"><span data-stu-id="46585-149">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="46585-150">Należy zauważyć, że aplikacja nie będzie mogła pomyślnie wykryć systemu Windows 10, jeśli nie został on wymieniony jako obsługiwany system operacyjny w manifeście aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46585-150">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="46585-151">Możesz również sprawdzić wersję .NET Framework, z którą została skompilowana aplikacja:</span><span class="sxs-lookup"><span data-stu-id="46585-151">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="46585-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46585-152">See also</span></span>

- [<span data-ttu-id="46585-153">Windows Forms dodać elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="46585-153">Windows Forms Add Configuration Element</span></span>](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="46585-154">Dostosowywanie rozmiaru i skali formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46585-154">Adjusting the Size and Scale of Windows Forms</span></span>](adjusting-the-size-and-scale-of-windows-forms.md)
