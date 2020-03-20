---
title: Sposoby lokalizowania zestawów przez środowisko uruchomieniowe
ms.date: 03/30/2017
helpviewer_keywords:
- app.config files, assembly locations
- deploying applications [.NET Framework], assembly locations
- application configuration files, locating assemblies
- .NET Framework application deployment, locating assemblies
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 772ac6f4-64d2-4cfb-92fd-58096dcd6c34
ms.openlocfilehash: 13e2661b67ba3b717b8917e80118175acb09e756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181675"
---
# <a name="how-the-runtime-locates-assemblies"></a>Sposoby lokalizowania zestawów przez środowisko uruchomieniowe

Aby pomyślnie wdrożyć aplikację .NET Framework, należy zrozumieć, jak środowisko wykonawcze języka wspólnego lokalizuje i wiąże się z zestawami, które tworzą aplikację. Domyślnie środowisko uruchomieniowe próbuje powiązać z dokładną wersją zestawu, z pomocą których została zbudowana aplikacja. To domyślne zachowanie można zastąpić ustawieniami pliku konfiguracyjnego.

Środowisko wykonawcze języka wspólnego wykonuje szereg kroków podczas próby zlokalizowania zestawu i rozwiązania odwołania do zestawu. Każdy krok jest wyjaśniony w poniższych sekcjach. Termin sondowanie jest często używany podczas opisywania sposobu, w jaki środowisko wykonawcze lokalizuje zestawy; odnosi się do zestawu heurystyki używanej do lokalizowania zestawu na podstawie jego nazwy i kultury.

> [!NOTE]
> Informacje o powiązaniach można wyświetlać w pliku dziennika za pomocą [przeglądarki dziennika wiązania zestawu (Fuslogvw.exe),](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)która znajduje się w zestawie Windows SDK.

## <a name="initiating-the-bind"></a>Inicjowanie powiązania

Proces lokalizowania i wiązania z zestawem rozpoczyna się, gdy środowisko uruchomieniowe próbuje rozwiązać odwołanie do innego zestawu. To odwołanie może być statyczne lub dynamiczne. Kompilator rejestruje odwołania statyczne w metadanych manifestu zestawu w czasie kompilacji. Odniesienia dynamiczne są konstruowane w locie w wyniku <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>wywoływania różnych metod, takich jak .

Preferowanym sposobem odwoływania się do zestawu jest użycie pełnego odwołania, w tym nazwy zestawu, wersji, kultury i tokenu klucza publicznego (jeśli istnieje). Środowisko wykonawcze używa tych informacji do zlokalizowania zestawu, wykonując kroki opisane w dalszej części tej sekcji. Środowisko wykonawcze używa tego samego procesu rozpoznawania niezależnie od tego, czy odwołanie jest dla zestawu statycznego lub dynamicznego.

Można również dokonać dynamicznego odwołania do zestawu, podając metodę wywołującą tylko częściowe informacje o zestawie, takie jak określanie tylko nazwy zestawu. W takim przypadku tylko katalog aplikacji jest wyszukiwany dla zestawu i nie występuje inne sprawdzanie. Należy dokonać częściowego odwołania przy użyciu dowolnej z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> różnych <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>metod ładowania zestawów, takich jak lub .

Na koniec można dokonać odwołania dynamicznego przy <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> użyciu metody, takich jak i podać tylko częściowe informacje; następnie zakwalifikujesz odwołanie przy użyciu [ \<elementu qualifyAssembly>](../configure-apps/file-schema/runtime/qualifyassembly-element.md) w pliku konfiguracji aplikacji. Ten element umożliwia podanie pełnych informacji referencyjnych (nazwa, wersja, kultura i, jeśli dotyczy, token klucza publicznego) w pliku konfiguracji aplikacji, a nie w kodzie. Tej techniki należy użyć, jeśli chcesz w pełni zakwalifikować odwołanie do zestawu poza katalogiem aplikacji lub jeśli chcesz odwołać się do zestawu w globalnej pamięci podręcznej zestawów, ale chcesz wygodę określania pełnego odwołania w pliku konfiguracyjnego, a nie w kodzie.

> [!NOTE]
> Tego typu częściowego odwołania nie należy używać z zestawami, które są współużytkowane przez kilka aplikacji. Ponieważ ustawienia konfiguracji są stosowane dla aplikacji, a nie na zestaw, zestaw udostępniony przy użyciu tego typu częściowego odwołania wymagałoby każdej aplikacji przy użyciu zestawu udostępnionego mieć informacje kwalifikacyjne w pliku konfiguracji.

Środowisko wykonawcze używa następujących kroków, aby rozwiązać odwołanie do zestawu:

1. [Określa poprawną wersję zestawu,](#step1) sprawdzając odpowiednie pliki konfiguracyjne, w tym plik konfiguracji aplikacji, plik zasad wydawcy i plik konfiguracji komputera. Jeśli plik konfiguracyjny znajduje się na komputerze zdalnym, środowisko wykonawcze musi najpierw zlokalizować i pobrać plik konfiguracji aplikacji.

2. [Sprawdza, czy nazwa zestawu została powiązana z przed,](#step2) a jeśli tak, używa wcześniej załadowanego zestawu. Jeśli poprzednie żądanie załadowania zestawu nie powiodło się, żądanie nie powiedzie się natychmiast bez próby załadowania zestawu.

    > [!NOTE]
    > Buforowanie błędów wiązania zestawu jest nowy w .NET Framework w wersji 2.0.

3. [Sprawdza globalną pamięć podręczną zestawów](#step3). Jeśli zestaw zostanie znaleziony tam, środowisko wykonawcze używa tego zestawu.

4. [Sondy dla zespołu](#step4) przy użyciu następujących kroków:

    1. Jeśli zasady konfiguracji i wydawcy nie mają wpływu na oryginalne <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> odwołanie i jeśli żądanie powiązania zostało utworzone przy użyciu metody, środowisko uruchomieniowe sprawdza wskazówki dotyczące lokalizacji.

    2. Jeśli baza kodu zostanie znaleziona w plikach konfiguracyjnych, środowisko wykonawcze sprawdza tylko tę lokalizację. Jeśli ta sonda nie powiedzie się, środowisko wykonawcze określa, że żądanie powiązania nie powiodło się i nie występuje inne sondowanie.

    3. Sondy do montażu przy użyciu heurystyki opisanej w [sekcji sondowania](#step4). Jeśli zestaw nie zostanie znaleziony po sondowaniu, środowisko wykonawcze żąda Instalatora Windows, aby zapewnić zestaw. Działa to jako funkcja instalacji na żądanie.

        > [!NOTE]
        > Nie ma sprawdzania wersji dla zestawów bez silnych nazw, ani nie sprawdza środowiska wykonawczego w globalnej pamięci podręcznej zestawów dla zestawów bez silnych nazw.

<a name="step1"></a>

## <a name="step-1-examining-the-configuration-files"></a>Krok 1. Badanie plików konfiguracji

Zachowanie wiązania zestawu można skonfigurować na różnych poziomach na podstawie trzech plików XML:

- Plik konfiguracyjny aplikacji.

- Plik zasad wydawcy.

- Plik konfiguracyjny komputera.

Pliki te są zgodne z tą samą składnią i zawierają informacje, takie jak przekierowania powiązania, lokalizacja kodu i tryby wiązania dla poszczególnych zestawów. Każdy plik konfiguracji może zawierać [ \<element zestawuBinowanie>,](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) który przekierowuje proces wiązania. Elementy podrzędne [ \<elementu zestawuBinowanie>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) obejmują [ \<zależnyAsześcij> element](../configure-apps/file-schema/runtime/dependentassembly-element.md). Elementy podrzędne [ \<dependentAssembly> element](../configure-apps/file-schema/runtime/dependentassembly-element.md) obejmują [ \<assemblyIdentity> element,](/visualstudio/deployment/assemblyidentity-element-clickonce-deployment) [ \<bindingRedirect> element](../configure-apps/file-schema/runtime/bindingredirect-element.md)i [ \<codeBase> element](../configure-apps/file-schema/runtime/codebase-element.md).

> [!NOTE]
> Informacje o konfiguracji można znaleźć w trzech plikach konfiguracyjnych; nie wszystkie elementy są prawidłowe we wszystkich plikach konfiguracyjnych. Na przykład informacje o trybie powiązania i ścieżce prywatnej mogą znajdować się tylko w pliku konfiguracji aplikacji. Aby uzyskać pełną listę informacji zawartych w każdym pliku, zobacz [Konfigurowanie aplikacji przy użyciu plików konfiguracyjnych](../configure-apps/index.md).

### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji

Po pierwsze środowisko uruchomieniowe języka wspólnego sprawdza plik konfiguracji aplikacji pod kątem informacji, które zastępuje informacje o wersji przechowywane w manifeście zestawu wywołującego. Plik konfiguracji aplikacji można wdrożyć z aplikacją, ale nie jest wymagane do wykonania aplikacji. Zazwyczaj pobieranie tego pliku jest niemal natychmiastowe, ale w sytuacjach, gdy baza aplikacji znajduje się na komputerze zdalnym, na przykład w scenariuszu opartym na sieci Web programu Internet Explorer, plik konfiguracyjny musi zostać pobrany.

W przypadku plików wykonywalnych klienta plik konfiguracji aplikacji znajduje się w tym samym katalogu co plik wykonywalny aplikacji i ma taką samą nazwę podstawową jak plik wykonywalny z rozszerzeniem .config. Na przykład plik konfiguracyjny dla C:\Program Files\Myapp\Myapp.exe to C:\Program Files\Myapp\Myapp.exe.config. W scenariuszu opartym na przeglądarce plik HTML musi używać ** \<elementu>łącza,** aby jawnie wskazać plik konfiguracyjny.

Poniższy kod zawiera prosty przykład pliku konfiguracji aplikacji. W tym <xref:System.Diagnostics.TextWriterTraceListener> przykładzie <xref:System.Diagnostics.Debug.Listeners%2A> dodaje do kolekcji, aby włączyć rejestrowanie informacji debugowania do pliku.

```xml
<configuration>
   <system.diagnostics>
      <trace useGlobalLock="false" autoflush="true" indentsize="0">
         <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
         </listeners>
      </trace>
   </system.diagnostics>
</configuration>
```

### <a name="publisher-policy-file"></a>Plik zasad wydawcy

Po drugie środowisko wykonawcze sprawdza plik zasad wydawcy, jeśli istnieje. Pliki zasad programu Publisher są rozpowszechniane przez wydawcę komponentu jako poprawka lub aktualizacja składnika udostępnionego. Pliki te zawierają informacje o zgodności wydane przez wydawcę udostępnionego składnika, który kieruje odwołanie do zestawu do nowej wersji. W przeciwieństwie do plików konfiguracyjnych aplikacji i maszyn pliki zasad wydawcy są zawarte we własnym zestawie, które muszą być zainstalowane w globalnej pamięci podręcznej zestawów.

Oto przykład pliku konfiguracji zasad programu Publisher:

```xml
<configuration>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">

            <dependentAssembly>
                <assemblyIdentity name="asm6" publicKeyToken="c0305c36380ba429" />
                <bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0"/>
            </dependentAssembly>

        </assemblyBinding>
    </runtime>
</configuration>
```

Aby utworzyć złożenie, można użyć narzędzia [Al.exe (Assembly Linker)](../tools/al-exe-assembly-linker.md) z następującym poleceniem:

```console
Al.exe /link:asm6.exe.config /out:policy.3.0.asm6.dll /keyfile: compatkey.dat /v:3.0.0.0
```

`compatkey.dat`jest plikiem klucza o silnej nazwie. To polecenie tworzy zestaw o silnej nazwie, który można umieścić w globalnej pamięci podręcznej zestawów.

> [!NOTE]
> Zasady programu Publisher mają wpływ na wszystkie aplikacje korzystające ze składnika udostępnionego.

Plik konfiguracji zasad wydawcy zastępuje informacje o wersji pochodzące z aplikacji (czyli z manifestu zestawu lub z pliku konfiguracji aplikacji). Jeśli w pliku konfiguracji aplikacji nie ma instrukcji, aby przekierować wersję określoną w manifeście zestawu, plik zasad wydawcy zastępuje wersję określoną w manifeście zestawu. Jednak jeśli istnieje instrukcja przekierowywania w pliku konfiguracji aplikacji, zasady wydawcy zastępuje tę wersję, a nie określoną w manifeście.

Plik zasad wydawcy jest używany, gdy składnik udostępniony jest aktualizowany, a nowa wersja składnika udostępnionego powinna zostać pobrana przez wszystkie aplikacje używające tego składnika. Ustawienia w pliku zasad wydawcy zastępują ustawienia w pliku konfiguracji aplikacji, chyba że plik konfiguracji aplikacji wymusza tryb awaryjny.

#### <a name="safe-mode"></a>Tryb awaryjny
Pliki zasad programu Publisher są zwykle jawnie instalowane jako część dodatku Service Pack lub aktualizacji programu. Jeśli występuje problem z uaktualnionym składnikiem udostępnionym, można zignorować zastąpienia w pliku zasad wydawcy w trybie awaryjnym. Tryb awaryjny jest określany przez ** \<wydawcęPolicy apply="yes**&#124;**no"/>** element, znajdujący się tylko w pliku konfiguracji aplikacji. Określa, czy informacje o konfiguracji zasad wydawcy powinny zostać usunięte z procesu wiązania.

Tryb awaryjny można ustawić dla całej aplikacji lub dla wybranych zestawów. Oznacza to, że można wyłączyć zasady dla wszystkich zestawów, które tworzą aplikację lub włączyć ją dla niektórych zestawów, ale nie dla innych. Aby selektywnie zastosować zasady wydawcy do zestawów, które tworzą aplikację, ustaw \< ** \<wydawcęPolicja zastosuj\=nie/>** i określ, których zestawów ma być naruszone przy użyciu elementu> **zależności.** Aby zastosować zasady wydawcy do wszystkich zestawów, które tworzą aplikację, ustaw ** \<publisherPolicy apply\=no/>** bez elementów zestawu zależnego. Aby uzyskać więcej informacji o konfiguracji, zobacz [Konfigurowanie aplikacji przy użyciu plików konfiguracyjnych](../configure-apps/index.md).

### <a name="machine-configuration-file"></a>Plik konfiguracji komputera
Po trzecie, środowisko wykonawcze sprawdza plik konfiguracji komputera. Ten plik o nazwie Machine.config znajduje się na komputerze lokalnym w podkatalogu konfiguracyjnym katalogu głównego, w którym jest zainstalowane środowisko wykonawcze. Ten plik może służyć przez administratorów do określenia ograniczeń powiązania zestawu, które są lokalne dla tego komputera. Ustawienia w pliku konfiguracyjnym komputera mają pierwszeństwo przed wszystkimi innymi ustawieniami konfiguracji; nie oznacza to jednak, że wszystkie ustawienia konfiguracji powinny być umieszczone w tym pliku. Wersja określona przez plik zasad administratora jest ostateczna i nie można jej zastąpić. Zastąpienia określone w pliku Machine.config mają wpływ na wszystkie aplikacje. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie aplikacji przy użyciu plików konfiguracyjnych](../configure-apps/index.md).

<a name="step2"></a>

## <a name="step-2-checking-for-previously-referenced-assemblies"></a>Krok 2. Sprawdzanie zestawów poprzednio występujących w odwołaniu

Jeśli żądany zestaw został również żądany w poprzednich wywołaniach, środowisko uruchomieniowe języka wspólnego używa zestawu, który jest już załadowany. Może to mieć konsekwencje podczas nazewnictwa zestawów, które tworzą aplikację. Aby uzyskać więcej informacji na temat nazewnictwa zestawów, zobacz [Nazwy zestawów](../../standard/assembly/names.md).

Jeśli poprzednie żądanie dla zestawu nie powiodło się, kolejne żądania dla zestawu nie powiedzie się natychmiast bez próby załadowania zestawu. Począwszy od programu .NET Framework w wersji 2.0, błędy wiązania zestawu są buforowane, a buforowane informacje są używane do określenia, czy ma być podejmowana próba załadowania zestawu.

> [!NOTE]
> Aby przywrócić zachowanie .NET Framework w wersjach 1.0 i 1.1, które nie buforują błędów wiązania, należy [ \<uwzględnić disablecingBindingFailures> Element](../configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md) w pliku konfiguracji.

<a name="step3"></a>

## <a name="step-3-checking-the-global-assembly-cache"></a>Krok 3. Sprawdzanie globalnej pamięci podręcznej zestawów

W przypadku zestawów o silnej nazwie proces wiązania jest kontynuowany przez wyszukiwanie w globalnej pamięci podręcznej zestawów. Globalna pamięć podręczna zestawów przechowuje zestawy, które mogą być używane przez kilka aplikacji na komputerze. Wszystkie zestawy w globalnej pamięci podręcznej zestawów muszą mieć silne nazwy.

<a name="step4"></a>

## <a name="step-4-locating-the-assembly-through-codebases-or-probing"></a>Krok 4. Lokalizowanie zestawu za pośrednictwem ścieżek bazowych kodu lub sondowania

Po określeniu poprawnej wersji zestawu przy użyciu informacji w odwołaniu do zestawu wywołującego i w plikach konfiguracyjnych oraz po zaewidencjonowaniu w globalnej pamięci podręcznej zestawów (tylko dla zestawów o silnych nazwach), wspólny język runtime próbuje znaleźć zestaw. Proces lokalizowania zestawu obejmuje następujące kroki:

1. Jeśli [ \<w](../configure-apps/file-schema/runtime/codebase-element.md) pliku konfiguracji aplikacji zostanie znaleziony element codeBase>, środowisko wykonawcze sprawdza określoną lokalizację. Jeśli zostanie znaleziony dopasowania, ten zestaw jest używany i nie sondowania występuje. Jeśli zestaw nie zostanie znaleziony tam, żądanie powiązania kończy się niepowodzeniem.

2. Środowisko wykonawcze następnie sonduje dla zestawu, do którego istnieje odwołanie, przy użyciu reguł określonych w dalszej części tej sekcji.

> [!NOTE]
> Jeśli masz wiele wersji zestawu w katalogu i chcesz odwołać się do określonej wersji tego zestawu, należy użyć `privatePath` [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element zamiast atrybutu [ \<sondowania>](../configure-apps/file-schema/runtime/probing-element.md) elementu. Jeśli używasz [ \<sondowania>](../configure-apps/file-schema/runtime/probing-element.md) element, środowisko uruchomieniowe zatrzymuje sondowanie po raz pierwszy znajdzie zestaw, który pasuje do prostej nazwy zestawu, do którego odwołuje się, czy jest to poprawne dopasowanie, czy nie. Jeśli jest to poprawne dopasowanie, używany jest ten zestaw. Jeśli nie jest poprawne dopasowanie, sondowanie zatrzymuje i powiązania nie powiedzie się.

### <a name="locating-the-assembly-through-codebases"></a>Lokalizowanie zestawu za pomocą baz kodu

Informacje codebase mogą być dostarczane przy użyciu [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element w pliku konfiguracji. Ta baza kodu jest zawsze sprawdzana przed próbą sondowania środowiska wykonawczego dla zestawu, do którego istnieje odwołanie. Jeśli plik zasad wydawcy zawierający przekierowanie ostatecznej wersji zawiera również [ \<element codeBase>,](../configure-apps/file-schema/runtime/codebase-element.md) ten [ \<element codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) jest używany. Na przykład jeśli plik konfiguracji aplikacji określa [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) element, a plik zasad wydawcy, który zastępuje informacje o aplikacji określa również [ \<element codeBase>,](../configure-apps/file-schema/runtime/codebase-element.md) jest używany element [ \<codeBase>](../configure-apps/file-schema/runtime/codebase-element.md) w pliku zasad wydawcy.

Jeśli nie zostanie znalezione żadne dopasowanie w lokalizacji określonej przez [ \<element codeBase>,](../configure-apps/file-schema/runtime/codebase-element.md) żądanie powiązania kończy się niepowodzeniem i nie zostaną podjęte żadne dalsze kroki. Jeśli środowisko wykonawcze określa, że zestaw spełnia kryteria zestawu wywołującego, używa tego zestawu. Po załadowaniu pliku określonego przez danego [ \<koduBase>](../configure-apps/file-schema/runtime/codebase-element.md) element jest ładowany, środowisko wykonawcze sprawdza, czy nazwa, wersja, kultura i klucz publiczny są zgodne z odwołaniem zestawu wywołującego.

> [!NOTE]
> Zestawy, do których istnieje odwołanie poza katalogiem głównym aplikacji, muszą mieć silne nazwy i muszą być zainstalowane w globalnej pamięci podręcznej zestawów lub określone przy użyciu [ \<elementu codeBase>.](../configure-apps/file-schema/runtime/codebase-element.md)

### <a name="locating-the-assembly-through-probing"></a>Lokalizowanie zespołu za pomocą sondowania

Jeśli w pliku konfiguracji aplikacji nie ma [ \<elementu codeBase>,](../configure-apps/file-schema/runtime/codebase-element.md) sondy środowiska wykonawczego dla zestawu przy użyciu czterech kryteriów:

- Baza aplikacji, która jest lokalizacją główną, w której aplikacja jest wykonywana.

- Kultura, która jest atrybutem kultury zestawu, do którego się odwołuje.

- Nazwa, która jest nazwą zestawu, do którego istnieje odwołanie.

- `privatePath` [Atrybut \<sondowania>](../configure-apps/file-schema/runtime/probing-element.md) element, który jest zdefiniowaną przez użytkownika listą podkatalogów w lokalizacji głównej. Tę lokalizację można określić w pliku konfiguracji aplikacji <xref:System.AppDomainSetup.PrivateBinPath?displayProperty=nameWithType> i w kodzie zarządzanym przy użyciu właściwości dla domeny aplikacji. Po określeniu w kodzie zarządzanym kod `privatePath` zarządzany jest badany jako pierwszy, a następnie ścieżka określona w pliku konfiguracji aplikacji.

#### <a name="probing-the-application-base-and-culture-directories"></a>Sondowanie katalogów bazy aplikacji i kultury

Środowisko wykonawcze zawsze rozpoczyna sondowanie w bazie aplikacji, która może być adresem URL lub katalogiem głównym aplikacji na komputerze. Jeśli zestaw, do którego istnieje odwołanie, nie zostanie znaleziony w bazie aplikacji i nie podano żadnych informacji o kulturze, środowisko wykonawcze przeszukuje wszystkie podkatalogi o nazwie zestawu. Badane katalogi obejmują:

- [baza aplikacji] / [nazwa zestawu].dll

- [baza aplikacji] / [nazwa zestawu] / [nazwa zestawu].dll

Jeśli informacje o kulturze są określone dla zestawu, do którego istnieje odwołanie, badane są tylko następujące katalogi:

- [baza aplikacji] / [kultura] / [nazwa zestawu].dll

- [baza aplikacji] / [kultura] / [nazwa zestawu] / [nazwa zestawu].dll

#### <a name="probing-with-the-privatepath-attribute"></a>Sondowanie za pomocą atrybutu privatePath

Oprócz podkatalogów kultury i podkatalogów nazwanych dla zestawu, do którego istnieje odwołanie, środowisko wykonawcze sonduje również katalogi określone przy użyciu `privatePath` atrybutu elementu [ \<sondowania>.](../configure-apps/file-schema/runtime/probing-element.md) Katalogi określone przy `privatePath` użyciu atrybutu muszą być podkatalogami katalogu głównego aplikacji. Badane katalogi różnią się w zależności od tego, czy informacje o kulturze są zawarte w żądaniu zestawu, do którego istnieje odwołanie.

Środowisko wykonawcze zatrzymuje sondowanie po raz pierwszy znajdzie zestaw, który pasuje do prostej nazwy zestawu, do którego odwołuje się, czy jest to poprawne dopasowanie, czy nie. Jeśli jest to poprawne dopasowanie, używany jest ten zestaw. Jeśli nie jest poprawne dopasowanie, sondowanie zatrzymuje i powiązania nie powiedzie się.

Jeśli kultura jest uwzględniona, badane są następujące katalogi:

- [baza aplikacji] / [binpath] / [culture] / [nazwa zestawu].dll

- [baza aplikacji] / [binpath] / [culture] / [nazwa zestawu] / [nazwa zestawu].dll

Jeśli informacje o kulturze nie są uwzględniane, badane są następujące katalogi:

- [baza aplikacji] / [binpath] / [nazwa zestawu].dll

- [baza aplikacji] / [binpath] / [nazwa zestawu] / [nazwa zestawu].dll

#### <a name="probing-examples"></a>Sondowanie przykładów

Biorąc pod uwagę następujące informacje:

- Nazwa zestawu, do którego istnieje odwołanie: myAssembly

- Katalog główny aplikacji:`http://www.code.microsoft.com`

- sondowanie>element w pliku konfiguracyjnym określa: bin [ \<](../configure-apps/file-schema/runtime/probing-element.md)

- Kultura: de

Środowisko wykonawcze sonduje następujące adresy URL:

- `http://www.code.microsoft.com/de/myAssembly.dll`

- `http://www.code.microsoft.com/de/myAssembly/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly.dll`

- `http://www.code.microsoft.com/bin/de/myAssembly/myAssembly.dll`

##### <a name="multiple-assemblies-with-the-same-name"></a>Wiele zestawów o tej samej nazwie

W poniższym przykładzie pokazano, jak skonfigurować wiele zestawów o tej samej nazwie.

```xml
<dependentAssembly>
   <assemblyIdentity name="Server" publicKeyToken="c0305c36380ba429" />
   <codeBase version="1.0.0.0" href="v1/Server.dll" />
   <codeBase version="2.0.0.0" href="v2/Server.dll" />
</dependentAssembly>
```

#### <a name="other-locations-probed"></a>Inne lokalizacje badane

Lokalizacja zestawu można również określić przy użyciu bieżącego kontekstu wiązania. To najczęściej występuje, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> gdy metoda jest używana i w scenariuszach współdziałać COM. Jeśli zestaw używa <xref:System.Reflection.Assembly.LoadFrom%2A> metody do odwoływania się do innego zestawu, lokalizacja zestawu wywołującego jest uważana za wskazówkę o tym, gdzie można znaleźć zestaw, do którego istnieje odwołanie. Jeśli zostanie znaleziony dopasowanie, ten zestaw jest ładowany. Jeśli nie zostanie znaleziony żaden mecz, środowisko wykonawcze kontynuuje semantyce wyszukiwania, a następnie wysyła zapytanie do Instalatora Windows, aby zapewnić zestaw. Jeśli nie zestaw jest pod warunkiem, że pasuje do żądania powiązania, wyjątek. Ten wyjątek <xref:System.TypeLoadException> jest w kodzie zarządzanym, <xref:System.IO.FileNotFoundException> jeśli odwołuje się do typu lub jeśli nie znaleziono zestawu ładowanego.

Na przykład jeśli Assembly1 odwołuje Assembly2 i Assembly1 został pobrany z `http://www.code.microsoft.com/utils`, że lokalizacja jest uważany za wskazówkę o tym, gdzie można znaleźć Assembly2.dll. Środowisko wykonawcze następnie sonduje `http://www.code.microsoft.com/utils/Assembly2.dll` dla `http://www.code.microsoft.com/utils/Assembly2/Assembly2.dll`zestawu w i . Jeśli Assembly2 nie zostanie znaleziony w żadnej z tych lokalizacji, środowisko wykonawcze wysyła zapytanie do Instalatora Windows.

## <a name="see-also"></a>Zobacz też

- [Najlepsze praktyki dotyczące ładowania zestawu](best-practices-for-assembly-loading.md)
- [Wdrożenie](index.md)
