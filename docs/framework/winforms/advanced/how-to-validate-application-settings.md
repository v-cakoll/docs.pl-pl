---
title: "Porady: sprawdzanie poprawności ustawień aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 309429c2481bad3a8dff4708d9e2ea8a03057a4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="5e0fc-102">Porady: sprawdzanie poprawności ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="5e0fc-102">How to: Validate Application Settings</span></span>
<span data-ttu-id="5e0fc-103">W tym temacie przedstawiono sposób sprawdzania poprawności ustawień aplikacji przed zostają one zachowane.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>  
  
 <span data-ttu-id="5e0fc-104">Ponieważ ustawienia aplikacji są silnie typizowane, możesz mieć pewność, niektórych użytkowników nie można przypisać danych jest niepoprawnego typu do danego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="5e0fc-105">Jednak użytkownik nadal może próbować przypisać wartości do ustawienia, która wykracza poza granice dopuszczalne — na przykład dostarczanie Data urodzenia, który występuje w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="5e0fc-106"><xref:System.Configuration.ApplicationSettingsBase>, klasy nadrzędnej klasy wszystkie ustawienia aplikacji, opisuje cztery zdarzenia, aby włączyć takie sprawdzanie granic.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="5e0fc-107">Obsługa tych zdarzeń umieszcza kodu sprawdzania poprawności w jednej lokalizacji, a nie rozproszenie go w projekcie.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>  
  
 <span data-ttu-id="5e0fc-108">Zdarzenia, których używasz zależy od gdy trzeba sprawdzić ustawienia, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>  
  
|<span data-ttu-id="5e0fc-109">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="5e0fc-109">Event</span></span>|<span data-ttu-id="5e0fc-110">Wystąpień i użycie</span><span class="sxs-lookup"><span data-stu-id="5e0fc-110">Occurrence and use</span></span>|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="5e0fc-111">Występuje po początkowej podczas ładowania ustawień właściwości grupy.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="5e0fc-112">To zdarzenie służy do sprawdzania poprawności wartości początkowe dla właściwości całej grupy, zanim zostaną użyte w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="5e0fc-113">Występuje, zanim zostanie zmieniona wartość właściwości jednego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="5e0fc-114">To zdarzenie służy do sprawdzania poprawności jednej właściwości, zanim zostanie on zmieniony.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="5e0fc-115">Zapewniają natychmiast uzyskuje opinie użytkowników dotyczące ich działania i dostępnych wyborów.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="5e0fc-116">Występuje po zmianie wartości właściwości jednego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="5e0fc-117">To zdarzenie służy do sprawdzania poprawności jednej właściwości po zmodyfikowaniu.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="5e0fc-118">To zdarzenie jest rzadko używana do sprawdzania poprawności, chyba, że proces sprawdzania poprawności długie, asynchronicznego jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="5e0fc-119">Występuje przed Grupa ustawienia właściwości są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="5e0fc-120">To zdarzenie służy do sprawdzania poprawności wartości dla właściwości całej grupy przed zostają one zachowane na dysku.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|  
  
 <span data-ttu-id="5e0fc-121">Zazwyczaj nie użyjesz wszystkie te zdarzenia w tej samej aplikacji w celach sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="5e0fc-122">Na przykład często jest możliwe do spełnienia wymagań weryfikacji wszystkich dzięki obsłudze tylko <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
 <span data-ttu-id="5e0fc-123">Program obsługi zdarzeń zazwyczaj wykonuje jeden z następujących akcji po wykryciu nieprawidłową wartość:</span><span class="sxs-lookup"><span data-stu-id="5e0fc-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>  
  
-   <span data-ttu-id="5e0fc-124">Automatycznie dostarcza wartość wiadomo, że są prawidłowe, np. wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-124">Automatically supplies a value known to be correct, such as the default value.</span></span>  
  
-   <span data-ttu-id="5e0fc-125">Ponownie wysyła zapytanie użytkownika kod serwera.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-125">Re-queries the user of server code for information.</span></span>  
  
-   <span data-ttu-id="5e0fc-126">Zdarzenia wywoływane przed wykonaniem skojarzonych z nimi działań, takich jak <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, używa <xref:System.ComponentModel.CancelEventArgs> argumentu, aby anulować operację.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>  
  
 <span data-ttu-id="5e0fc-127">Aby uzyskać więcej informacji na temat obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5e0fc-127">For more information about event handling, see [Event Handlers Overview](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="5e0fc-128">Poniższe procedury pokazują, jak przetestować daty urodzenia prawidłowy za pomocą <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> lub <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="5e0fc-129">Procedury zostały napisane przy założeniu, że utworzono już ustawienia aplikacji; w tym przykładzie zostaną wykonane sprawdzanie na ustawienie o nazwie granic `DateOfBirth`.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="5e0fc-130">Aby uzyskać więcej informacji na temat tworzenia ustawień, zobacz [porady: Tworzenie ustawień aplikacji](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5e0fc-130">For more information about creating settings, see [How to: Create Application Settings](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span></span>  
  
### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="5e0fc-131">Aby uzyskać obiekt ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="5e0fc-131">To obtain the application settings object</span></span>  
  
-   <span data-ttu-id="5e0fc-132">Uzyskaj odwołanie do obiektu Ustawienia aplikacji (wystąpienia otoki), wykonując jedną z następujących elementów listy punktowane:</span><span class="sxs-lookup"><span data-stu-id="5e0fc-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>  
  
    -   <span data-ttu-id="5e0fc-133">Jeśli utworzono ustawień za pomocą okna dialogowego Ustawienia aplikacji programu Visual Studio w **Edytor właściwości**, można pobrać obiektu Ustawienia domyślne wygenerowany dla danego języka, za pomocą następującego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         <span data-ttu-id="5e0fc-134">—lub—</span><span class="sxs-lookup"><span data-stu-id="5e0fc-134">-or-</span></span>  
  
    -   <span data-ttu-id="5e0fc-135">Jeśli jesteś deweloperem Visual Basic i tworzenia ustawienia aplikacji przy użyciu narzędzia Projektant projektu, można pobrać ustawienia za pomocą [My.Settings — obiekt](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="5e0fc-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
         <span data-ttu-id="5e0fc-136">—lub—</span><span class="sxs-lookup"><span data-stu-id="5e0fc-136">-or-</span></span>  
  
    -   <span data-ttu-id="5e0fc-137">Jeśli utworzono ustawienia z wynikających z <xref:System.Configuration.ApplicationSettingsBase> bezpośrednio, należy ręcznie utworzyć wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 <span data-ttu-id="5e0fc-138">Poniższe procedury zostały napisane przy założeniu uzyskanego obiekt ustawień aplikacji, wykonując punktowanej ostatniego elementu w tej procedurze.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="5e0fc-139">Aby zweryfikować ustawienia aplikacji, zmieniając ustawienie</span><span class="sxs-lookup"><span data-stu-id="5e0fc-139">To validate Application Settings when a setting is changing</span></span>  
  
1.  <span data-ttu-id="5e0fc-140">Jeśli jesteś C# deweloperów, w tym formularza lub kontrolki `Load` zdarzeń, Dodaj program obsługi zdarzeń dla <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
     <span data-ttu-id="5e0fc-141">—lub—</span><span class="sxs-lookup"><span data-stu-id="5e0fc-141">-or-</span></span>  
  
     <span data-ttu-id="5e0fc-142">Jeśli jesteś deweloperem Visual Basic, należy zadeklarować `Settings` przy użyciu zmiennej `WithEvents` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>  
  
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
  
2.  <span data-ttu-id="5e0fc-143">Definiowanie procedury obsługi zdarzeń i pisanie kodu wewnątrz niej przeprowadzić sprawdzanie na datę urodzenia granic.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="5e0fc-144">Występuje, można sprawdzić poprawności ustawień aplikacji podczas zapisywania</span><span class="sxs-lookup"><span data-stu-id="5e0fc-144">To validate Application Settings when a Save occurs</span></span>  
  
1.  <span data-ttu-id="5e0fc-145">W formularzu lub formantu `Load` zdarzeń, Dodaj program obsługi zdarzeń dla <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>  
  
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
  
2.  <span data-ttu-id="5e0fc-146">Definiowanie procedury obsługi zdarzeń i pisanie kodu wewnątrz niej przeprowadzić sprawdzanie na datę urodzenia granic.</span><span class="sxs-lookup"><span data-stu-id="5e0fc-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5e0fc-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e0fc-147">See Also</span></span>  
 [<span data-ttu-id="5e0fc-148">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5e0fc-148">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="5e0fc-149">Porady: Tworzenie ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="5e0fc-149">How to: Create Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)
