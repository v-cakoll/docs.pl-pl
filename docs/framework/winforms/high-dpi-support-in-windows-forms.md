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
# <a name="high-dpi-support-in-windows-forms"></a>Wysoka obsługa rozdzielczości DPI w formularzach Windows Forms

Począwszy od programu .NET Framework 4.7 formularzy Windows zawiera ulepszenia dla typowych o wysokiej rozdzielczości i dynamiczne scenariuszy DPI. Należą do nich następujące elementy: 

- Ulepszenia skalowanie i układ liczby formularzy Windows Forms kontroluje, takich jak <xref:System.Windows.Forms.MonthCalendar> kontroli i <xref:System.Windows.Forms.CheckedListBox> kontroli. 

- Jednego przebiegu skalowania.  W .NET Framework 4.6 i wcześniejszych wersjach skalowania została wykonana przy użyciu wielu przebiegów, które spowodowało niektóre formanty, które można skalować więcej niż było konieczne.

- Obsługa dynamicznego scenariuszy DPI, w których użytkownik zmieni współczynnik skalowania lub DPI po aplikacji Windows Forms została uruchomiona.

W wersjach programu .NET Framework, począwszy od programu .NET Framework 4.7 rozszerzoną obsługę w wysokiej rozdzielczości DPI to funkcja opcjonalna. Należy skonfigurować aplikację, aby z niej korzystać.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Konfigurowanie aplikacji Windows Forms o wysokiej rozdzielczości DPI pomocy technicznej.

Nowe funkcje Windows Forms, które obsługują wysokiej świadomości DPI są dostępne tylko w aplikacjach docelowych programu .NET Framework 4.7, które są uruchomione w systemach operacyjnych Windows, począwszy od systemu Windows 10 dla kreatywnych. 

Ponadto aby skonfigurować obsługa wysokiej rozdzielczości DPI w aplikacji Windows Forms, możesz wykonaj następujące czynności:

- Zadeklaruj zgodności z systemem Windows 10.

  Aby to zrobić, Dodaj do pliku manifestu:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- Włączanie rozpoznawanie wartości DPI monitora w *app.config* pliku.

  Windows Forms wprowadzono nowy [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element do obsługi nowych funkcji i dodać dostosowania, począwszy od programu .NET Framework 4.7. Aby móc korzystać z nowych funkcji, które obsługują o wysokiej rozdzielczości, Dodaj następujący element do pliku konfiguracyjnego aplikacji.   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > W poprzednich wersjach programu .NET Framework manifest jest służy do dodawania obsługa wysokiej rozdzielczości DPI. To podejście nie jest już zalecany, ponieważ zastępuje ona ustawień zdefiniowanych w pliku app.config.
   
- Wywołaj statyczną <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.
   
  Powinna to być to pierwsze wywołanie metody w punktem wejścia aplikacji. Na przykład:
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Rezygnacja z poszczególnych funkcji DPI wysoka

Ustawienie `DpiAwareness` wartość `PerMonitorV2` włącza wszystkie wysokiej funkcji świadomości DPI, są obsługiwane przez wersje programu .NET Framework, począwszy od programu .NET Framework 4.7. Zazwyczaj jest to odpowiednie dla większości aplikacji Windows Forms. Można jednak zrezygnować z co najmniej jeden poszczególnych funkcji. Najważniejszą przyczyną takiego postępowania jest, że istniejący kod aplikacji już obsługuje tę funkcję.  Na przykład jeśli aplikacja obsługuje automatyczne skalowanie, możesz chcieć wyłączyć funkcję automatycznej zmiany rozmiaru w następujący sposób:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

Aby uzyskać listę poszczególnych kluczy i ich wartości, zobacz [elementu Dodawanie konfiguracji w programie Windows Forms](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Nowe zdarzenia Zmiana rozdzielczości DPI

Począwszy od programu .NET Framework 4.7, trzy nowe zdarzenia umożliwiają programowe obsługi dynamicznej zmian rozdzielczości:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, który uruchamiane, gdy ustawienie DPI dla formantu jest programistycznej zmiany po wystąpieniu zdarzenia zmiany DPI do jego kontrolki nadrzędnej lub formularza wystąpił.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, którego uruchamiane, gdy ustawienie DPI dla formantu jest programistycznej zmiany przed DPI zdarzenia zmiany, do kontrolki nadrzędnej lub formularza wystąpił.
- <xref:System.Windows.Forms.Form.DpiChanged>, którego uruchamiane, gdy zmieni się ustawienie DPI na urządzeniu wyświetlana, gdy formularz jest aktualnie wyświetlany.

## <a name="new-helper-methods-and-properties"></a>Nowy Pomocnik metody i właściwości

.NET Framework 4.7 również dodaje nowe metody pomocnicze i właściwości, które zawierają informacje dotyczące skalowania DPI i umożliwiają wykonywanie, Skalowanie DPI. Należą do nich następujące elementy:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, która konwertuje wartość z logiczną pikseli urządzenia.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, która skaluje się obrazu mapy bitowej do logicznego DPI dla urządzenia.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, która zwraca DPI dla bieżącego urządzenia.

## <a name="versioning-considerations"></a>Uwagi dotyczące wersji

Oprócz uruchamiania na .NET Framework 4.7 i systemu Windows 10 dla kreatywnych, aplikacji mogą być wykonywane w środowisku, w którym nie jest zgodny z wysokiej rozdzielczości DPI ulepszenia. W takim przypadku należy tworzyć rezerwowych dla aplikacji. Można to zrobić przeprowadzić [Rysowanie niestandardowe](./controls/user-drawn-controls.md) do obsługi skalowania.

Aby to zrobić, należy także określić systemu operacyjnego, na którym uruchomiona jest aplikacja. Możesz to zrobić przy użyciu kodu, jak pokazano poniżej:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Należy pamiętać, że aplikacja nie będzie pomyślnie wykryć systemu Windows 10, jeśli nie został wymieniony jako obsługiwany system operacyjny w manifeście aplikacji.

Możesz również sprawdzić wersji programu .NET Framework, która została skompilowana aplikacja:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Zobacz także

- [Windows Forms, Dodaj Element konfiguracji](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [Dostosowywanie rozmiaru i skali formularzy Windows Forms](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
