---
title: 'Instrukcje: Walidacja ustawień aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
ms.openlocfilehash: 220b86c0de57e60036527bb49f2d8de46390a9ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929790"
---
# <a name="how-to-validate-application-settings"></a>Instrukcje: Walidacja ustawień aplikacji

W tym temacie przedstawiono sposób sprawdzania poprawności ustawień aplikacji przed ich utrwaleniem.

Ponieważ ustawienia aplikacji mają silną wartość, masz pewność, że użytkownicy nie mogą przypisywać danych nieprawidłowego typu do danego ustawienia. Jednak użytkownik nadal może próbować przypisać wartość do ustawienia, które wykracza poza akceptowalne granice — na przykład dostarczając datę urodzenia, która występuje w przyszłości. <xref:System.Configuration.ApplicationSettingsBase>, Klasa nadrzędna wszystkich klas ustawień aplikacji udostępnia cztery zdarzenia umożliwiające sprawdzenie takich powiązań. Obsługa tych zdarzeń umieszcza cały kod weryfikacyjny w jednej lokalizacji, zamiast rozpraszać go w całym projekcie.

Używane zdarzenie zależy od tego, kiedy trzeba zweryfikować ustawienia, zgodnie z opisem w poniższej tabeli.

|Zdarzenie|Wystąpienie i użycie|
|-----------|------------------------|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Występuje po początkowym załadowaniu grupy właściwości ustawień.<br /><br /> To zdarzenie służy do sprawdzania poprawności wartości początkowych dla całej grupy właściwości, zanim zostaną one użyte w aplikacji.|
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Występuje przed zmianą wartości właściwości Single Settings.<br /><br /> Użyj tego zdarzenia, aby sprawdzić poprawność pojedynczej właściwości przed jej zmianą. Może ona udostępniać użytkownikom natychmiastową opinię dotyczącą ich działań i wyborów.|
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Występuje po zmianie wartości właściwości Single Settings.<br /><br /> To zdarzenie służy do sprawdzania poprawności pojedynczej właściwości po jej zmianie. To zdarzenie jest rzadko używane do sprawdzania poprawności, chyba że jest wymagany proces asynchronicznej walidacji.|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Występuje przed zapisaniem grupy właściwości ustawienia.<br /><br /> To zdarzenie służy do sprawdzania poprawności wartości dla całej grupy właściwości, zanim zostaną one utrwalone na dysku.|

Zwykle nie będzie można używać wszystkich tych zdarzeń w ramach tej samej aplikacji na potrzeby sprawdzania poprawności. Na przykład często istnieje możliwość spełnienia wszystkich wymagań związanych z walidacją przez obsługę tylko <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzenia.

Program obsługi zdarzeń zazwyczaj wykonuje jedną z następujących akcji po wykryciu nieprawidłowej wartości:

- Automatycznie dostarcza wartość znaną do poprawnego, na przykład wartość domyślną.

- Umożliwia ponowne zazapytanie użytkownika kodu serwera o informacje.

- Dla zdarzeń wywoływanych przed skojarzonych z nimi akcjami <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> , <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>takimi jak <xref:System.ComponentModel.CancelEventArgs> i, używa argumentu, aby anulować operację.

Aby uzyskać więcej informacji na temat obsługi zdarzeń, zobacz [Omówienie obsługi zdarzeń](../event-handlers-overview-windows-forms.md).

W poniższych procedurach pokazano, jak sprawdzić poprawność daty urodzenia przy <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> użyciu <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> albo zdarzenia. Procedury zostały utworzone w ramach założeń, w których utworzono już ustawienia aplikacji; w tym przykładzie wykonamy sprawdzanie granic dla ustawienia o nazwie `DateOfBirth`. Aby uzyskać więcej informacji na temat tworzenia ustawień [, zobacz How to: Utwórz ustawienia](how-to-create-application-settings.md)aplikacji.

### <a name="to-obtain-the-application-settings-object"></a>Aby uzyskać obiekt ustawień aplikacji

- Uzyskaj odwołanie do obiektu ustawień aplikacji (wystąpienie otoki), wykonując jedną z następujących pozycji:

  - Jeśli ustawienia zostały utworzone za pomocą okna dialogowego Ustawienia aplikacji Visual Studio w **Edytorze właściwości**, można pobrać domyślny obiekt ustawień wygenerowany dla danego języka za pomocą następującego wyrażenia.

    ```csharp
    Configuration.Settings.Default
    ```

    ```vb
    MySettings.Default
    ```

    —lub—

  - Jeśli jesteś deweloperem Visual Basic i utworzysz ustawienia aplikacji przy użyciu projektanta projektu, możesz pobrać ustawienia za pomocą [obiektu My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).

    —lub—

  - Jeśli ustawienia zostały utworzone przez <xref:System.Configuration.ApplicationSettingsBase> bezpośrednie wypróbowanie, należy ręcznie utworzyć wystąpienie klasy.

    ```csharp
    MyCustomSettings settings = new MyCustomSettings();
    ```

    ```vb
    Dim Settings as New MyCustomSettings()
    ```

Następujące procedury zostały wprowadzone w ramach założenia, że obiekt ustawienia aplikacji został uzyskany przez wypełnienie ostatniego elementu punktowanego w tej procedurze.

### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Aby sprawdzić poprawność ustawień aplikacji w przypadku zmiany ustawienia

1. Jeśli jesteś C# deweloperem, w `Load` zdarzeniu formularza lub kontrolki Dodaj procedurę obsługi <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzeń dla zdarzenia.

    —lub—

    Jeśli jesteś deweloperem Visual Basic, należy zadeklarować `Settings` zmienną `WithEvents` za pomocą słowa kluczowego.

    ```csharp
    public void Form1_Load(Object sender, EventArgs e)
    {
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);
    }
    ```

    ```vb
    Public Sub Form1_Load(sender as Object, e as EventArgs)
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging
    End Sub
    ```

2. Zdefiniuj program obsługi zdarzeń i napisz kod wewnątrz niego, aby przeprowadzić sprawdzanie powiązane z datą urodzenia.

    ```csharp
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)
    {
        if (e.SettingName.Equals("DateOfBirth")) {
            Date newDate = (Date)e.NewValue;
            If (newDate > Date.Now) {
                e.Cancel = true;
                // Inform the user.
            }
        }
    }
    ```

    ```vb
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging
        If (e.SettingName.Equals("DateOfBirth")) Then
            Dim NewDate as Date = CType(e.NewValue, Date)
            If (NewDate > Date.Now) Then
                e.Cancel = True
                ' Inform the user.
            End If
        End If
    End Sub
    ```

### <a name="to-validate-application-settings-when-a-save-occurs"></a>Aby sprawdzić poprawność ustawień aplikacji po wystąpieniu zapisywania

1. W `Load` zdarzeniu formularza lub kontrolki Dodaj procedurę obsługi zdarzeń <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> dla zdarzenia.

    ```csharp
    public void Form1_Load(Object sender, EventArgs e)
    {
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);
    }
    ```

    ```vb
    Public Sub Form1_Load(Sender as Object, e as EventArgs)
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving
    End Sub
    ```

2. Zdefiniuj program obsługi zdarzeń i napisz kod wewnątrz niego, aby przeprowadzić sprawdzanie powiązane z datą urodzenia.

    ```csharp
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)
    {
        if (this["DateOfBirth"] > Date.Now) {
            e.Cancel = true;
        }
    }
    ```

    ```vb
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)
        If (Me["DateOfBirth"] > Date.Now) Then
            e.Cancel = True
        End If
    End Sub
    ```

## <a name="see-also"></a>Zobacz także

- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../creating-event-handlers-in-windows-forms.md)
- [Instrukcje: Utwórz ustawienia aplikacji](how-to-create-application-settings.md)
