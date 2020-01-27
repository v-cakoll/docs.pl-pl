---
title: Obsługa wysokiej rozdzielczości DPI
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a5c3125475c2de2cf83a3d97e356b26c0acdde99
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741898"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="5c3cc-102">Obsługa wysokiej rozdzielczości DPI w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c3cc-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="5c3cc-103">Począwszy od .NET Framework 4,7, Windows Forms zawiera usprawnienia dla typowych scenariuszy o wysokiej rozdzielczości DPI i rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="5c3cc-104">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5c3cc-104">These include:</span></span>

- <span data-ttu-id="5c3cc-105">Ulepszenia skalowania i układu wielu kontrolek Windows Forms, takich jak kontrolka <xref:System.Windows.Forms.MonthCalendar> i kontrolka <xref:System.Windows.Forms.CheckedListBox>.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span>

- <span data-ttu-id="5c3cc-106">Skalowanie pojedynczej karty.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-106">Single-pass scaling.</span></span>  <span data-ttu-id="5c3cc-107">W .NET Framework 4,6 i wcześniejszych wersjach skalowanie było wykonywane przez wiele przebiegów, co spowodowało, że niektóre kontrolki są skalowane więcej niż jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="5c3cc-108">Obsługa dynamicznych scenariuszy DPI, w których użytkownik zmienia współczynnik DPI lub skalowania po uruchomieniu aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="5c3cc-109">W wersjach .NET Framework rozpoczynających się od .NET Framework 4,7 Ulepszona obsługa wysokiej rozdzielczości DPI jest funkcją wyboru.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="5c3cc-110">Musisz skonfigurować aplikację, aby korzystać z niej.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="5c3cc-111">Konfigurowanie aplikacji Windows Forms na potrzeby obsługi wysokiej rozdzielczości DPI</span><span class="sxs-lookup"><span data-stu-id="5c3cc-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="5c3cc-112">Nowe funkcje Windows Forms obsługujące rozpoznawanie wysokiej rozdzielczości DPI są dostępne tylko w aplikacjach przeznaczonych dla .NET Framework 4,7 i działają w systemach operacyjnych Windows, począwszy od aktualizacji systemu Windows 10 dla twórców.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span>

<span data-ttu-id="5c3cc-113">Ponadto w celu skonfigurowania obsługi wysokiej rozdzielczości DPI w aplikacji Windows Forms należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5c3cc-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="5c3cc-114">Zadeklaruj zgodność z systemem Windows 10.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="5c3cc-115">Aby to zrobić, Dodaj następujący plik do pliku manifestu:</span><span class="sxs-lookup"><span data-stu-id="5c3cc-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="5c3cc-116">Włącz obsługę rozdzielczości DPI na poziomie monitora w pliku *App. config* .</span><span class="sxs-lookup"><span data-stu-id="5c3cc-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="5c3cc-117">Windows Forms wprowadza nowy element [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) do obsługi nowych funkcji i dostosowanych dostosowań, rozpoczynając od .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="5c3cc-118">Aby skorzystać z nowych funkcji, które obsługują wysoką wartość DPI, Dodaj następujące elementy do pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > <span data-ttu-id="5c3cc-119">W poprzednich wersjach .NET Framework użyto manifestu w celu dodania obsługi wysokiej rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="5c3cc-120">Takie podejście nie jest już zalecane, ponieważ zastępuje ustawienia zdefiniowane w pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>

- <span data-ttu-id="5c3cc-121">Wywołaj metodę static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>

  <span data-ttu-id="5c3cc-122">Powinno to być pierwsze wywołanie metody w punkcie wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="5c3cc-123">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5c3cc-123">For example:</span></span>

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="5c3cc-124">Rezygnacja z pojedynczych funkcji wysokiej rozdzielczości DPI</span><span class="sxs-lookup"><span data-stu-id="5c3cc-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="5c3cc-125">Ustawienie wartości `DpiAwareness` na `PerMonitorV2` włącza wszystkie funkcje rozpoznawania o wysokiej rozdzielczości DPI obsługiwane przez .NET Framework wersje zaczynające się od .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="5c3cc-126">Zwykle jest to odpowiednie dla większości aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="5c3cc-127">Można jednak zrezygnować z jednej lub kilku poszczególnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="5c3cc-128">Najważniejszym powodem tego jest to, że istniejący kod aplikacji już obsługuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="5c3cc-129">Na przykład jeśli aplikacja obsługuje automatyczne skalowanie, można wyłączyć funkcję automatycznego zmieniania rozmiarów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5c3cc-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

<span data-ttu-id="5c3cc-130">Aby uzyskać listę poszczególnych kluczy i ich wartości, zobacz [Windows Forms dodawania elementu konfiguracji](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="5c3cc-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="5c3cc-131">Nowe zdarzenia zmiany DPI</span><span class="sxs-lookup"><span data-stu-id="5c3cc-131">New DPI change events</span></span>

<span data-ttu-id="5c3cc-132">Począwszy od .NET Framework 4,7, trzy nowe zdarzenia pozwalają programowo obsługiwać dynamiczne zmiany DPI:</span><span class="sxs-lookup"><span data-stu-id="5c3cc-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="5c3cc-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, który jest uruchamiany, gdy ustawienie DPI dla kontrolki jest zmieniane programowo po wystąpieniu zdarzenia zmiany DPI dla jego formantu nadrzędnego lub formularza.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="5c3cc-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, który jest uruchamiany, gdy ustawienie DPI dla kontrolki jest zmieniane programowo przed wystąpieniem zdarzenia zmiany DPI dla jego formantu nadrzędnego lub formularza.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="5c3cc-135"><xref:System.Windows.Forms.Form.DpiChanged>, który jest uruchamiany, gdy ustawienie DPI zostanie zmienione na urządzeniu wyświetlającym, w którym formularz jest aktualnie wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="5c3cc-136">Nowe metody i właściwości pomocnika</span><span class="sxs-lookup"><span data-stu-id="5c3cc-136">New helper methods and properties</span></span>

<span data-ttu-id="5c3cc-137">.NET Framework 4,7 dodaje także nowe metody pomocnika i właściwości, które zawierają informacje na temat skalowania DPI i umożliwiają skalowanie DPI.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="5c3cc-138">Należą do nich następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5c3cc-138">These include:</span></span>

- <span data-ttu-id="5c3cc-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, która konwertuje wartość z logicznego na piksele urządzenia.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="5c3cc-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, która skaluje obraz mapy bitowej do logicznej rozdzielczości DPI urządzenia.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="5c3cc-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, która zwraca wartość DPI dla bieżącego urządzenia.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="5c3cc-142">Zagadnienia dotyczące wersji</span><span class="sxs-lookup"><span data-stu-id="5c3cc-142">Versioning considerations</span></span>

<span data-ttu-id="5c3cc-143">Oprócz uruchamiania w systemie .NET Framework 4,7 i aktualizacji systemu Windows 10 dla twórców aplikacja może również działać w środowisku, w którym nie jest zgodna z ulepszeniami o wysokiej rozdzielczości DPI.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="5c3cc-144">W takim przypadku należy opracować rezerwę dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="5c3cc-145">Można to zrobić, aby przeprowadzić [Niestandardowe Rysowanie](./controls/user-drawn-controls.md) w celu obsługi skalowania.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="5c3cc-146">W tym celu należy również określić system operacyjny, w którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="5c3cc-147">Można to zrobić z kodem podobnym do następującego:</span><span class="sxs-lookup"><span data-stu-id="5c3cc-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="5c3cc-148">Należy zauważyć, że aplikacja nie będzie mogła pomyślnie wykryć systemu Windows 10, jeśli nie został on wymieniony jako obsługiwany system operacyjny w manifeście aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5c3cc-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="5c3cc-149">Możesz również sprawdzić wersję .NET Framework, z którą została skompilowana aplikacja:</span><span class="sxs-lookup"><span data-stu-id="5c3cc-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="5c3cc-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c3cc-150">See also</span></span>

- [<span data-ttu-id="5c3cc-151">Windows Forms dodać elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5c3cc-151">Windows Forms Add Configuration Element</span></span>](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="5c3cc-152">Dostosowywanie rozmiaru i skali formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c3cc-152">Adjusting the Size and Scale of Windows Forms</span></span>](adjusting-the-size-and-scale-of-windows-forms.md)
