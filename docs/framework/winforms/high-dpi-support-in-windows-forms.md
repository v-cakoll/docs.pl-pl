---
title: Wysokie DPI pomocy technicznej w formularzach systemu Windows
ms.custom: 
ms.date: 05/16/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a68c9278d4e8092be5c744109e56f7cb52498095
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="high-dpi-support-in-windows-forms"></a>Wysokie DPI pomocy technicznej w formularzach systemu Windows

Począwszy od .NET Framework 4.7, formularze systemu Windows zawiera rozszerzenia dla typowych wysokiej rozdzielczości i dynamicznych scenariuszach rozdzielczości. Należą do nich następujące elementy: 

- Formanty ulepszenia skalowanie i układu liczby formularzy systemu Windows, takich jak <xref:System.Windows.Forms.MonthCalendar> kontroli i <xref:System.Windows.Forms.CheckedListBox> formantu. 

- Jednego przebiegu skalowania.  W programie .NET Framework 4.6 i wcześniejszych wersjach skalowanie została wykonana za pomocą wielu przebiegi, które spowodowało niektóre formanty skalowania ponad konieczne było.

- Obsługa dynamicznego DPI scenariusze, w których użytkownik zmieni współczynnik DPI lub skalę po uruchomieniu aplikacji formularzy systemu Windows.

W wersjach programu .NET Framework w programie .NET Framework 4.7 rozszerzoną obsługę wysokiej rozdzielczości jest funkcji opcjonalnych. Należy skonfigurować aplikację, aby móc korzystać z niego.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Konfigurowanie obsługi wysokiej rozdzielczości DPI aplikacji Windows Forms

Nowe funkcje formularzy systemu Windows, które obsługują wysokiej rozdzielczości DPI pogłębianie wiedzy na temat są dostępne tylko w aplikacji, które docelową .NET Framework 4.7 i działają w systemach operacyjnych Windows, począwszy od aktualizacji twórców systemu Windows 10. 

Ponadto Konfigurowanie wysokiej obsługi DPI w aplikacji formularzy systemu Windows, należy wykonać następujące czynności:

- Deklarowanie zgodności z systemem Windows 10.

  Aby to zrobić, należy dodać następujące do pliku manifestu:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.comn:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- Włącz świadomości rozdzielczości monitora w *app.config* pliku.

  Formularze systemu Windows wprowadzono nowy [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element do obsługi nowych funkcji i dostosowania począwszy .NET Framework 4.7. Aby móc korzystać z nowych funkcji, które obsługują wysokiej rozdzielczości, dodaj następującą wartość do pliku konfiguracji aplikacji.   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > W poprzednich wersjach programu .NET Framework manifestu jest służy do dodawania wysokiej rozdzielczości DPI pomocy technicznej. Tej metody nie jest zalecane, ponieważ zastępuje ustawienia zdefiniowane w pliku app.config.
   
- Wywołaj statycznych <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.
   
  Powinno to być pierwsze wywołanie metody w punktu wejścia aplikacji. Na przykład:
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Rezygnacja z poszczególnych funkcji wysokiej rozdzielczości

Ustawienie `DpiAwareness` do wartości `PerMonitorV2` włącza wszystkie wysokiej DPI świadomości funkcje obsługiwane przez wersje programu .NET Framework w programie .NET Framework 4.7. Zazwyczaj jest to odpowiednie dla większości aplikacji formularzy systemu Windows. Można jednak zrezygnować z jedną lub więcej poszczególnych funkcji. Najważniejsze przyczyny w ten sposób jest już obsługi tej funkcji przez istniejący kod aplikacji.  Na przykład jeśli aplikacja obsługuje automatyczne skalowanie, możesz wyłączyć funkcję automatycznej zmiany rozmiaru w następujący sposób:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

Aby uzyskać listę poszczególnych kluczy i ich wartości, zobacz [formularzy systemu Windows Dodaj Element konfiguracji](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Nowe zdarzenia zmiany DPI

Począwszy od .NET Framework 4.7, trzech nowych zdarzeń umożliwiają programowe obsługi dynamicznej zmiany DPI:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, które uruchamiane, gdy ustawienie DPI w formancie zostanie zmieniona programowo po zdarzeniu zmiany DPI, jego kontrolki nadrzędnej lub formularza wystąpił.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, które uruchamiane, gdy ustawienie DPI w formancie zostanie zmieniona programowo przed zdarzeniem zmiany DPI dla kontrolki nadrzędnej lub formularza wystąpił.
- <xref:System.Windows.Forms.Form.DpiChanged>, które jest wywoływane po zmianie ustawienia DPI na urządzeniu wyświetlana, gdy formularz jest aktualnie wyświetlany.

## <a name="new-helper-methods-and-properties"></a>Nowe metody pomocnicze i właściwości

.NET Framework 4.7 dodaje również nowe metody pomocnicze i właściwości, które zawierają informacje na temat skalowania DPI i zezwalają na wykonanie skalowania DPI. Należą do nich następujące elementy:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, który konwertuje wartość z logiczną na następującą liczbę pikseli urządzenia.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, które skaluje obraz mapy bitowej do logicznego DPI dla urządzenia.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, która zwraca wartość DPI dla bieżącego urządzenia.

## <a name="versioning-considerations"></a>Zagadnienia dotyczące kontroli wersji

Oprócz systemem .NET Framework 4.7 lub Windows 10 twórców aktualizacji, aplikacji mogą być wykonywane w środowisku, w którym nie jest zgodny z wysokiej rozdzielczości DPI ulepszenia. W takim przypadku należy opracowanie używane dla danych aplikacji. Należy przeprowadzić [Rysowanie niestandardowe](./controls/user-drawn-controls.md) do obsługi skalowania.

Aby to zrobić, należy również określić systemu operacyjnego, na którym jest uruchomiona aplikacja. Możesz to zrobić z kodem podobne do poniższych:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Należy pamiętać, że aplikacja pomyślnie nie wykryć systemu Windows 10, jeśli go nie został wymieniony jako obsługiwany system operacyjny w manifeście aplikacji.

Możesz również sprawdzić wersji programu .NET Framework, która aplikacja została skompilowana przed:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Zobacz także

[Formularze systemu Windows, Dodaj Element konfiguracji](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[Dostosowywanie rozmiaru i skali formularzy Windows Forms](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
