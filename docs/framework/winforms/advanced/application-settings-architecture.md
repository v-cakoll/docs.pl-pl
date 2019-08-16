---
title: Architektura ustawień aplikacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: b5d5a4456bef925cd8093fe9c696145aff83660e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039417"
---
# <a name="application-settings-architecture"></a>Architektura ustawień aplikacji
W tym temacie opisano sposób działania architektury ustawień aplikacji oraz omówiono zaawansowane funkcje architektury, takie jak pogrupowane ustawienia i klucze ustawień.

 Architektura ustawień aplikacji obsługuje definiowanie ustawień o jednoznacznie określonym typie przy użyciu aplikacji lub zakresu użytkownika i utrwalanie ustawień między sesjami aplikacji. Architektura zapewnia domyślny aparat trwałości do zapisywania ustawień i ładowania ich z lokalnego systemu plików. Architektura definiuje również interfejsy umożliwiające dostarczenie niestandardowego aparatu trwałości.

 Dostępne są interfejsy, które umożliwiają składnikom niestandardowym zachowywanie własnych ustawień, gdy są one hostowane w aplikacji. Korzystając z kluczy ustawień, składniki mogą zachować różne ustawienia dla wielu wystąpień składnika.

## <a name="defining-settings"></a>Definiowanie ustawień
 Architektura ustawień aplikacji jest używana zarówno w ASP.NET, jak i Windows Forms i zawiera szereg klas bazowych, które są współużytkowane w obu środowiskach. Najważniejszym z nich <xref:System.Configuration.SettingsBase>jest, która zapewnia dostęp do ustawień za pomocą kolekcji i zapewnia metody niskiego poziomu do ładowania i zapisywania ustawień. Każde środowisko implementuje własną klasę pochodną od <xref:System.Configuration.SettingsBase> w celu zapewnienia dodatkowych funkcji ustawień dla tego środowiska. W aplikacji opartej na Windows Forms wszystkie ustawienia aplikacji muszą być zdefiniowane w klasie pochodzącej od <xref:System.Configuration.ApplicationSettingsBase> klasy, która dodaje następujące funkcje do klasy bazowej:

- Operacje ładowania i zapisywania wyższego poziomu

- Obsługa ustawień z zakresu użytkownika

- Przywracanie ustawień użytkownika do wstępnie zdefiniowanych wartości domyślnych

- Uaktualnianie ustawień z poprzedniej wersji aplikacji

- Weryfikowanie ustawień przed ich zmianą lub przed ich zapisaniem

 Ustawienia te można opisać przy użyciu wielu atrybutów zdefiniowanych <xref:System.Configuration> w przestrzeni nazw. są one opisane w obszarze [atrybuty ustawień aplikacji](application-settings-attributes.md). Podczas definiowania ustawienia, należy zastosować je z <xref:System.Configuration.ApplicationScopedSettingAttribute> lub <xref:System.Configuration.UserScopedSettingAttribute>, w tym opis, czy ustawienie ma zastosowanie do całej aplikacji, czy tylko dla bieżącego użytkownika.

 Poniższy przykład kodu definiuje klasę ustawień niestandardowych z pojedynczym ustawieniem `BackgroundColor`.

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Trwałość ustawień
 Klasa nie sama sama lub nie ładuje ustawień. to zadanie jest przeznaczone dla dostawcy ustawień, klasy, która pochodzi od <xref:System.Configuration.SettingsProvider>. <xref:System.Configuration.ApplicationSettingsBase> Jeśli klasa pochodna programu <xref:System.Configuration.ApplicationSettingsBase> nie określi dostawcy ustawień <xref:System.Configuration.SettingsProviderAttribute>za pomocą programu, zostanie użyty domyślny dostawca <xref:System.Configuration.LocalFileSettingsProvider>.

 System konfiguracyjny, który pierwotnie wydano w .NET Framework, obsługuje dostarczanie statycznych danych konfiguracyjnych aplikacji za pomocą pliku Machine. config komputera lokalnego lub w `app.`pliku exe. config, który jest wdrażany za pomocą Twoja aplikacja. <xref:System.Configuration.LocalFileSettingsProvider> Klasa rozszerza tę natywną obsługę w następujący sposób:

- Ustawienia o zakresie aplikacji mogą być przechowywane w plikach Machine. config lub `app.`exe. config. Plik Machine. config jest zawsze tylko do odczytu, `app`natomiast plik. exe. config jest ograniczony przez zagadnienia dotyczące zabezpieczeń tylko do odczytu dla większości aplikacji.

- Ustawienia o zakresie użytkownika mogą być przechowywane w `app`plikach. exe. config, w takim przypadku są one traktowane jako statyczne wartości domyślne.

- Ustawienia z zakresu użytkownika inne niż domyślne są przechowywane w nowym pliku, *User*. config, gdzie *użytkownik* jest nazwą użytkownika osoby, która aktualnie wykonuje aplikację. Wartość domyślną dla ustawienia zakresu użytkownika można określić za pomocą <xref:System.Configuration.DefaultSettingValueAttribute>. Ponieważ ustawienia o zakresie użytkownika często zmieniają się podczas wykonywania aplikacji, `user`plik. config ma zawsze odczyt/zapis.

 Wszystkie trzy pliki konfiguracji przechowują ustawienia w formacie XML. Element XML najwyższego poziomu dla ustawień o zakresie aplikacji ma wartość `<appSettings>`, natomiast `<userSettings>` jest używany dla ustawień z zakresu użytkownika. Plik `app`. exe. config, który zawiera ustawienia dotyczące zakresu aplikacji i ustawienia domyślne dla ustawień o zakresie użytkownika, będzie wyglądać następująco:

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

 Aby zapoznać się z definicją elementów w sekcji Ustawienia aplikacji w pliku konfiguracji, zobacz [Schemat ustawień aplikacji](../../configure-apps/file-schema/application-settings-schema.md).

### <a name="settings-bindings"></a>Powiązania ustawień
 Ustawienia aplikacji używają architektury powiązań danych Windows Forms w celu zapewnienia dwukierunkowej komunikacji między ustawieniami ustawień a obiektem ustawień. Jeśli używasz programu Visual Studio do tworzenia ustawień aplikacji i przypisywania ich do właściwości składników, te powiązania są generowane automatycznie.

 Ustawienie aplikacji można powiązać tylko ze składnikiem, który obsługuje <xref:System.Windows.Forms.IBindableComponent> interfejs. Ponadto składnik musi zaimplementować zdarzenie zmiany dla konkretnej powiązanej właściwości lub Powiadom ustawienia aplikacji, że właściwość została zmieniona za pomocą <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Jeśli składnik nie zostanie zaimplementowany <xref:System.Windows.Forms.IBindableComponent> i masz powiązanie za pomocą programu Visual Studio, właściwości powiązane zostaną ustawione po raz pierwszy, ale nie zostaną zaktualizowane. Jeśli składnik implementuje <xref:System.Windows.Forms.IBindableComponent> , ale nie obsługuje powiadomień o zmianach właściwości, powiązanie nie zostanie zaktualizowane w pliku ustawień, gdy właściwość zostanie zmieniona.

 Niektóre składniki Windows Forms, takie jak <xref:System.Windows.Forms.ToolStripItem>, nie obsługują powiązań ustawień.

### <a name="settings-serialization"></a>Serializacja ustawień
 Gdy <xref:System.Configuration.LocalFileSettingsProvider> program musi zapisać ustawienia na dysku, wykonuje następujące czynności:

1. Używa odbicia, aby przejrzeć wszystkie właściwości zdefiniowane w <xref:System.Configuration.ApplicationSettingsBase> klasie pochodnej, wyszukując te, które są stosowane <xref:System.Configuration.ApplicationScopedSettingAttribute> z lub <xref:System.Configuration.UserScopedSettingAttribute>.

2. Serializować właściwość na dysk. Najpierw próbuje wywołać <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> lub <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> na skojarzonym <xref:System.ComponentModel.TypeConverter>typie. Jeśli to się nie powiedzie, zamiast tego używa serializacji XML.

3. Określa, które Ustawienia przejdź do plików, na podstawie atrybutu ustawienia.

 W przypadku zaimplementowania własnej klasy ustawień można użyć <xref:System.Configuration.SettingsSerializeAsAttribute> do oznaczenia ustawienia dla serializacji binarnej lub niestandardowej <xref:System.Configuration.SettingsSerializeAs> przy użyciu wyliczenia. Aby uzyskać więcej informacji na temat tworzenia własnych klas ustawień w kodzie, [zobacz How to: Utwórz ustawienia](how-to-create-application-settings.md)aplikacji.

### <a name="settings-file-locations"></a>Lokalizacje plików ustawień
 Lokalizacja `app`plików exe. config i *User*. config różni się w zależności od sposobu instalowania aplikacji. W przypadku aplikacji opartej na Windows Forms skopiowanej na komputer `app`lokalny plik. exe. config będzie znajdować się w tym samym katalogu, co katalog podstawowy głównego pliku wykonywalnego aplikacji, a *User*. config będzie znajdować się w lokalizacji określonej przez <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> właściwość. W przypadku aplikacji zainstalowanej za pomocą technologii ClickOnce oba te pliki będą znajdować się w katalogu danych ClickOnce poniżej%InstallRoot%\Documents i ustawienia\\*username*\Ustawienia Settings.

 Lokalizacja przechowywania tych plików jest nieco inna, jeśli użytkownik włączył profile mobilne, dzięki czemu użytkownik może zdefiniować różne ustawienia systemu Windows i aplikacji, gdy używa innych komputerów w domenie. W takim przypadku zarówno aplikacje ClickOnce, jak i aplikacje inne niż ClickOnce będą mieć `app`pliki. exe. config i *User*. config przechowywane w obszarze%InstallRoot%\Documents i\\Settings*username*\Dane dane.

 Aby uzyskać więcej informacji o tym, jak funkcja ustawienia aplikacji współpracuje z nową technologią wdrażania, zobacz [ustawienia technologii ClickOnce i aplikacji](/visualstudio/deployment/clickonce-and-application-settings). Aby uzyskać więcej informacji na temat katalogu danych ClickOnce, zobacz [dostęp do danych lokalnych i zdalnych w aplikacjach ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).

## <a name="application-settings-and-security"></a>Ustawienia i zabezpieczenia aplikacji
 Ustawienia aplikacji są przeznaczone do pracy w częściowej relacji zaufania, czyli środowiska z ograniczeniami, które jest domyślnie przeznaczone dla aplikacji Windows Forms hostowanych przez Internet lub intranet. Nie są konieczne żadne specjalne uprawnienia poza częściową relacją zaufania, aby użyć ustawień aplikacji z domyślnym dostawcą ustawień.

 Gdy ustawienia aplikacji są używane w aplikacji ClickOnce, `user`plik. config jest przechowywany w katalogu danych ClickOnce. Rozmiar pliku `user`. config aplikacji nie może przekroczyć limitu przydziału katalogu danych określonego przez ClickOnce. Aby uzyskać więcej informacji, zobacz [ustawienia technologii ClickOnce i aplikacji](/visualstudio/deployment/clickonce-and-application-settings).

## <a name="custom-settings-providers"></a>Dostawcy ustawień niestandardowych
 W architekturze ustawień aplikacji istnieje luźny sprzężenie między klasą otoki ustawień aplikacji, pochodną <xref:System.Configuration.ApplicationSettingsBase>od i dostawcami powiązanych ustawień lub dostawcy, pochodnymi <xref:System.Configuration.SettingsProvider>od. To skojarzenie jest zdefiniowane tylko przez <xref:System.Configuration.SettingsProviderAttribute> zastosowany do klasy otoki lub jej poszczególnych właściwości. Jeśli dostawca ustawień nie został jawnie określony, używany jest domyślny dostawca <xref:System.Configuration.LocalFileSettingsProvider>. W efekcie ta architektura obsługuje tworzenie i używanie dostawców ustawień niestandardowych.

 Załóżmy na przykład, że chcesz utworzyć i użyć `SqlSettingsProvider`dostawcy, który będzie przechowywać wszystkie dane ustawień w Microsoft SQL Server bazie danych. Klasa pochodna otrzyma te informacje w swojej `Initialize` metodzie jako parametr typu <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. <xref:System.Configuration.SettingsProvider> Następnie należy zaimplementować <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> metodę w celu pobrania ustawień z magazynu danych i <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> zapisania ich. Dostawca może użyć <xref:System.Configuration.SettingsPropertyCollection> dostarczonych do <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> , aby określić nazwę, typ i zakres właściwości, a także inne atrybuty ustawień zdefiniowane dla tej właściwości.

 Dostawca będzie musiał zaimplementować jedną właściwość i jedną metodę, której implementacje mogą nie być oczywiste. Właściwość jest właściwością abstrakcyjną; należy ją zaprogramować, aby zwracała następujące elementy: <xref:System.Configuration.SettingsProvider> <xref:System.Configuration.SettingsProvider.ApplicationName%2A>

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Klasa pochodna musi również implementować `Initialize` metodę, która nie przyjmuje argumentów i nie zwraca żadnej wartości. Ta metoda nie jest definiowana przez <xref:System.Configuration.SettingsProvider>.

 Na koniec należy wdrożyć <xref:System.Configuration.IApplicationSettingsProvider> na swoim dostawcy, aby zapewnić obsługę odświeżania ustawień, przywrócenie ustawień domyślnych i uaktualnienie ustawień z jednej wersji aplikacji do innej.

 Po zaimplementowaniu i skompilowaniu dostawcy należy poinstruować klasę ustawień, aby używała tego dostawcy zamiast domyślnego. Można to zrobić za pomocą <xref:System.Configuration.SettingsProviderAttribute>. W przypadku zastosowania do całej klasy ustawień dostawca jest używany dla każdego ustawienia, które definiuje Klasa; w przypadku zastosowania do poszczególnych ustawień Architektura ustawień aplikacji używa tego dostawcy tylko dla tych ustawień i używa <xref:System.Configuration.LocalFileSettingsProvider> dla reszty. Poniższy przykład kodu pokazuje, jak nakazać klasie ustawień użycie dostawcy niestandardowego.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Dostawca może być wywoływany z wielu wątków jednocześnie, ale zawsze będzie zapisywać w tej samej lokalizacji magazynu; w związku z tym Architektura ustawień aplikacji będzie kiedykolwiek tworzyć wystąpienie tylko jednego wystąpienia klasy dostawcy.

> [!IMPORTANT]
>  Należy upewnić się, że dostawca jest bezpieczny dla wątków i zezwala tylko jednemu wątkowi na zapisywanie w plikach konfiguracji.

 Dostawca nie musi obsługiwać wszystkich <xref:System.Configuration?displayProperty=nameWithType> atrybutów ustawień zdefiniowanych w przestrzeni nazw, chociaż musi mieć minimalną pomoc techniczną <xref:System.Configuration.ApplicationScopedSettingAttribute> i <xref:System.Configuration.UserScopedSettingAttribute>, i powinien również obsługiwać <xref:System.Configuration.DefaultSettingValueAttribute>. Dla tych atrybutów, które nie są obsługiwane, dostawca powinien po prostu kończyć się niepowodzeniem bez powiadomienia; nie powinna zgłosić wyjątku. Jeśli jednak Klasa Settings używa nieprawidłowej kombinacji atrybutów, takie jak zastosowanie <xref:System.Configuration.ApplicationScopedSettingAttribute> i <xref:System.Configuration.UserScopedSettingAttribute> do tego samego ustawienia — dostawca powinien zgłosić wyjątek i zakończyć operację.

## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Przegląd ustawień aplikacji](application-settings-overview.md)
- [Ustawienia aplikacji dotyczące kontrolek niestandardowych](application-settings-for-custom-controls.md)
- [ClickOnce i ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings)
- [Schemat ustawień aplikacji](../../configure-apps/file-schema/application-settings-schema.md)
