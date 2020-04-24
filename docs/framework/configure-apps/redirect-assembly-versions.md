---
title: Przekierowywanie wersji zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
ms.openlocfilehash: 0d55171e37ec056b3470d238a60bc32f2feb04fb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646042"
---
# <a name="redirecting-assembly-versions"></a>Przekierowywanie wersji zestawu

Można przekierować odwołania do wiązania w czasie kompilacji do zestawów .NET Framework, zestawów innych firm lub zestawów własnej aplikacji. Możesz przekierować aplikację, aby używała innej wersji zestawu na wiele sposobów: za pośrednictwem zasad wydawcy, za pośrednictwem pliku konfiguracji aplikacji; lub za pośrednictwem pliku konfiguracyjnego urządzenia. W tym artykule omówiono sposób działania powiązania zestawu w ramach .NET Framework i jak można go skonfigurować.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Ujednolicenie zestawu i domyślne powiązanie
 Powiązania do zestawów .NET Framework są czasami przekierowywane przez proces zwany *unifikacji zestawu*. .NET Framework składa się z wersji środowiska wykonawczego języka wspólnego i około dwóch tuzinów .NET Framework zestawów, które tworzą bibliotekę typów. Te zestawy .NET Framework są traktowane przez środowisko wykonawcze jako pojedyncza jednostka. Domyślnie po uruchomieniu aplikacji wszystkie odwołania do typów w kodzie uruchamianym przez środowisko wykonawcze są kierowane do zestawów .NET Framework, które mają ten sam numer wersji co środowisko wykonawcze, które jest ładowane w procesie. Przekierowania, które występują w tym modelu są domyślne zachowanie dla środowiska wykonawczego.

 Na przykład jeśli aplikacja odwołuje się do typów w obszarze nazw System.XML i został zbudowany przy użyciu programu .NET Framework 4.5, zawiera statyczne odwołania do zestawu System.XML, który jest dostarczany ze środowiska wykonawczego w wersji 4.5. Jeśli chcesz przekierować odwołanie do powiązania, aby wskazać zestaw System.XML dostarczany z programem .NET Framework 4, możesz umieścić informacje o przekierowaniu w pliku konfiguracji aplikacji. Przekierowanie powiązania w pliku konfiguracji dla ujednoliconego zestawu .NET Framework anuluje ujednolicenie dla tego zestawu.

 Ponadto można ręcznie przekierować powiązanie zestawu dla zestawów innych firm, jeśli dostępnych jest wiele wersji.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Przekierowywanie wersji zestawu przy użyciu zasad wydawcy
 Dostawcy zestawów mogą kierować aplikacje do nowszej wersji zestawu, dołączając plik zasad wydawcy z nowym zestawem. Plik zasad wydawcy, który znajduje się w globalnej pamięci podręcznej zestawów, zawiera ustawienia przekierowania zestawu.

 Każdy *większy*. *wersja pomocnicza* zestawu ma własny plik zasad wydawcy. Na przykład przekierowania z wersji 2.0.2.222 do 2.0.3.000 i z wersji 2.0.2.321 do wersji 2.0.3.000 zarówno przejść do tego samego pliku, ponieważ są one związane z wersją 2.0. Jednak przekierowanie z wersji 3.0.0.999 do wersji 4.0.0.000 przechodzi do pliku dla wersji 3.0.999. Każda główna wersja programu .NET Framework ma własny plik zasad wydawcy.

 Jeśli plik zasad wydawcy istnieje dla zestawu, środowisko wykonawcze sprawdza ten plik po sprawdzeniu pliku manifestu i konfiguracji aplikacji zestawu. Dostawcy powinni używać plików zasad wydawcy tylko wtedy, gdy nowy zestaw jest wstecznie zgodny z zestawem przekierowywanym.

 Zasady wydawcy aplikacji można pominąć, określając ustawienia w pliku konfiguracji aplikacji, zgodnie z omówieniem w [sekcji Pomijanie zasad wydawcy](#bypass_PP).

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Przekierowywanie wersji zestawu na poziomie aplikacji
 Istnieje kilka różnych technik zmiany zachowania powiązania dla aplikacji za pośrednictwem pliku konfiguracji aplikacji: można ręcznie edytować plik, można polegać na automatycznym przekierowywaniu powiązania lub można określić zachowanie powiązania, pomijając zasady wydawcy.

### <a name="manually-editing-the-app-config-file"></a>Ręczna edycja pliku konfiguracyjnego aplikacji
 Można ręcznie edytować plik konfiguracji aplikacji, aby rozwiązać problemy z montażem. Na przykład jeśli dostawca może zwolnić nowszą wersję zestawu, który używa aplikacji bez dostarczania zasad wydawcy, ponieważ nie gwarantują one zgodność z powrotem, można skierować aplikację do korzystania z nowszej wersji zestawu, umieszczając informacje wiązania zestawu w pliku konfiguracji aplikacji w następujący sposób.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Poleganie na automatycznym przekierowywaniu powiązania

Podczas tworzenia aplikacji klasycznej w programie Visual Studio, która jest przeznaczona dla programu .NET Framework 4.5.1 lub nowszej wersji, aplikacja używa automatycznego przekierowywania powiązania. Oznacza to, że jeśli dwa składniki odwołują się do różnych wersji tego samego zestawu o silnej nazwie, środowisko wykonawcze automatycznie dodaje przekierowanie powiązania do nowszej wersji zestawu w pliku konfiguracji aplikacji wyjściowej (app.config). To przekierowanie zastępuje ujednolicenie zestawu, które w przeciwnym razie może mieć miejsce. Źródłowy plik app.config nie jest modyfikowany. Załóżmy na przykład, że aplikacja bezpośrednio odwołuje się do składnika programu .NET Framework poza pasmem, ale używa biblioteki innej firmy przeznaczonej dla starszej wersji tego samego składnika. Podczas kompilowania aplikacji plik konfiguracji aplikacji wyjściowej jest modyfikowany w celu ograniczenia przekierowania powiązania do nowszej wersji składnika. Jeśli utworzysz aplikację sieci web, otrzymasz ostrzeżenie kompilacji dotyczące konfliktu powiązania, co z kolei daje możliwość dodania niezbędnego przekierowania powiązania do źródłowego pliku konfiguracji sieci Web.

Jeśli ręcznie dodać przekierowania powiązania do pliku source app.config, w czasie kompilacji visual studio próbuje ujednolicić zestawy na podstawie przekierowań powiązania, które zostały dodane. Załóżmy na przykład, że wstawisz następujące przekierowanie powiązania dla zestawu:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Jeśli inny projekt w aplikacji odwołuje się do wersji 1.0.0.0 tego samego zestawu, automatyczne przekierowywanie powiązania dodaje następujący wpis do pliku output app.config, dzięki czemu aplikacja jest ujednolicona w wersji 2.0.0.0 tego zestawu:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Można włączyć automatyczne przekierowanie powiązania, jeśli aplikacja jest przeznaczona dla starszych wersji programu .NET Framework. To domyślne zachowanie można zastąpić, udostępniając informacje o przekierowaniu powiązania w pliku app.config dla dowolnego zestawu lub wyłączając funkcję przekierowania powiązania. Aby uzyskać informacje dotyczące włączania lub wyłączania tej funkcji, zobacz [Jak: Włączanie i wyłączanie automatycznego przekierowania powiązania](how-to-enable-and-disable-automatic-binding-redirection.md).

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Pomijanie zasad wydawcy
 W razie potrzeby można zastąpić zasady wydawcy w pliku konfiguracji aplikacji. Na przykład nowe wersje zestawów, które twierdzą, że są zgodne wstecznie nadal można przerwać aplikację. Jeśli chcesz pominąć zasady wydawcy, dodaj [ \<wydawcęPolicy>](./file-schema/runtime/publisherpolicy-element.md) element do [ \<elementu zależnegoAsześci>](./file-schema/runtime/dependentassembly-element.md) w pliku konfiguracji aplikacji i ustaw atrybut **apply** na **nie**, który zastępuje wszystkie poprzednie ustawienia **tak.**

 `<publisherPolicy apply="no" />`

 Pomiń zasady wydawcy, aby aplikacja była uruchomiona dla użytkowników, ale upewnij się, że problem został zgłosiny dostawcy zestawu. Jeśli zestaw ma plik zasad wydawcy, dostawca powinien upewnić się, że zestaw jest wstecznie zgodny i że klienci mogą używać nowej wersji w miarę możliwości.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Przekierowywanie wersji montażowych na poziomie maszyny
 Może się wydawać, że rzadko zdarza się, gdy administrator komputera chce, aby wszystkie aplikacje na komputerze używały określonej wersji zestawu. Na przykład administrator może chcieć, aby każda aplikacja używała określonej wersji zestawu, ponieważ ta wersja rozwiązuje dziurę w zabezpieczeniach. Jeśli zestaw zostanie przekierowany w pliku konfiguracyjnym komputera, wszystkie aplikacje na tym komputerze, które używają starej wersji, zostaną skierowane do użycia nowej wersji. Plik konfiguracji komputera zastępuje plik konfiguracji aplikacji i plik zasad wydawcy. Ten plik znajduje się w*ścieżce instalacji*% środowiska wykonawczego %\Config. Zazwyczaj program .NET Framework jest instalowany w katalogu %drive%\Windows\Microsoft.NET\Framework.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Określanie powiązania złożenia w plikach konfiguracyjnych
 Ten sam format XML służy do określania przekierowań powiązania, niezależnie od tego, czy znajduje się on w pliku konfiguracji aplikacji, pliku konfiguracyjnym komputera, czy w pliku zasad wydawcy. Aby przekierować jedną wersję zestawu do innej, należy użyć [ \<bindingRedirect>](./file-schema/runtime/bindingredirect-element.md) element. Atrybut **oldVersion** można określić wersję zestawu pojedynczego lub zakresu wersji. Atrybut `newVersion` należy określić pojedynczą wersję.  Na przykład `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` określa, że środowisko wykonawcze należy używać wersji 2.0.0.0 zamiast wersji zestawu między 1.1.0.0 i 1.2.0.0.

 Poniższy przykład kodu pokazuje różne scenariusze przekierowania powiązania. W przykładzie określono przekierowanie dla `myAssembly`zakresu wersji dla programu `mySecondAssembly`, oraz pojedyncze przekierowanie powiązania dla programu . W przykładzie określono również, że plik zasad wydawcy `myThirdAssembly`nie zastąpi przekierowań powiązania dla programu .

 Aby powiązać zestaw, należy określić ciąg "urn:schemas-microsoft-com:asm.v1" z atrybutem **xmlns** w [ \<tagu>zestawu.](./file-schema/runtime/assemblybinding-element-for-runtime.md)

```xml
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="myAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
        <!-- Assembly versions can be redirected in app,
          publisher policy, or machine configuration files. -->
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
        <assemblyIdentity name="mySecondAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
      <assemblyIdentity name="myThirdAssembly"
        publicKeyToken="32ab4ba45e0a69a1"
        culture="en-us" />
        <!-- Publisher policy can be set only in the app
          configuration file. -->
        <publisherPolicy apply="no" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Ograniczanie powiązań zestawu do określonej wersji
 Można użyć **appliesTo** atrybut na [ \<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element w pliku konfiguracji aplikacji, aby przekierować odwołania wiązania zestawu do określonej wersji programu .NET Framework. Ten atrybut opcjonalny używa numeru wersji programu .NET Framework, aby wskazać, jakiej wersji dotyczy. Jeśli nie **appliesTo** atrybut jest określony, [ \<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element ma zastosowanie do wszystkich wersji programu .NET Framework.

 Na przykład, aby przekierować powiązanie zestawu dla zestawu .NET Framework 3.5, należy dołączyć następujący kod XML w pliku konfiguracji aplikacji.

```xml
<runtime>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"
    appliesTo="v3.5">
    <dependentAssembly>
      <!-- assembly information goes here -->
    </dependentAssembly>
  </assemblyBinding>
</runtime>
```

 Informacje o przekierowaniu należy wprowadzić w kolejności wersji. Na przykład wprowadź informacje o przekierowywaniu powiązania zestawu dla zestawów .NET Framework 3.5, po których następują zestawy .NET Framework 4.5. Na koniec wprowadź informacje o przekierowywaniu powiązania zestawu dla dowolnego przekierowania zestawu .NET Framework, który nie używa atrybutu **appliesTo** i dlatego ma zastosowanie do wszystkich wersji programu .NET Framework. Jeśli występuje konflikt w przekierowaniu, używana jest pierwsza pasująca instrukcja przekierowania w pliku konfiguracyjnym.

 Na przykład, aby przekierować jedno odwołanie do zestawu .NET Framework 3.5 i inne odwołanie do zestawu .NET Framework 4, użyj wzorca pokazanego w poniższym pseudokodem.

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a>Zobacz też

- [Porady: włączanie i wyłączanie automatycznego przekierowania powiązań](how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<element> bindingRedirect](./file-schema/runtime/bindingredirect-element.md)
- [Uprawnienia zabezpieczeń przekierowania powiązania zestawu](assembly-binding-redirection-security-permission.md)
- [Zestawy w środowisku .NET](../../standard/assembly/index.md)
- [Programowanie za pomocą zestawów](../../standard/assembly/index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji](index.md)
- [Schemat ustawień środowiska uruchomieniowego](./file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](./file-schema/index.md)
- [Instrukcje: tworzenie zasad wydawcy](how-to-create-a-publisher-policy.md)
