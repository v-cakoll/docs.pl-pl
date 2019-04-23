---
title: Architektura ustawień aplikacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: c2a62b61cb7b31c978a84a3d3f41c24f9fafb84d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312569"
---
# <a name="application-settings-architecture"></a>Architektura ustawień aplikacji
W tym temacie opisano, jak działa Architektura ustawień aplikacji i analizuje zaawansowanych funkcji architektury, takich jak ustawienia pogrupowanych i klucze ustawienia.  
  
 Architektura ustawień aplikacji obsługuje definiowanie ustawień silnie typizowaną z albo aplikacji lub zakres użytkowników oraz przechowywanie ustawienia między sesjami aplikacji. Architektura zawiera domyślny aparat trwałości, zapisywania ustawień i ładowania ich z lokalnego systemu plików. Architektura definiuje również interfejsów dla podanie aparatu niestandardowego.  
  
 Interfejsy są dostarczane, dzięki którym składników niestandardowych utrwalić własne ustawienia, jeśli są one hostowane w aplikacji. Przy użyciu kluczy ustawienia, składniki zachować ustawienia dla wielu wystąpień składnika oddzielne.  
  
## <a name="defining-settings"></a>Definiowanie ustawień  
 Architektura ustawień aplikacji jest używany w obu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] i Windows Forms i zawiera wiele klas bazowych, które są udostępniane w obu środowiskach. Najważniejsze jest <xref:System.Configuration.SettingsBase>, która zapewnia dostęp do ustawień za pomocą kolekcji, a także metody niskiego poziomu ładowania i zapisywania ustawień. Każde środowisko implementuje własne klasy pochodzącej od <xref:System.Configuration.SettingsBase> umożliwiają korzystanie z funkcji dodatkowych ustawień dla tego środowiska. W aplikacji opartej na formularzach Windows, wszystkie ustawienia aplikacji musi być zdefiniowana w klasę pochodną <xref:System.Configuration.ApplicationSettingsBase> klasy, która dodaje następujące funkcje do klasy bazowej:  
  
-   Ładowanie wyższego poziomu i zapisywanie operacji  
  
-   Obsługa ustawień zakresu użytkownika  
  
-   Przywracanie ustawień użytkownika do wstępnie zdefiniowanych ustawień domyślnych  
  
-   Uaktualnianie ustawień z poprzedniej wersji aplikacji  
  
-   Weryfikowanie ustawień, zanim zostaną one zmienione lub przed ich zapisaniem  
  
 Ustawienia można opisać za pomocą numeru atrybuty zdefiniowane w ramach <xref:System.Configuration> przestrzeni nazw; te ustawienia zostały opisane w [atrybuty ustawień aplikacji](application-settings-attributes.md). Podczas definiowania ustawienie, należy zastosować go z oboma <xref:System.Configuration.ApplicationScopedSettingAttribute> lub <xref:System.Configuration.UserScopedSettingAttribute>, która opisuje, czy ustawienie dotyczy całej aplikacji, lub po prostu bieżącego użytkownika.  
  
 Poniższy kod definiuje klasę ustawienia niestandardowe, za pomocą pojedynczego ustawienia `BackgroundColor`.  
  
 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>Ustawienia trwałości  
 <xref:System.Configuration.ApplicationSettingsBase> Klasy nie sam utrwalić lub załadować ustawień; tego zadania znajduje się z dostawcą ustawienia klasy, która pochodzi od klasy <xref:System.Configuration.SettingsProvider>. Jeśli klasa pochodna <xref:System.Configuration.ApplicationSettingsBase> nie określono ustawień dostawcy za pośrednictwem <xref:System.Configuration.SettingsProviderAttribute>, domyślny dostawca, a następnie <xref:System.Configuration.LocalFileSettingsProvider>, jest używany.  
  
 System konfiguracyjny, który pierwotnie został wydany przy użyciu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obsługuje, podając dane konfiguracji statycznej aplikacji za pomocą komputera lokalnego pliku machine.config lub w ramach `app.`pliku exe.config, który można wdrożyć za pomocą Twoja aplikacja. <xref:System.Configuration.LocalFileSettingsProvider> Klasa rozszerza ten macierzystą obsługę w następujący sposób:  
  
-   Ustawienia w zakresie aplikacji mogą być przechowywane w dowolnym pliku machine.config lub `app.`exe.config plików. Machine.config zawsze jest tylko do odczytu, podczas `app`. exe.config jest ograniczony przez zagadnienia dotyczące zabezpieczeń tylko do odczytu dla większości aplikacji.  
  
-   Ustawienia z zakresu użytkownika mogą być przechowywane w `app`. exe.config plików, w którym to przypadku będą one traktowane jako statyczne ustawienia domyślne.  
  
-   Inne niż domyślne ustawień zakresu użytkownika są przechowywane w nowym pliku *użytkownika*.config, gdzie *użytkownika* to nazwa użytkownika osoby, w trakcie wykonywania aplikacji. Można określić jako domyślną dla ustawień z zakresu użytkownika za pomocą <xref:System.Configuration.DefaultSettingValueAttribute>. Ponieważ ustawienia z zakresu użytkownika często zmieniać podczas wykonywania aplikacji `user`.config jest zawsze odczytu/zapisu.  
  
 Wszystkie pliki konfiguracji trzy ustawienia są przechowywane w formacie XML. Element XML najwyższego poziomu dla ustawień o zakresie aplikacji jest `<appSettings>`, podczas gdy `<userSettings>` służy do ustawienia z zakresu użytkownika. `app`. Plik exe.config, który zawiera ustawienia z zakresu aplikacji i ustawień domyślnych ustawień zakresu użytkownika będzie wyglądać następująco:  
  
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
  
 Dla definicji elementów w obrębie sekcji Ustawienia aplikacji w pliku konfiguracji, zobacz [schemat ustawień aplikacji](../../configure-apps/file-schema/application-settings-schema.md).  
  
### <a name="settings-bindings"></a>Ustawienia powiązań  
 Ustawienia aplikacji używa architektury powiązanie danych formularzy Windows w celu zapewnienia dwukierunkowej komunikacji aktualizacji ustawień między obiektu ustawień i składników. Jeśli używasz programu Visual Studio do tworzenie ustawień aplikacji i przypisać je do właściwości składnika te powiązania są generowane automatycznie.  
  
 Ustawienie aplikacji można powiązać tylko z składnik, który obsługuje <xref:System.Windows.Forms.IBindableComponent> interfejsu. Również składnik musi implementować zdarzenia zmiany dla określonego powiązane właściwości lub powiadomić ustawienia aplikacji, których właściwość zmieniła się za pośrednictwem <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Jeśli składnik nie implementuje <xref:System.Windows.Forms.IBindableComponent> i której dokonywane jest wiązanie za pomocą programu Visual Studio, powiązane właściwości można ustawić po raz pierwszy, ale nie będzie aktualizowana. Jeśli składnik implementuje <xref:System.Windows.Forms.IBindableComponent> , ale nie pomocy technicznej właściwość zmienia się powiadomienia, powiązanie nie zostanie zaktualizowana w pliku ustawień po zmianie właściwości.  
  
 Niektóre składniki formularzy Windows, takich jak <xref:System.Windows.Forms.ToolStripItem>, nie obsługuje ustawienia powiązania.  
  
### <a name="settings-serialization"></a>Ustawienia serializacji  
 Gdy <xref:System.Configuration.LocalFileSettingsProvider> należy zapisać ustawienia dysku, wykonuje następujące czynności:  
  
1. Używa odbicia, aby sprawdzić wszystkie właściwości zdefiniowane w Twojej <xref:System.Configuration.ApplicationSettingsBase> klasy i znajdowania tych, które są stosowane z oboma <xref:System.Configuration.ApplicationScopedSettingAttribute> lub <xref:System.Configuration.UserScopedSettingAttribute>.  
  
2. Serializuje właściwości na dysku. Najpierw próbuje wywołać <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> lub <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> na skojarzonej z typem <xref:System.ComponentModel.TypeConverter>. Jeśli to się nie powiedzie, używa serializacji XML zamiast tego.  
  
3. Określa ustawienia, które go, w której pliki na podstawie atrybutu tego ustawienia.  
  
 W przypadku zastosowania klasy ustawienia, można użyć <xref:System.Configuration.SettingsSerializeAsAttribute> do oznaczania ustawienie binarne lub niestandardowej serializacji przy użyciu <xref:System.Configuration.SettingsSerializeAs> wyliczenia. Aby uzyskać więcej informacji na temat tworzenia własnych klas ustawień w kodzie, zobacz [jak: Tworzenie ustawień aplikacji](how-to-create-application-settings.md).  
  
### <a name="settings-file-locations"></a>Ustawienia lokalizacji plików  
 Lokalizacja `app`. exe.config i *użytkownika*.config pliki będą się różnić w zależności od sposobu instalowania aplikacji. W przypadku aplikacji opartych na formularzach Windows skopiować na komputer lokalny `app`. exe.config będą znajdować się w tym samym katalogu, jako katalog podstawowy aplikacji głównego pliku wykonywalnego, i *użytkownika*.config będą znajdować się w lokalizacji określonej przez <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> właściwości. Dla aplikacji, który został zainstalowany przez [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], oba te pliki będą znajdować się w [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] katalog danych poniżej ustawienia i %InstallRoot%\Documents\\*username*\Local ustawienia.  
  
 Lokalizacja przechowywania tych plików jest nieco inny, jeśli użytkownik włączył profile mobilne umożliwiającego użytkownikowi na definiowanie Windows różnych ustawień i aplikacji, jeśli użytkownik korzysta z innych komputerów w domenie. W takim przypadku zarówno [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikacji i innych niż-[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikacji ma ich `app`. exe.config i *użytkownika*.config pliki przechowywane w obszarze Ustawienia i %InstallRoot%\Documents\\ *username*\Application.  
  
 Aby uzyskać więcej informacji na temat działania funkcji ustawień aplikacji za pomocą nowej technologii wdrażania zobacz [ClickOnce i ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings). Aby uzyskać więcej informacji na temat [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] katalog danych, zobacz [Accessing Local and Remote Data in ClickOnce Applications](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="application-settings-and-security"></a>Ustawienia aplikacji i zabezpieczeń  
 Ustawienia aplikacji są przeznaczone do pracy w trybie częściowego zaufania ograniczonym środowisku, które jest ustawieniem domyślnym dla aplikacji Windows Forms, hostowanych przez Internet lub intranet. Żadne specjalne uprawnienia, poza częściowej relacji zaufania są potrzebne do ustawień aplikacji za pomocą ustawienia domyślnego dostawcy.  
  
 Gdy ustawienia aplikacji są używane w [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikacji `user`.config plik jest przechowywany w [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] katalog danych. Rozmiar aplikacji `user`plik .config nie może przekraczać limitu przydziału katalogu danych, które zostały ustawione przez [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]. Aby uzyskać więcej informacji, zobacz [ClickOnce i ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings).  
  
## <a name="custom-settings-providers"></a>Niestandardowe ustawienia dostawcy  
 W architekturze ustawienia aplikacji znajduje się tym luźne powiązanie ustawienia aplikacji klasy otoki pochodzące z <xref:System.Configuration.ApplicationSettingsBase>, i skojarzone ustawienia lub dostawców, pochodnych <xref:System.Configuration.SettingsProvider>. To skojarzenie jest zdefiniowana tylko przez <xref:System.Configuration.SettingsProviderAttribute> stosowane do klasy otoki lub jego poszczególnych właściwości. Jeśli ustawienia, dostawca nie jest jawnie określona, domyślny dostawca <xref:System.Configuration.LocalFileSettingsProvider>, jest używany. W rezultacie Ta architektura obsługuje tworzenie i używanie dostawców ustawień niestandardowych.  
  
 Załóżmy, że chcesz tworzyć i używać `SqlSettingsProvider`, dostawcy, w której będą przechowywane wszystkie dane ustawienia w bazie danych programu Microsoft SQL Server. Twoje <xref:System.Configuration.SettingsProvider>-klasy pochodnej będą otrzymywać te informacje w jego `Initialize` metoda jako parametr typu <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Umożliwi wdrożenie <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> metodę, aby pobrać ustawienia z magazynu danych i <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> je zapisać. Można użyć dostawcy <xref:System.Configuration.SettingsPropertyCollection> dostarczane do <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> Aby określić nazwę właściwości, typie i zakresie, jak również wszelkie inne atrybuty ustawienia zdefiniowane dla tej właściwości.  
  
 Twój dostawca musi implementować jedną właściwość i jedną metodę, której implementacji może nie być oczywista. <xref:System.Configuration.SettingsProvider.ApplicationName%2A> Właściwość jest abstrakcyjny właściwość <xref:System.Configuration.SettingsProvider>; programujesz powinno zwrócić następujące czynności:  
  
 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 Klasy pochodnej musi implementować też `Initialize` metodę, która nie przyjmuje żadnych argumentów i nie zwraca żadnej wartości. Ta metoda nie jest zdefiniowany przez <xref:System.Configuration.SettingsProvider>.  
  
 Na koniec należy zaimplementować <xref:System.Configuration.IApplicationSettingsProvider> na Twój dostawca w celu zapewnienia obsługi odświeżanie ustawień przywrócenie ustawień domyślnych i aktualizowanie ustawień z wersji jednej aplikacji na inny.  
  
 Po zaimplementowane i kompilowane dostawcy należy wydać polecenie klasy ustawienia do używania tego dostawcy zamiast domyślnego. Osiągniesz to za pośrednictwem <xref:System.Configuration.SettingsProviderAttribute>. Zastosowanie do całej klasy ustawień dostawcy jest używany dla każdego ustawienia, który definiuje klasę; Jeśli stosowane do poszczególnych ustawień, architektura ustawień aplikacji używa tego dostawcy tylko do tych ustawień i używa <xref:System.Configuration.LocalFileSettingsProvider> przez resztę. W poniższym przykładzie kodu pokazano, jak nakazać Klasa ustawień, aby użyć niestandardowego dostawcy.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 Dostawca może być wywoływana z wielu wątków jednocześnie, ale zawsze będzie zapisywać w tej samej lokalizacji magazynu; w związku z tym Architektura ustawień aplikacji będzie tylko tworzy pojedyncze wystąpienie klasy dostawcy.  
  
> [!IMPORTANT]
>  Należy upewnić się, Twój dostawca jest bezpieczna dla wątków i może składać się jednemu wątkowi w czasie do zapisu do plików konfiguracji.  
  
 Twój dostawca musi obsługiwać wszystkie ustawienia zdefiniowane atrybuty w <xref:System.Configuration?displayProperty=nameWithType> przestrzeni nazw, chociaż jest to wymagane na minimalna obsługa <xref:System.Configuration.ApplicationScopedSettingAttribute> i <xref:System.Configuration.UserScopedSettingAttribute>i powinien obsługiwać <xref:System.Configuration.DefaultSettingValueAttribute>. Te atrybuty, które nie obsługuje Twój dostawca powinna po prostu zakończyć się niepowodzeniem bez powiadomienia; nie należy go zgłosić wyjątek. Jeśli klasa ustawień korzysta z nieprawidłową kombinację atrybutów, jednak — takich jak stosowanie <xref:System.Configuration.ApplicationScopedSettingAttribute> i <xref:System.Configuration.UserScopedSettingAttribute> takie samo ustawienie — dostawcy należy zgłosić wyjątek i zaprzestanie działania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Przegląd ustawień aplikacji](application-settings-overview.md)
- [Ustawienia aplikacji dotyczące kontrolek niestandardowych](application-settings-for-custom-controls.md)
- [ClickOnce i ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings)
- [Schemat ustawień aplikacji](../../configure-apps/file-schema/application-settings-schema.md)
