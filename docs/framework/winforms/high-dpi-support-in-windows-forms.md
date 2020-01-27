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
# <a name="high-dpi-support-in-windows-forms"></a>Obsługa wysokiej rozdzielczości DPI w Windows Forms

Począwszy od .NET Framework 4,7, Windows Forms zawiera usprawnienia dla typowych scenariuszy o wysokiej rozdzielczości DPI i rozdzielczości DPI. Należą do nich następujące elementy:

- Ulepszenia skalowania i układu wielu kontrolek Windows Forms, takich jak kontrolka <xref:System.Windows.Forms.MonthCalendar> i kontrolka <xref:System.Windows.Forms.CheckedListBox>.

- Skalowanie pojedynczej karty.  W .NET Framework 4,6 i wcześniejszych wersjach skalowanie było wykonywane przez wiele przebiegów, co spowodowało, że niektóre kontrolki są skalowane więcej niż jest to konieczne.

- Obsługa dynamicznych scenariuszy DPI, w których użytkownik zmienia współczynnik DPI lub skalowania po uruchomieniu aplikacji Windows Forms.

W wersjach .NET Framework rozpoczynających się od .NET Framework 4,7 Ulepszona obsługa wysokiej rozdzielczości DPI jest funkcją wyboru. Musisz skonfigurować aplikację, aby korzystać z niej.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Konfigurowanie aplikacji Windows Forms na potrzeby obsługi wysokiej rozdzielczości DPI

Nowe funkcje Windows Forms obsługujące rozpoznawanie wysokiej rozdzielczości DPI są dostępne tylko w aplikacjach przeznaczonych dla .NET Framework 4,7 i działają w systemach operacyjnych Windows, począwszy od aktualizacji systemu Windows 10 dla twórców.

Ponadto w celu skonfigurowania obsługi wysokiej rozdzielczości DPI w aplikacji Windows Forms należy wykonać następujące czynności:

- Zadeklaruj zgodność z systemem Windows 10.

  Aby to zrobić, Dodaj następujący plik do pliku manifestu:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- Włącz obsługę rozdzielczości DPI na poziomie monitora w pliku *App. config* .

  Windows Forms wprowadza nowy element [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) do obsługi nowych funkcji i dostosowanych dostosowań, rozpoczynając od .NET Framework 4,7. Aby skorzystać z nowych funkcji, które obsługują wysoką wartość DPI, Dodaj następujące elementy do pliku konfiguracji aplikacji.

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > W poprzednich wersjach .NET Framework użyto manifestu w celu dodania obsługi wysokiej rozdzielczości DPI. Takie podejście nie jest już zalecane, ponieważ zastępuje ustawienia zdefiniowane w pliku App. config.

- Wywołaj metodę static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.

  Powinno to być pierwsze wywołanie metody w punkcie wejścia aplikacji. Na przykład:

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Rezygnacja z pojedynczych funkcji wysokiej rozdzielczości DPI

Ustawienie wartości `DpiAwareness` na `PerMonitorV2` włącza wszystkie funkcje rozpoznawania o wysokiej rozdzielczości DPI obsługiwane przez .NET Framework wersje zaczynające się od .NET Framework 4,7. Zwykle jest to odpowiednie dla większości aplikacji Windows Forms. Można jednak zrezygnować z jednej lub kilku poszczególnych funkcji. Najważniejszym powodem tego jest to, że istniejący kod aplikacji już obsługuje tę funkcję.  Na przykład jeśli aplikacja obsługuje automatyczne skalowanie, można wyłączyć funkcję automatycznego zmieniania rozmiarów w następujący sposób:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

Aby uzyskać listę poszczególnych kluczy i ich wartości, zobacz [Windows Forms dodawania elementu konfiguracji](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Nowe zdarzenia zmiany DPI

Począwszy od .NET Framework 4,7, trzy nowe zdarzenia pozwalają programowo obsługiwać dynamiczne zmiany DPI:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, który jest uruchamiany, gdy ustawienie DPI dla kontrolki jest zmieniane programowo po wystąpieniu zdarzenia zmiany DPI dla jego formantu nadrzędnego lub formularza.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, który jest uruchamiany, gdy ustawienie DPI dla kontrolki jest zmieniane programowo przed wystąpieniem zdarzenia zmiany DPI dla jego formantu nadrzędnego lub formularza.
- <xref:System.Windows.Forms.Form.DpiChanged>, który jest uruchamiany, gdy ustawienie DPI zostanie zmienione na urządzeniu wyświetlającym, w którym formularz jest aktualnie wyświetlany.

## <a name="new-helper-methods-and-properties"></a>Nowe metody i właściwości pomocnika

.NET Framework 4,7 dodaje także nowe metody pomocnika i właściwości, które zawierają informacje na temat skalowania DPI i umożliwiają skalowanie DPI. Należą do nich następujące elementy:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, która konwertuje wartość z logicznego na piksele urządzenia.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, która skaluje obraz mapy bitowej do logicznej rozdzielczości DPI urządzenia.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, która zwraca wartość DPI dla bieżącego urządzenia.

## <a name="versioning-considerations"></a>Zagadnienia dotyczące wersji

Oprócz uruchamiania w systemie .NET Framework 4,7 i aktualizacji systemu Windows 10 dla twórców aplikacja może również działać w środowisku, w którym nie jest zgodna z ulepszeniami o wysokiej rozdzielczości DPI. W takim przypadku należy opracować rezerwę dla aplikacji. Można to zrobić, aby przeprowadzić [Niestandardowe Rysowanie](./controls/user-drawn-controls.md) w celu obsługi skalowania.

W tym celu należy również określić system operacyjny, w którym działa aplikacja. Można to zrobić z kodem podobnym do następującego:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Należy zauważyć, że aplikacja nie będzie mogła pomyślnie wykryć systemu Windows 10, jeśli nie został on wymieniony jako obsługiwany system operacyjny w manifeście aplikacji.

Możesz również sprawdzić wersję .NET Framework, z którą została skompilowana aplikacja:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Zobacz także

- [Windows Forms dodać elementu konfiguracji](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [Dostosowywanie rozmiaru i skali formularzy Windows Forms](adjusting-the-size-and-scale-of-windows-forms.md)
