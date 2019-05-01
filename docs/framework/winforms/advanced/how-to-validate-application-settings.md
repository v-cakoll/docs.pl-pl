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
ms.openlocfilehash: b7aba4935756fc218a1fadaa1dd9f20a5bc3034f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778849"
---
# <a name="how-to-validate-application-settings"></a>Instrukcje: Walidacja ustawień aplikacji
W tym temacie pokazano, jak sprawdzanie poprawności ustawień aplikacji, zanim zostaną utrwalone.  
  
 Ponieważ ustawienia aplikacji są silnie typizowane, masz niektóre pewność użytkowników nie można przypisać danych niepoprawny typ danego ustawienia. Jednak użytkownik nadal może podejmować prób do przypisania wartości do ustawienia, która wykracza poza dopuszczalne granice — na przykład, podając datę urodzenia, który występuje w przyszłości. <xref:System.Configuration.ApplicationSettingsBase>, klasą nadrzędną dla wszystkich klas ustawienia aplikacji, udostępnia cztery zdarzeń w celu włączenia takich sprawdzanie granic. Obsługa tych zdarzeń umieszcza wszystkie kod sprawdzania poprawności w jednej lokalizacji, a nie rozproszenie go w całym projekcie.  
  
 Zdarzenie, którego używasz zależy, gdy trzeba sprawdzić poprawność ustawień, zgodnie z opisem w poniższej tabeli.  
  
|Zdarzenie|Wystąpień i użycie|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|Występuje po początkowym załadowaniu grupy właściwości ustawień.<br /><br /> To zdarzenie służy do sprawdzania poprawności wartości początkowe dla grupy całej właściwości, zanim zostaną użyte w aplikacji.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|Występuje, zanim zostanie zmieniona wartość właściwości jednego ustawienia.<br /><br /> To zdarzenie służy do sprawdzania poprawności jedną właściwość, zanim zostanie on zmieniony. Jego jest udostępnienie natychmiastowej opinii do użytkowników w zakresie ich działania i opcje.|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|Występuje po zmianie wartości właściwości jednego ustawienia.<br /><br /> To zdarzenie służy do sprawdzania poprawności pojedynczej właściwości po zmodyfikowaniu. To zdarzenie jest rzadko używana do sprawdzania poprawności, chyba że proces sprawdzania poprawności długie, asynchronicznego jest wymagana.|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|Występuje, zanim grupy właściwości ustawienia są przechowywane.<br /><br /> To zdarzenie służy do sprawdzania poprawności wartości dla właściwości całej grupy, zanim zostaną utrwalone na dysku.|  
  
 Zazwyczaj użytkownik nie będzie używać wszystkich tych zdarzeń w ramach tej samej aplikacji do celów sprawdzania poprawności. Na przykład często jest to możliwe spełnić wszystkie wymagania weryfikacji dzięki obsłudze tylko <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzeń.  
  
 Program obsługi zdarzeń zazwyczaj wykonuje jedną z następujących czynności w przypadku wykrycia nieprawidłową wartość:  
  
- Automatycznie dostarczy wartość wiadomo, że są poprawne, np. wartością domyślną.  
  
- Ponownie wysyła zapytanie do użytkownika o kodzie serwera, aby uzyskać informacje.  
  
- Zdarzenia wywoływane przed wykonaniem skojarzonych z nimi działań, takich jak <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> i <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, używa <xref:System.ComponentModel.CancelEventArgs> argumentu, aby anulować operację.  
  
 Aby uzyskać więcej informacji na temat obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../event-handlers-overview-windows-forms.md).  
  
 Poniższe procedury pokazują, jak testować prawidłową datę urodzenia za pomocą <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> lub <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> zdarzeń. Procedury przedstawione zostały napisane przy założeniu, że utworzono już ustawienia aplikacji; w tym przykładzie zostaną wykonane sprawdzanie ustawienie o nazwie granic `DateOfBirth`. Aby uzyskać więcej informacji na temat tworzenia ustawień, zobacz [jak: Tworzenie ustawień aplikacji](how-to-create-application-settings.md).  
  
### <a name="to-obtain-the-application-settings-object"></a>Aby uzyskać obiekt ustawień aplikacji  
  
- Uzyskaj odwołanie do obiektu ustawień aplikacji (wystąpienia otoki), wykonując jedną z następujących elementów punktowanej:  
  
    - Jeśli utworzono ustawień za pomocą okna dialogowego Ustawienia aplikacji programu Visual Studio w **Edytor właściwości**, mogą pobrać obiekt ustawienia domyślne, które są generowane dla języka przy użyciu następującego wyrażenia.  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         —lub—  
  
    - Jeśli jesteś programistą języka Visual Basic i utworzyć ustawienia aplikacji przy użyciu projektanta projektu, można pobrać ustawienia za pomocą [My.Settings — obiekt](~/docs/visual-basic/language-reference/objects/my-settings-object.md).  
  
         —lub—  
  
    - W przypadku utworzenia ustawień przy pochodząca od <xref:System.Configuration.ApplicationSettingsBase> bezpośrednio, należy ręcznie utworzyć wystąpienia klasy.  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 Poniższe procedury zostały napisane w obszarze przy założeniu, że obiekt ustawień aplikacji uzyskano, wykonując ostatni element listy w tej procedurze.  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>Aby zweryfikować ustawienia aplikacji, zmieniając ustawienie  
  
1. Jeśli jesteś C# dla deweloperów w formularza lub formantu `Load` zdarzeń, Dodaj program obsługi zdarzeń dla <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> zdarzeń.  
  
     —lub—  
  
     Jeśli jesteś programistą języka Visual Basic, należy zadeklarować `Settings` przy użyciu zmiennej `WithEvents` — słowo kluczowe.  
  
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
  
2. Definiowanie procedury obsługi zdarzeń, a następnie napisać kod wewnątrz niej, aby wykonać sprawdzanie na datę urodzenia granic.  
  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a>Występuje, aby zweryfikować ustawienia aplikacji, podczas zapisywania  
  
1. W formularzu lub kontrolki `Load` zdarzeń, Dodaj program obsługi zdarzeń dla <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> zdarzeń.  
  
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
  
2. Definiowanie procedury obsługi zdarzeń, a następnie napisać kod wewnątrz niej, aby wykonać sprawdzanie na datę urodzenia granic.  
  
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
- [Instrukcje: Tworzenie ustawień aplikacji](how-to-create-application-settings.md)
