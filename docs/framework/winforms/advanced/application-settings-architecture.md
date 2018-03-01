---
title: "Architektura ustawień aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c437f305b847ff7922c98b4917e86ebd39ee100
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-architecture"></a>Architektura ustawień aplikacji
W tym temacie opisano, jak działa Architektura ustawień aplikacji i Eksploruje zaawansowanych funkcji architektury, takie jak ustawienia grupowanych i ustawienia kluczy.  
  
 Architektura ustawień aplikacji obsługuje definiującego jednoznacznie ustawienia za pomocą aplikacji lub zakresu użytkownika i przechowywanie ustawienia między sesjami aplikacji. Architektura udostępnia domyślny aparat trwałości, który zapisywania ustawienia i ładuje je z lokalnego systemu plików. Architektura definiuje również interfejsy dostarczanie aparatu niestandardowego.  
  
 Interfejsy są dostarczane umożliwiających niestandardowych składników utrwalić własne ustawienia, jeśli są one hostowane w aplikacji. Przy użyciu ustawienia kluczy, składniki ustawienia można zachować wiele wystąpień składnika oddzielne.  
  
## <a name="defining-settings"></a>Definiowanie ustawień  
 Architektura ustawień aplikacji jest używany w obu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] i formularze systemu Windows który zawiera wiele klas podstawowych, które są udostępniane w obu środowiskach. Najważniejsze jest <xref:System.Configuration.SettingsBase>, który zapewnia dostęp do ustawień za pomocą kolekcji i udostępnia metody niskiego poziomu do ładowania i zapisywania ustawień. Każde środowisko implementuje własnej pochodzi od klasy <xref:System.Configuration.SettingsBase> umożliwiają korzystanie z funkcji dodatkowych ustawień dla tego środowiska. W aplikacji formularzy systemu Windows, wszystkie ustawienia aplikacji musi być zdefiniowana w klasy pochodzącej od <xref:System.Configuration.ApplicationSettingsBase> klasy, która dodaje do klasy podstawowej następujące funkcje:  
  
-   Ładowanie wyższego poziomu i zapisywanie operacji  
  
-   Obsługa ustawień z zakresu użytkownika  
  
-   Przywracanie ustawień użytkownika do wstępnie zdefiniowanych ustawień domyślnych  
  
-   Uaktualnianie ustawień z poprzedniej wersji aplikacji  
  
-   Sprawdzanie poprawności ustawień, zanim zostaną one zmienione lub przed ich zapisaniem  
  
 Ustawienia można również opisać za pomocą numeru atrybuty zdefiniowane w ramach <xref:System.Configuration> przestrzeni nazw; opisano je w [atrybuty ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-attributes.md). Po zdefiniowaniu ustawienia, należy najpierw zastosować go przy użyciu jednej <xref:System.Configuration.ApplicationScopedSettingAttribute> lub <xref:System.Configuration.UserScopedSettingAttribute>, która opisuje, czy ustawienie ma zastosowanie do całej aplikacji lub tylko do bieżącego użytkownika.  
  
 Poniższy przykładowy kod definiuje klasę ustawień niestandardowych przy użyciu jednego ustawienia `BackgroundColor`.  
  
 [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>Ustawienia trwałości  
 <xref:System.Configuration.ApplicationSettingsBase> Klasy nie sam utrwalić lub załadować ustawień; tego zadania znajduje się do ustawień dostawcy, klasy, która jest pochodną <xref:System.Configuration.SettingsProvider>. Jeśli klasa pochodna z <xref:System.Configuration.ApplicationSettingsBase> nie określono ustawień dostawcy za pośrednictwem <xref:System.Configuration.SettingsProviderAttribute>, domyślny dostawca, a następnie <xref:System.Configuration.LocalFileSettingsProvider>, jest używany.  
  
 System konfiguracji, który pierwotnie został wydany z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obsługuje dostarcza dane konfiguracji statycznej aplikacji za pomocą komputera lokalnego pliku machine.config lub w `app.`pliku exe.config, który można wdrożyć z aplikacji. <xref:System.Configuration.LocalFileSettingsProvider> Klasa rozszerza Natywna obsługa w następujący sposób:  
  
-   Ustawienia zakresu aplikacji mogą być przechowywane w każdym pliku machine.config lub `app.`exe.config plików. Machine.config jest zawsze tylko do odczytu, podczas `app`. exe.config jest ograniczony przez zagadnienia dotyczące zabezpieczeń tylko do odczytu dla większości aplikacji.  
  
-   Ustawienia zakresu użytkownika mogą być przechowywane w `app`. exe.config plików, w tym przypadku są traktowane jako statyczne ustawienia domyślne.  
  
-   Inne niż domyślne ustawienia zakresu użytkownika są przechowywane w nowym pliku *użytkownika*.config, gdzie *użytkownika* jest nazwą użytkownika osoby aktualnie wykonywanych aplikacji. Można określić domyślnego ustawienia zakresu użytkownika z <xref:System.Configuration.DefaultSettingValueAttribute>. Ponieważ ustawień z zakresu użytkownika często się zmieniają podczas wykonywania aplikacji `user`.config jest zawsze odczytu/zapisu.  
  
 Wszystkie pliki konfiguracji trzy ustawienia są przechowywane w formacie XML. Element XML najwyższego poziomu dla ustawień z zakresu aplikacji jest `<appSettings>`, podczas gdy `<userSettings>` jest używana do ustawienia zakresu użytkownika. `app`. Exe.config pliku, który zawiera zarówno zakresu aplikacji i domyślne ustawienia dla ustawień z zakresu użytkownika będzie wyglądać następująco:  
  
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
  
 Dla definicji elementów w sekcji Ustawienia aplikacji w pliku konfiguracji, zobacz [schemat ustawień aplikacji](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md).  
  
### <a name="settings-bindings"></a>Ustawienia powiązań  
 Ustawienia aplikacji używa architektura powiązanie danych formularzy systemu Windows w celu zapewnienia dwukierunkowej komunikacji aktualizacji ustawienia między obiekt ustawień i składniki. Jeśli używasz programu Visual Studio do tworzenia ustawienia aplikacji i przypisać je do właściwości składnika tych powiązań są generowane automatycznie.  
  
 Ustawienie aplikacji można powiązać tylko z składnika obsługującego <xref:System.Windows.Forms.IBindableComponent> interfejsu. Ponadto składnik musi implementować zdarzenia zmiany dla określonego powiązane właściwości lub powiadomić ustawienia aplikacji, które właściwości została zmieniona przez <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Jeśli składnik nie implementuje <xref:System.Windows.Forms.IBindableComponent> i są powiązania za pomocą programu Visual Studio, powiązane właściwości można ustawić po raz pierwszy, ale nie będzie aktualizowana. Jeśli zaimplementowano składnik <xref:System.Windows.Forms.IBindableComponent> , ale nie Obsługa właściwości zmienia powiadomienia, po zmianie właściwości powiązania nie będzie aktualizowana w pliku ustawień.  
  
 Niektóre składniki formularzy systemu Windows, takich jak <xref:System.Windows.Forms.ToolStripItem>, nie obsługuje ustawienia powiązania.  
  
### <a name="settings-serialization"></a>Ustawienia serializacji  
 Gdy <xref:System.Configuration.LocalFileSettingsProvider> należy zapisać ustawienia, dysku wykonuje następujące akcje:  
  
1.  Używa odbicia w celu zbadania wszystkich właściwości zdefiniowane w Twojej <xref:System.Configuration.ApplicationSettingsBase> klasy znajdowania tych, które są stosowane przy użyciu jednej <xref:System.Configuration.ApplicationScopedSettingAttribute> lub <xref:System.Configuration.UserScopedSettingAttribute>.  
  
2.  Serializuje właściwości na dysku. Najpierw próbuje wywołać <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> lub <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> na skojarzonym typ <xref:System.ComponentModel.TypeConverter>. Jeśli to się nie powiedzie, nastąpi serializacji XML zamiast tego.  
  
3.  Określa ustawienia, które są umieszczone w plikach, w którym na podstawie atrybutu tego ustawienia.  
  
 Implementuje klasy ustawienia, można użyć <xref:System.Configuration.SettingsSerializeAsAttribute> do oznaczania ustawienie albo za pomocą serializacji binarnej lub niestandardowych <xref:System.Configuration.SettingsSerializeAs> wyliczenia. Aby uzyskać więcej informacji na temat tworzenia własnych klas ustawienia w kodzie, zobacz [porady: Tworzenie ustawień aplikacji](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
### <a name="settings-file-locations"></a>Ustawienia lokalizacji plików  
 Lokalizacja `app`. exe.config i *użytkownika*plikach .config będą różne w zależności od sposobu instalowania aplikacji. Dla aplikacji opartych na formularzach systemu Windows skopiowany na komputer lokalny `app`. exe.config będą znajdować się w tym samym katalogu co katalogu podstawowego aplikacji głównego pliku wykonywalnego, a *użytkownika*.config będą znajdować się w lokalizacji określonej przez <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> właściwości. Dla aplikacji zainstalowane za pomocą klasy [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], oba te pliki będą znajdować się w [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] katalog danych poniżej %InstallRoot%\Documents i ustawienia\\*username*\Local ustawienia.  
  
 Lokalizacja przechowywania tych plików różni się nieznacznie, jeśli użytkownik włączył profilów mobilnych, co umożliwia użytkownikowi na definiowanie różnych systemu Windows i ustawienia aplikacji, jeśli użytkownik korzysta z innych komputerów w domenie. W takim przypadku zarówno [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikacji i nie-[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikacji będą miały ich `app`. exe.config i *użytkownika*.config pliki przechowywane w obszarze Ustawienia i %InstallRoot%\Documents\\ *username*\Application danych.  
  
 Aby uzyskać więcej informacji na temat działania funkcji ustawień aplikacji z nowej technologii wdrażania, zobacz [ClickOnce i ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings). Aby uzyskać więcej informacji na temat [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] katalog danych, zobacz [dostęp do lokalnych i zdalnych danych w aplikacjach ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="application-settings-and-security"></a>Ustawienia aplikacji i zabezpieczenia  
 Ustawienia aplikacji są przeznaczone do pracy w częściowej relacji zaufania, środowisko z ograniczeniami, które jest ustawieniem domyślnym dla aplikacji Windows Forms hostowanej w Internecie lub intranecie. Żadne specjalne uprawnienia, które wykraczają poza częściowej relacji zaufania są niezbędne do używania ustawienia aplikacji z ustawienia domyślnego dostawcy.  
  
 Gdy aplikacja, ustawienia są używane w [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikacji, `user`pliku .config są przechowywane w [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] katalog danych. Rozmiar aplikacji `user`pliku .config nie może przekraczać limit przydziału katalogu ustawione przez [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]. Aby uzyskać więcej informacji, zobacz [ClickOnce i ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings).  
  
## <a name="custom-settings-providers"></a>Niestandardowe ustawienia dostawcy  
 Architektura ustawień aplikacji ma luźne powiązanie między ustawień aplikacji pochodzi od klasy otoki <xref:System.Configuration.ApplicationSettingsBase>, i powiązane ustawienia dostawcy lub dostawców, pochodnych <xref:System.Configuration.SettingsProvider>. To skojarzenie jest zdefiniowana tylko przez <xref:System.Configuration.SettingsProviderAttribute> stosowane do klasy otoki lub jego poszczególnych właściwości. Jeśli ustawienia dostawcy nie jest jawnie określić domyślnego dostawcę <xref:System.Configuration.LocalFileSettingsProvider>, jest używany. W związku z tym tej architektury obsługuje tworzenie i korzystanie z ustawień niestandardowych dostawców.  
  
 Na przykład załóżmy, że chcesz opracowanie i wykorzystanie `SqlSettingsProvider`, dostawcy, w którym będą przechowywane wszystkie ustawienia danych w bazie danych programu Microsoft SQL Server. Twoje <xref:System.Configuration.SettingsProvider>— Klasa pochodna może pobrać te informacje w jego `Initialize` metody jako parametr typu <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Czy można następnie wdrożyć <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> metodę, aby pobrać ustawienia z magazynu danych i <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> ich zapisanie. Można użyć dostawcy <xref:System.Configuration.SettingsPropertyCollection> dostarczonych <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> Aby określić nazwę, typ i zakresu właściwości, oraz wszelkie inne atrybuty ustawienia zdefiniowane dla tej właściwości.  
  
 Twój dostawca należy zaimplementować jedną właściwość i jedną metodę, której implementacje może nie być widoczne. <xref:System.Configuration.SettingsProvider.ApplicationName%2A> Właściwość jest abstrakcyjny właściwość <xref:System.Configuration.SettingsProvider>; zostanie powinna zwracać następujące:  
  
 [!code-csharp[ApplicationSettings.Architecture#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 Klasy pochodne musi implementować też `Initialize` metodę, która nie przyjmuje żadnych argumentów i nie zwraca żadnej wartości. Ta metoda nie jest zdefiniowany przez <xref:System.Configuration.SettingsProvider>.  
  
 Ponadto wdrożenie <xref:System.Configuration.IApplicationSettingsProvider> na Twój dostawca zapewnia obsługę odświeżanie ustawień przywrócenie ustawień domyślnych i uaktualniania ustawienia wersji jedną aplikację do innego.  
  
 Po zaimplementowane i kompilowane dostawcy należy poinstruować klasy ustawień można użyć tego dostawcy, zamiast domyślnej. Można dodać za pomocą <xref:System.Configuration.SettingsProviderAttribute>. Zastosowanie do całej klasy ustawienia dostawcy jest używany dla każdego ustawienia, który definiuje klasę; Jeśli stosowane do poszczególnych ustawień, używa tego dostawcy dla tych ustawień tylko Architektura ustawień aplikacji, a używa <xref:System.Configuration.LocalFileSettingsProvider> dla pozostałej. Poniższy przykład kodu pokazuje, jak nakazać klasy ustawienia do użycia niestandardowego dostawcy.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 Dostawca może być wywoływana z wiele wątków jednocześnie, ale zawsze będą zapisywane w tej samej lokalizacji magazynu; w związku z tym Architektura ustawień aplikacji będą tylko wystąpienia pojedynczego wystąpienia klasy dostawcy.  
  
> [!IMPORTANT]
>  Należy upewnić się czy Twój dostawca wątkowo a zezwala na tylko jeden wątek w momencie można zapisać plików konfiguracji.  
  
 Twój dostawca musi obsługiwać wszystkie ustawienia atrybutów zdefiniowanych w <xref:System.Configuration?displayProperty=nameWithType> przestrzeni nazw, chociaż musi się ona na minimalnej obsługi <xref:System.Configuration.ApplicationScopedSettingAttribute> i <xref:System.Configuration.UserScopedSettingAttribute>i powinna obsługiwać <xref:System.Configuration.DefaultSettingValueAttribute>. Dla tych atrybutów, które nie obsługują dostawcy ulegnie awarii po prostu bez powiadomienia; należy zgłosiła wyjątek. Jeśli klasa ustawienia używa nieprawidłowej kombinacji atrybutów, jednak — takie jak stosowanie <xref:System.Configuration.ApplicationScopedSettingAttribute> i <xref:System.Configuration.UserScopedSettingAttribute> takie samo ustawienie — dostawcy należy zgłosić wyjątek i zaprzestanie operacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Ustawienia aplikacji dotyczące kontrolek niestandardowych](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)  
 [ClickOnce i ustawienia aplikacji](/visualstudio/deployment/clickonce-and-application-settings)  
 [Schemat ustawień aplikacji](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)
