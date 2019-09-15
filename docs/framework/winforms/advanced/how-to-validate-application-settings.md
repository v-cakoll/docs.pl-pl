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
ms.openlocfilehash: b3b2447b570f0635942183dcc62c0e4ed73800d1
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972245"
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="a3973-102">Instrukcje: Walidacja ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="a3973-102">How to: Validate Application Settings</span></span>

<span data-ttu-id="a3973-103">W tym temacie przedstawiono sposób sprawdzania poprawności ustawień aplikacji przed ich utrwaleniem.</span><span class="sxs-lookup"><span data-stu-id="a3973-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>

<span data-ttu-id="a3973-104">Ponieważ ustawienia aplikacji mają silną wartość, masz pewność, że użytkownicy nie mogą przypisywać danych nieprawidłowego typu do danego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a3973-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="a3973-105">Jednak użytkownik nadal może próbować przypisać wartość do ustawienia, które wykracza poza akceptowalne granice — na przykład dostarczając datę urodzenia, która występuje w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="a3973-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="a3973-106"><xref:System.Configuration.ApplicationSettingsBase>, Klasa nadrzędna wszystkich klas ustawień aplikacji udostępnia cztery zdarzenia umożliwiające sprawdzenie takich powiązań.</span><span class="sxs-lookup"><span data-stu-id="a3973-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="a3973-107">Obsługa tych zdarzeń umieszcza cały kod weryfikacyjny w jednej lokalizacji, zamiast rozpraszać go w całym projekcie.</span><span class="sxs-lookup"><span data-stu-id="a3973-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>

<span data-ttu-id="a3973-108">Używane zdarzenie zależy od tego, kiedy trzeba zweryfikować ustawienia, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a3973-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>

|<span data-ttu-id="a3973-109">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a3973-109">Event</span></span>|<span data-ttu-id="a3973-110">Wystąpienie i użycie</span><span class="sxs-lookup"><span data-stu-id="a3973-110">Occurrence and use</span></span>|
|-----------|------------------------|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="a3973-111">Występuje po początkowym załadowaniu grupy właściwości ustawień.</span><span class="sxs-lookup"><span data-stu-id="a3973-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="a3973-112">To zdarzenie służy do sprawdzania poprawności wartości początkowych dla całej grupy właściwości, zanim zostaną one użyte w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3973-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="a3973-113">Występuje przed zmianą wartości właściwości Single Settings.</span><span class="sxs-lookup"><span data-stu-id="a3973-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="a3973-114">Użyj tego zdarzenia, aby sprawdzić poprawność pojedynczej właściwości przed jej zmianą.</span><span class="sxs-lookup"><span data-stu-id="a3973-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="a3973-115">Może ona udostępniać użytkownikom natychmiastową opinię dotyczącą ich działań i wyborów.</span><span class="sxs-lookup"><span data-stu-id="a3973-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="a3973-116">Występuje po zmianie wartości właściwości Single Settings.</span><span class="sxs-lookup"><span data-stu-id="a3973-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="a3973-117">To zdarzenie służy do sprawdzania poprawności pojedynczej właściwości po jej zmianie.</span><span class="sxs-lookup"><span data-stu-id="a3973-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="a3973-118">To zdarzenie jest rzadko używane do sprawdzania poprawności, chyba że jest wymagany proces asynchronicznej walidacji.</span><span class="sxs-lookup"><span data-stu-id="a3973-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="a3973-119">Występuje przed zapisaniem grupy właściwości ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a3973-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="a3973-120">To zdarzenie służy do sprawdzania poprawności wartości dla całej grupy właściwości, zanim zostaną one utrwalone na dysku.</span><span class="sxs-lookup"><span data-stu-id="a3973-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|

<span data-ttu-id="a3973-121">Zwykle nie będzie można używać wszystkich tych zdarzeń w ramach tej samej aplikacji na potrzeby sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="a3973-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="a3973-122">Na przykład często istnieje możliwość spełnienia wszystkich wymagań związanych z walidacją przez obsługę tylko <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3973-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>

<span data-ttu-id="a3973-123">Program obsługi zdarzeń zazwyczaj wykonuje jedną z następujących akcji po wykryciu nieprawidłowej wartości:</span><span class="sxs-lookup"><span data-stu-id="a3973-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>

- <span data-ttu-id="a3973-124">Automatycznie dostarcza wartość znaną do poprawnego, na przykład wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="a3973-124">Automatically supplies a value known to be correct, such as the default value.</span></span>

- <span data-ttu-id="a3973-125">Umożliwia ponowne zazapytanie użytkownika kodu serwera o informacje.</span><span class="sxs-lookup"><span data-stu-id="a3973-125">Re-queries the user of server code for information.</span></span>

- <span data-ttu-id="a3973-126">Dla zdarzeń wywoływanych przed skojarzonych z nimi akcjami <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> , <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>takimi jak <xref:System.ComponentModel.CancelEventArgs> i, używa argumentu, aby anulować operację.</span><span class="sxs-lookup"><span data-stu-id="a3973-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>

<span data-ttu-id="a3973-127">Aby uzyskać więcej informacji na temat obsługi zdarzeń, zobacz [Omówienie obsługi zdarzeń](../event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a3973-127">For more information about event handling, see [Event Handlers Overview](../event-handlers-overview-windows-forms.md).</span></span>

<span data-ttu-id="a3973-128">W poniższych procedurach pokazano, jak sprawdzić poprawność daty urodzenia przy <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> użyciu <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> albo zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3973-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="a3973-129">Procedury zostały utworzone w ramach założeń, w których utworzono już ustawienia aplikacji; w tym przykładzie wykonamy sprawdzanie granic dla ustawienia o nazwie `DateOfBirth`.</span><span class="sxs-lookup"><span data-stu-id="a3973-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="a3973-130">Aby uzyskać więcej informacji na temat tworzenia ustawień [, zobacz How to: Utwórz ustawienia](how-to-create-application-settings.md)aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3973-130">For more information about creating settings, see [How to: Create Application Settings](how-to-create-application-settings.md).</span></span>

### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="a3973-131">Aby uzyskać obiekt ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="a3973-131">To obtain the application settings object</span></span>

- <span data-ttu-id="a3973-132">Uzyskaj odwołanie do obiektu ustawień aplikacji (wystąpienie otoki), wykonując jedną z następujących pozycji:</span><span class="sxs-lookup"><span data-stu-id="a3973-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>

  - <span data-ttu-id="a3973-133">Jeśli ustawienia zostały utworzone za pomocą okna dialogowego Ustawienia aplikacji Visual Studio w **Edytorze właściwości**, można pobrać domyślny obiekt ustawień wygenerowany dla danego języka za pomocą następującego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a3973-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>

    ```csharp
    Configuration.Settings.Default
    ```

    ```vb
    MySettings.Default
    ```

    <span data-ttu-id="a3973-134">—lub—</span><span class="sxs-lookup"><span data-stu-id="a3973-134">-or-</span></span>

  - <span data-ttu-id="a3973-135">Jeśli jesteś deweloperem Visual Basic i utworzysz ustawienia aplikacji przy użyciu projektanta projektu, możesz pobrać ustawienia za pomocą [obiektu My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="a3973-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>

    <span data-ttu-id="a3973-136">—lub—</span><span class="sxs-lookup"><span data-stu-id="a3973-136">-or-</span></span>

  - <span data-ttu-id="a3973-137">Jeśli ustawienia zostały utworzone przez <xref:System.Configuration.ApplicationSettingsBase> bezpośrednie wypróbowanie, należy ręcznie utworzyć wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="a3973-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>

    ```csharp
    MyCustomSettings settings = new MyCustomSettings();
    ```

    ```vb
    Dim Settings as New MyCustomSettings()
    ```

<span data-ttu-id="a3973-138">Następujące procedury zostały wprowadzone w ramach założenia, że obiekt ustawienia aplikacji został uzyskany przez wypełnienie ostatniego elementu punktowanego w tej procedurze.</span><span class="sxs-lookup"><span data-stu-id="a3973-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>

### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="a3973-139">Aby sprawdzić poprawność ustawień aplikacji w przypadku zmiany ustawienia</span><span class="sxs-lookup"><span data-stu-id="a3973-139">To validate Application Settings when a setting is changing</span></span>

1. <span data-ttu-id="a3973-140">Jeśli jesteś C# deweloperem, w `Load` zdarzeniu formularza lub kontrolki Dodaj procedurę obsługi <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzeń dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3973-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>

    <span data-ttu-id="a3973-141">—lub—</span><span class="sxs-lookup"><span data-stu-id="a3973-141">-or-</span></span>

    <span data-ttu-id="a3973-142">Jeśli jesteś deweloperem Visual Basic, należy zadeklarować `Settings` zmienną `WithEvents` za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="a3973-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>

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

2. <span data-ttu-id="a3973-143">Zdefiniuj program obsługi zdarzeń i napisz kod wewnątrz niego, aby przeprowadzić sprawdzanie powiązane z datą urodzenia.</span><span class="sxs-lookup"><span data-stu-id="a3973-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>

    ```csharp
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)
    {
        if (e.SettingName.Equals("DateOfBirth"))
        {
            var newDate = (DateTime)e.NewValue;
            if (newDate > DateTime.Now)
            {
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

### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="a3973-144">Aby sprawdzić poprawność ustawień aplikacji po wystąpieniu zapisywania</span><span class="sxs-lookup"><span data-stu-id="a3973-144">To validate Application Settings when a Save occurs</span></span>

1. <span data-ttu-id="a3973-145">W `Load` zdarzeniu formularza lub kontrolki Dodaj procedurę obsługi zdarzeń <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3973-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>

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

2. <span data-ttu-id="a3973-146">Zdefiniuj program obsługi zdarzeń i napisz kod wewnątrz niego, aby przeprowadzić sprawdzanie powiązane z datą urodzenia.</span><span class="sxs-lookup"><span data-stu-id="a3973-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a3973-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3973-147">See also</span></span>

- [<span data-ttu-id="a3973-148">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a3973-148">Creating Event Handlers in Windows Forms</span></span>](../creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="a3973-149">Instrukcje: Utwórz ustawienia aplikacji</span><span class="sxs-lookup"><span data-stu-id="a3973-149">How to: Create Application Settings</span></span>](how-to-create-application-settings.md)
