---
title: Architektura ustawień aplikacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 078b5f3fc1cd4273af282580f41e68ca9bd8ff51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182626"
---
# <a name="application-settings-architecture"></a>Architektura ustawień aplikacji
W tym temacie opisano, jak działa architektura Ustawień aplikacji i eksploruje zaawansowane funkcje architektury, takie jak zgrupowane ustawienia i klucze ustawień.

 Architektura ustawień aplikacji obsługuje definiowanie silnie wpisanych ustawień za pomocą aplikacji lub zakresu użytkownika i utrwalanie ustawień między sesjami aplikacji. Architektura zapewnia domyślny aparat trwałości do zapisywania ustawień i ładowania ich z lokalnego systemu plików. Architektura definiuje również interfejsy do dostarczania aparatu trwałości niestandardowe.

 Interfejsy są dostarczane, które umożliwiają składniki niestandardowe do utrwalenia własnych ustawień, gdy są one hostowane w aplikacji. Za pomocą klawiszy ustawień, składniki mogą zachować ustawienia dla wielu wystąpień składnika oddzielne.

## <a name="defining-settings"></a>Definiowanie ustawień
 Architektura ustawień aplikacji jest używana zarówno w ASP.NET, jak i windows forms i zawiera wiele klas podstawowych, które są współużytkowane w obu środowiskach. Najważniejsze jest <xref:System.Configuration.SettingsBase>, który zapewnia dostęp do ustawień za pośrednictwem kolekcji i zapewnia niski poziom metod ładowania i zapisywania ustawień. Każde środowisko implementuje własną klasę <xref:System.Configuration.SettingsBase> pochodną, aby zapewnić dodatkowe funkcje ustawień dla tego środowiska. W aplikacji opartej na formularzach systemu Windows wszystkie ustawienia aplikacji <xref:System.Configuration.ApplicationSettingsBase> muszą być zdefiniowane w klasie pochodzącej z klasy, która dodaje następujące funkcje do klasy podstawowej:

- Operacje ładowania i zapisywania wyższego poziomu

- Obsługa ustawień o zakresie użytkownika

- Przywracanie ustawień użytkownika do wstępnie zdefiniowanych ustawień domyślnych

- Uaktualnianie ustawień z poprzedniej wersji aplikacji

- Sprawdzanie poprawności ustawień przed ich zmianą lub przed zapisaniem

 Ustawienia można opisać przy użyciu liczby atrybutów <xref:System.Configuration> zdefiniowanych w obszarze nazw; są one opisane w [atrybutach ustawień aplikacji](application-settings-attributes.md). Podczas definiowania ustawienia należy zastosować je <xref:System.Configuration.ApplicationScopedSettingAttribute> z <xref:System.Configuration.UserScopedSettingAttribute>jednym z nich lub , który opisuje, czy ustawienie ma zastosowanie do całej aplikacji, czy tylko do bieżącego użytkownika.

 Poniższy przykład kodu definiuje klasę ustawień niestandardowych `BackgroundColor`z jednym ustawieniem.

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Trwałość ustawień
 Klasa <xref:System.Configuration.ApplicationSettingsBase> sama nie utrwala lub nie ładuje ustawień; to zadanie należy do dostawcy ustawień, klasy, która wywodzi się z <xref:System.Configuration.SettingsProvider>. Jeśli klasa <xref:System.Configuration.ApplicationSettingsBase> pochodna nie określa dostawcy ustawień <xref:System.Configuration.SettingsProviderAttribute>za pośrednictwem , <xref:System.Configuration.LocalFileSettingsProvider>a następnie domyślnego dostawcy, jest używany.

 System konfiguracji, który został pierwotnie wydany z programem .NET Framework obsługuje dostarczanie danych konfiguracji aplikacji statycznych `app.`za pośrednictwem pliku machine.config komputera lokalnego lub w pliku exe.config, który można wdrożyć z aplikacją. Klasa <xref:System.Configuration.LocalFileSettingsProvider> rozszerza tę natywną obsługę w następujący sposób:

- Ustawienia o zakresie aplikacji mogą być przechowywane w plikach machine.config lub `app.`exe.config. Plik Machine.config jest zawsze `app`tylko do odczytu, podczas gdy plik .exe.config jest ograniczony przez zagadnienia dotyczące zabezpieczeń do tylko do odczytu dla większości aplikacji.

- Ustawienia o zakresie użytkownika mogą `app`być przechowywane w plikach .exe.config, w którym to przypadku są traktowane jako statyczne ustawienia domyślne.

- Ustawienia o zakresie użytkownika nieobe domyślnie są przechowywane w nowym pliku *user*.config, gdzie *użytkownik* jest nazwą użytkownika osoby aktualnie wykonującej aplikację. Można określić ustawienie domyślne dla ustawienia <xref:System.Configuration.DefaultSettingValueAttribute>o zakresie użytkownika za pomocą pliku . Ponieważ ustawienia o zakresie użytkownika często `user`zmieniają się podczas wykonywania aplikacji, .config jest zawsze odczyt/zapis.

 Wszystkie trzy pliki konfiguracyjne przechowują ustawienia w formacie XML. Element XML najwyższego poziomu dla ustawień `<appSettings>`o `<userSettings>` zakresie aplikacji jest , podczas gdy jest używany do ustawień o zakresie użytkownika. Plik `app`.exe.config zawierający zarówno ustawienia o zakresie aplikacji, jak i ustawienia domyślne dla ustawień o zakresie użytkownika wygląda następująco:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
        </sectionGroup>
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
        </sectionGroup>
    </configSections>
    <applicationSettings>
        <WindowsApplication1.Properties.Settings>
            <setting name="Cursor" serializeAs="String">
                <value>Default</value>
            </setting>
            <setting name="DoubleBuffering" serializeAs="String">
                <value>False</value>
            </setting>
        </WindowsApplication1.Properties.Settings>
    </applicationSettings>
    <userSettings>
        <WindowsApplication1.Properties.Settings>
            <setting name="FormTitle" serializeAs="String">
                <value>Form1</value>
            </setting>
            <setting name="FormSize" serializeAs="String">
                <value>595, 536</value>
            </setting>
        </WindowsApplication1.Properties.Settings>
    </userSettings>
</configuration>
```

 Aby uzyskać definicję elementów w sekcji ustawień aplikacji pliku konfiguracyjnego, zobacz [Schemat ustawień aplikacji](../../configure-apps/file-schema/application-settings-schema.md).

### <a name="settings-bindings"></a>Powiązania ustawień
 Ustawienia aplikacji używają architektury wiązania danych formularzy systemu Windows, aby zapewnić dwukierunkową komunikację aktualizacji ustawień między obiektem ustawień i składnikami. Jeśli używasz programu Visual Studio do tworzenia ustawień aplikacji i przypisywania ich do właściwości składnika, te powiązania są generowane automatycznie.

 Ustawienie aplikacji można powiązać tylko ze <xref:System.Windows.Forms.IBindableComponent> składnikiem obsługującym interfejs. Ponadto składnik musi implementować zdarzenie zmiany dla określonej właściwości powiązanej lub powiadamiać ustawienia aplikacji, że właściwość została zmieniona <xref:System.ComponentModel.INotifyPropertyChanged> za pośrednictwem interfejsu. Jeśli składnik nie <xref:System.Windows.Forms.IBindableComponent> implementuje i są wiążące za pośrednictwem programu Visual Studio, właściwości powiązane zostaną ustawione po raz pierwszy, ale nie zostanie zaktualizowany. Jeśli składnik implementuje, <xref:System.Windows.Forms.IBindableComponent> ale nie obsługuje powiadomień o zmianie właściwości, powiązanie nie zostanie zaktualizowane w pliku ustawień po zmianie właściwości.

 Niektóre składniki formularzy <xref:System.Windows.Forms.ToolStripItem>systemu Windows, takie jak , nie obsługują powiązań ustawień.

### <a name="settings-serialization"></a>Ustawienia Serializacji
 Gdy <xref:System.Configuration.LocalFileSettingsProvider> należy zapisać ustawienia na dysku, wykonuje następujące akcje:

1. Używa odbicia, aby zbadać wszystkie właściwości <xref:System.Configuration.ApplicationSettingsBase> zdefiniowane w klasie pochodnej, znajdując <xref:System.Configuration.ApplicationScopedSettingAttribute> te, które są stosowane z jedną lub <xref:System.Configuration.UserScopedSettingAttribute>.

2. Serializuje właściwość na dysku. Najpierw próbuje wywołać <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> lub na typ skojarzony <xref:System.ComponentModel.TypeConverter>. Jeśli to się nie powiedzie, używa serializacji XML zamiast tego.

3. Określa, które ustawienia są w których plikach, na podstawie atrybutu ustawienia.

 Jeśli zaimplementujesz własną klasę <xref:System.Configuration.SettingsSerializeAsAttribute> ustawień, można użyć, aby oznaczyć <xref:System.Configuration.SettingsSerializeAs> ustawienie dla serializacji binarnej lub niestandardowej przy użyciu wyliczenia. Aby uzyskać więcej informacji na temat tworzenia własnej klasy ustawień w kodzie, zobacz [Jak: Tworzenie ustawień aplikacji](how-to-create-application-settings.md).

### <a name="settings-file-locations"></a>Ustawienia lokalizacje plików
 Lokalizacja plików `app`.exe.config i *user*.config będzie się różnić w zależności od sposobu zainstalowania aplikacji. W przypadku aplikacji opartej na formularzach `app`systemu Windows skopiowanej na komputer lokalny plik .exe.config będzie rezydować w tym samym katalogu co podstawowy katalog <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> głównego pliku wykonywalnego aplikacji, a *użytkownik*.config będzie rezydować w lokalizacji określonej przez właściwość. Dla aplikacji zainstalowanej za pomocą ClickOnce oba te pliki będą znajdowały się w katalogu danych ClickOnce\\pod %InstallRoot%\Documents and Settings*username*\Local Settings.

 Lokalizacja przechowywania tych plików jest nieco inna, jeśli użytkownik włączył profile mobilne, co umożliwia użytkownikowi definiowanie różnych ustawień systemu Windows i aplikacji, gdy korzysta z innych komputerów w domenie. W takim przypadku zarówno aplikacje ClickOnce, jak i `app`aplikacje inne niż ClickOnce będą miały swoje pliki .exe.config i *user*.config przechowywane w obszarze %InstallRoot%\Documents and Settings\\*username*\Application Data.

 Aby uzyskać więcej informacji o tym, jak funkcja Ustawienia aplikacji działa z nową technologią wdrażania, zobacz [ClickOnce i Ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings). Aby uzyskać więcej informacji na temat katalogu danych ClickOnce, zobacz [Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).

## <a name="application-settings-and-security"></a>Ustawienia aplikacji i zabezpieczenia
 Ustawienia aplikacji są przeznaczone do pracy w częściowym zaufaniu, ograniczonym środowisku, które jest domyślnym dla aplikacji Windows Forms hostowanych przez Internet lub intranet. Żadne specjalne uprawnienia poza częściowym zaufaniem nie są potrzebne do używania ustawień aplikacji z dostawcą ustawień domyślnych.

 Gdy ustawienia aplikacji są używane w aplikacji `user`ClickOnce, plik .config jest przechowywany w katalogu danych ClickOnce. Rozmiar pliku `user`.config aplikacji nie może przekraczać przydziału katalogu danych ustawionego przez ClickOnce. Aby uzyskać więcej informacji, zobacz [ClickOnce i Ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings).

## <a name="custom-settings-providers"></a>Dostawcy ustawień niestandardowych
 W architekturze Ustawienia aplikacji istnieje luźne sprzężenie między klasą <xref:System.Configuration.ApplicationSettingsBase>otoki ustawień aplikacji, pochodzącą <xref:System.Configuration.SettingsProvider>od programu , a skojarzonym dostawcą lub dostawcami ustawień, pochodzącymi z . To skojarzenie jest <xref:System.Configuration.SettingsProviderAttribute> definiowane tylko przez zastosowane do klasy otoki lub jej indywidualne właściwości. Jeśli dostawca ustawień nie jest jawnie określony, używany jest dostawca domyślny. <xref:System.Configuration.LocalFileSettingsProvider> W rezultacie ta architektura obsługuje tworzenie i używanie dostawców ustawień niestandardowych.

 Załóżmy na przykład, że `SqlSettingsProvider`chcesz opracować i używać dostawcy, który będzie przechowywać wszystkie dane ustawień w bazie danych programu Microsoft SQL Server. Klasa <xref:System.Configuration.SettingsProvider>pochodna otrzyma te informacje `Initialize` w swojej metodzie <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>jako parametr typu . Następnie należy zaimplementować <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> metodę pobierania ustawień z <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> magazynu danych i zapisywania ich. Dostawca może użyć <xref:System.Configuration.SettingsPropertyCollection> dostarczone <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> do określenia nazwy właściwości, typu i zakresu, a także inne atrybuty ustawień zdefiniowane dla tej właściwości.

 Dostawca będzie musiał zaimplementować jedną właściwość i jedną metodę, której implementacje mogą nie być oczywiste. Właściwość <xref:System.Configuration.SettingsProvider.ApplicationName%2A> jest abstrakcyjną <xref:System.Configuration.SettingsProvider>właściwością ; należy zaprogramować go, aby zwrócić następujące elementy:

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Klasa pochodna musi również `Initialize` implementować metodę, która nie przyjmuje żadnych argumentów i zwraca wartość. Ta metoda nie <xref:System.Configuration.SettingsProvider>jest zdefiniowana przez .

 Na koniec zaimplementować <xref:System.Configuration.IApplicationSettingsProvider> na dostawcy, aby zapewnić obsługę odświeżania ustawień, przywracanie ustawień do ich ustawień domyślnych i uaktualnianie ustawień z jednej wersji aplikacji do innej.

 Po zaimplementowaniu i skompilowaniu dostawcy należy poinstruować klasę ustawień, aby używała tego dostawcy zamiast wartości domyślnej. Można to osiągnąć <xref:System.Configuration.SettingsProviderAttribute>poprzez . Jeśli zastosowano do całej klasy ustawień, dostawca jest używany dla każdego ustawienia, które definiuje klasa; jeśli są stosowane do poszczególnych ustawień, architektura Ustawienia aplikacji używa <xref:System.Configuration.LocalFileSettingsProvider> tego dostawcy tylko dla tych ustawień i używa dla pozostałych. Poniższy przykład kodu pokazuje, jak poinstruować klasy ustawień, aby użyć dostawcy niestandardowego.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Dostawca może być wywoływany z wielu wątków jednocześnie, ale zawsze będzie zapisywać w tej samej lokalizacji magazynu; w związku z tym architektura ustawienia aplikacji będzie tylko kiedykolwiek utworzyć wystąpienie pojedynczego wystąpienia klasy dostawcy.

> [!IMPORTANT]
> Należy upewnić się, że dostawca jest bezpieczny dla wątków i umożliwia tylko jeden wątek naraz do zapisu do plików konfiguracyjnych.

 Dostawca nie musi obsługiwać wszystkich atrybutów ustawień <xref:System.Configuration?displayProperty=nameWithType> zdefiniowanych w obszarze nazw, <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute>chociaż musi on <xref:System.Configuration.DefaultSettingValueAttribute>mieć minimalne wsparcie i , a także powinien obsługiwać. Dla tych atrybutów, które nie obsługuje, dostawca powinien po prostu nie bez powiadomienia; nie należy zgłaszać wyjątek. Jeśli klasa ustawień używa nieprawidłowej kombinacji atrybutów, jednak <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute> — takie jak stosowanie i do tego samego ustawienia — dostawca powinien zgłosić wyjątek i zaprzestać działania.

## <a name="see-also"></a>Zobacz też

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Przegląd ustawień aplikacji](application-settings-overview.md)
- [Ustawienia aplikacji dotyczące kontrolek niestandardowych](application-settings-for-custom-controls.md)
- [ClickOnce i ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings)
- [Schemat ustawień aplikacji](../../configure-apps/file-schema/application-settings-schema.md)
