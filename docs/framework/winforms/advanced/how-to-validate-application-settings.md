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
# <a name="how-to-validate-application-settings"></a>Porady: sprawdzanie poprawności ustawień aplikacji
W tym temacie przedstawiono sposób sprawdzania poprawności ustawień aplikacji przed zostają one zachowane.  
  
 Ponieważ ustawienia aplikacji są silnie typizowane, możesz mieć pewność, niektórych użytkowników nie można przypisać danych jest niepoprawnego typu do danego ustawienia. Jednak użytkownik nadal może próbować przypisać wartości do ustawienia, która wykracza poza granice dopuszczalne — na przykład dostarczanie Data urodzenia, który występuje w przyszłości. <xref:System.Configuration.ApplicationSettingsBase>, klasy nadrzędnej klasy wszystkie ustawienia aplikacji, opisuje cztery zdarzenia, aby włączyć takie sprawdzanie granic. Obsługa tych zdarzeń umieszcza kodu sprawdzania poprawności w jednej lokalizacji, a nie rozproszenie go w projekcie.  
  
 Zdarzenia, których używasz zależy od gdy trzeba sprawdzić ustawienia, zgodnie z opisem w poniższej tabeli.  
  
|Zdarzenie|Wystąpień i użycie|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Występuje po początkowej podczas ładowania ustawień właściwości grupy.<br /><br /> To zdarzenie służy do sprawdzania poprawności wartości początkowe dla właściwości całej grupy, zanim zostaną użyte w aplikacji.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Występuje, zanim zostanie zmieniona wartość właściwości jednego ustawienia.<br /><br /> To zdarzenie służy do sprawdzania poprawności jednej właściwości, zanim zostanie on zmieniony. Zapewniają natychmiast uzyskuje opinie użytkowników dotyczące ich działania i dostępnych wyborów.|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Występuje po zmianie wartości właściwości jednego ustawienia.<br /><br /> To zdarzenie służy do sprawdzania poprawności jednej właściwości po zmodyfikowaniu. To zdarzenie jest rzadko używana do sprawdzania poprawności, chyba, że proces sprawdzania poprawności długie, asynchronicznego jest wymagana.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Występuje przed Grupa ustawienia właściwości są przechowywane.<br /><br /> To zdarzenie służy do sprawdzania poprawności wartości dla właściwości całej grupy przed zostają one zachowane na dysku.|  
  
 Zazwyczaj nie użyjesz wszystkie te zdarzenia w tej samej aplikacji w celach sprawdzania poprawności. Na przykład często jest możliwe do spełnienia wymagań weryfikacji wszystkich dzięki obsłudze tylko <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzeń.  
  
 Program obsługi zdarzeń zazwyczaj wykonuje jeden z następujących akcji po wykryciu nieprawidłową wartość:  
  
-   Automatycznie dostarcza wartość wiadomo, że są prawidłowe, np. wartość domyślna.  
  
-   Ponownie wysyła zapytanie użytkownika kod serwera.  
  
-   Zdarzenia wywoływane przed wykonaniem skojarzonych z nimi działań, takich jak <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, używa <xref:System.ComponentModel.CancelEventArgs> argumentu, aby anulować operację.  
  
 Aby uzyskać więcej informacji na temat obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Poniższe procedury pokazują, jak przetestować daty urodzenia prawidłowy za pomocą <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> lub <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> zdarzeń. Procedury zostały napisane przy założeniu, że utworzono już ustawienia aplikacji; w tym przykładzie zostaną wykonane sprawdzanie na ustawienie o nazwie granic `DateOfBirth`. Aby uzyskać więcej informacji na temat tworzenia ustawień, zobacz [porady: Tworzenie ustawień aplikacji](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
### <a name="to-obtain-the-application-settings-object"></a>Aby uzyskać obiekt ustawień aplikacji  
  
-   Uzyskaj odwołanie do obiektu Ustawienia aplikacji (wystąpienia otoki), wykonując jedną z następujących elementów listy punktowane:  
  
    -   Jeśli utworzono ustawień za pomocą okna dialogowego Ustawienia aplikacji programu Visual Studio w **Edytor właściwości**, można pobrać obiektu Ustawienia domyślne wygenerowany dla danego języka, za pomocą następującego wyrażenia.  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         —lub—  
  
    -   Jeśli jesteś deweloperem Visual Basic i tworzenia ustawienia aplikacji przy użyciu narzędzia Projektant projektu, można pobrać ustawienia za pomocą [My.Settings — obiekt](~/docs/visual-basic/language-reference/objects/my-settings-object.md).  
  
         —lub—  
  
    -   Jeśli utworzono ustawienia z wynikających z <xref:System.Configuration.ApplicationSettingsBase> bezpośrednio, należy ręcznie utworzyć wystąpienia klasy.  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 Poniższe procedury zostały napisane przy założeniu uzyskanego obiekt ustawień aplikacji, wykonując punktowanej ostatniego elementu w tej procedurze.  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Aby zweryfikować ustawienia aplikacji, zmieniając ustawienie  
  
1.  Jeśli jesteś C# deweloperów, w tym formularza lub kontrolki `Load` zdarzeń, Dodaj program obsługi zdarzeń dla <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzeń.  
  
     —lub—  
  
     Jeśli jesteś deweloperem Visual Basic, należy zadeklarować `Settings` przy użyciu zmiennej `WithEvents` — słowo kluczowe.  
  
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
  
2.  Definiowanie procedury obsługi zdarzeń i pisanie kodu wewnątrz niej przeprowadzić sprawdzanie na datę urodzenia granic.  
  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a>Występuje, można sprawdzić poprawności ustawień aplikacji podczas zapisywania  
  
1.  W formularzu lub formantu `Load` zdarzeń, Dodaj program obsługi zdarzeń dla <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> zdarzeń.  
  
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
  
2.  Definiowanie procedury obsługi zdarzeń i pisanie kodu wewnątrz niej przeprowadzić sprawdzanie na datę urodzenia granic.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Porady: Tworzenie ustawień aplikacji](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)
