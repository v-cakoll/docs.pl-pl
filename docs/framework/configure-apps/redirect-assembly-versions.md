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
ms.openlocfilehash: c9670b00ea4a6b552469b7f33e924b8ab128d9d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948026"
---
# <a name="redirecting-assembly-versions"></a>Przekierowywanie wersji zestawu

Odwołania do powiązań w czasie kompilacji można przekierować do zestawów .NET Framework, zestawów stron trzecich lub zestawów aplikacji. Możesz przekierować aplikację do korzystania z innej wersji zestawu na wiele sposobów: za pomocą zasad wydawcy w pliku konfiguracji aplikacji; lub za pomocą pliku konfiguracji komputera. W tym artykule omówiono sposób działania powiązania zestawu w .NET Framework i sposobu jego konfiguracji.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Ujednolicenie zestawu i powiązanie domyślne
 Powiązania z zestawami .NET Framework czasami są przekierowane przez proces nazywany dezjednoczeniem *zestawu*. .NET Framework składa się z wersji środowiska uruchomieniowego języka wspólnego oraz o dwóch dziesiątych zestawach .NET Framework tworzących bibliotekę typów. Te zestawy .NET Framework są traktowane przez środowisko uruchomieniowe jako pojedynczą jednostkę. Domyślnie po uruchomieniu aplikacji wszystkie odwołania do typów w kodzie wykonywane przez środowisko uruchomieniowe są kierowane do zestawów .NET Framework, które mają ten sam numer wersji, co środowisko uruchomieniowe, które jest ładowane w procesie. Przekierowania, które występują w tym modelu, są domyślnym zachowaniem środowiska uruchomieniowego.

 Na przykład jeśli aplikacja odwołuje się do typów w przestrzeni nazw System. XML i została skompilowana przy użyciu .NET Framework 4,5, zawiera statyczne odwołania do zestawu System. XML, który jest dostarczany ze środowiskiem uruchomieniowym w wersji 4,5. Jeśli chcesz przekierować odwołanie do powiązania, aby wskazywało zestaw system. XML dostarczany z .NET Framework 4, możesz umieścić informacje o przekierowaniu w pliku konfiguracji aplikacji. Przekierowanie powiązania w pliku konfiguracyjnym dla ujednoliconego zestawu .NET Framework anuluje ujednolicenie tego zestawu.

 Ponadto możesz chcieć ręcznie przekierować powiązanie zestawu dla zestawów innych firm, jeśli jest dostępnych wiele wersji.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Przekierowywanie wersji zestawu przy użyciu zasad wydawcy
 Dostawcy zestawów mogą kierować aplikacje do nowszej wersji zestawu, dołączając plik zasad wydawcy z nowym zestawem. Plik zasad wydawcy, który znajduje się w globalnej pamięci podręcznej zestawów, zawiera ustawienia przekierowania zestawu.

 Każda *główna*. wersja pomocnicza zestawu ma swój własny plik zasad wydawcy. Na przykład przekierowania z wersji 2.0.2.222 do 2.0.3.000 i z wersji 2.0.2.321 do wersji 2.0.3.000 oba przechodzą do tego samego pliku, ponieważ są one skojarzone z wersją 2,0. Jednak przekierowanie z wersji 3.0.0.999 do wersji 4.0.0.000 przejdzie do pliku w wersji 3.0.999. Każda główna wersja .NET Framework ma swój własny plik zasad wydawcy.

 Jeśli plik zasad wydawcy istnieje dla zestawu, środowisko uruchomieniowe sprawdzi ten plik po sprawdzeniu pliku konfiguracji manifestu i aplikacji. Dostawcy powinni używać plików zasad wydawcy tylko wtedy, gdy nowy zestaw jest zgodny z poprzednimi wersjami z przekierowanym zestawem.

 Zasady wydawcy można ominąć dla aplikacji, określając Ustawienia w pliku konfiguracji aplikacji, zgodnie z opisem w [sekcji pomijanie zasad wydawcy](#bypass_PP).

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Przekierowywanie wersji zestawu na poziomie aplikacji
 Istnieje kilka różnych technik zmiany zachowania powiązania aplikacji za pomocą pliku konfiguracji aplikacji: można ręcznie edytować plik, można polegać na automatycznym przekierowaniu powiązań lub można określić zachowanie powiązania, pomijając zasady wydawcy.

### <a name="manually-editing-the-app-config-file"></a>Ręczne edytowanie pliku konfiguracji aplikacji
 Możesz ręcznie edytować plik konfiguracji aplikacji, aby rozwiązać problemy z zestawem. Na przykład, jeśli dostawca może wydać nowszą wersję zestawu, którego używa aplikacja bez dostarczania zasad wydawcy, ponieważ nie zapewniają zgodności z poprzednimi wersjami, można skierować aplikację do korzystania z nowszej wersji zestawu przez umieszczenie zestawu Powiąż informacje w pliku konfiguracyjnym aplikacji w następujący sposób.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Poleganie na automatycznym przekierowaniu powiązań

Po utworzeniu aplikacji klasycznej w programie Visual Studio, która jest przeznaczona dla .NET Framework 4.5.1 lub nowszej wersji, aplikacja używa automatycznego przekierowywania powiązań. Oznacza to, że jeśli dwa składniki odwołują się do różnych wersji tego samego zestawu o silnej nazwie, środowisko uruchomieniowe automatycznie dodaje przekierowanie powiązania do nowszej wersji zestawu w pliku konfiguracji aplikacji wyjściowej (App. config). To przekierowanie zastępuje Montaż zestawu, który może być w innym przypadku. Źródłowy plik app.config nie jest modyfikowany. Załóżmy na przykład, że aplikacja bezpośrednio odwołuje się do składnika .NET Framework poza pasmem, ale używa biblioteki innej firmy, która jest przeznaczona dla starszej wersji tego samego składnika. Podczas kompilowania aplikacji plik konfiguracji aplikacji wyjściowej jest modyfikowany tak, aby zawierał przekierowanie powiązania do nowszej wersji składnika. W przypadku tworzenia aplikacji sieci Web zostanie wyświetlone ostrzeżenie dotyczące kompilacji dotyczące konfliktu powiązania, co z kolei umożliwia dodanie niezbędnego przekierowania powiązania do źródłowego pliku konfiguracji sieci Web.

Jeśli ręcznie dodasz przekierowania powiązań do pliku źródłowego App. config, w czasie kompilacji program Visual Studio podejmie próbę ujednolicenia zestawów na podstawie dodanych przekierowań powiązań. Załóżmy na przykład, że wstawisz następujące przekierowanie powiązania dla zestawu:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Jeśli inny projekt w aplikacji odwołuje się do wersji 1.0.0.0 tego samego zestawu, automatyczne przekierowanie powiązań dodaje następujący wpis do pliku Output App. config, aby aplikacja była ujednolicona w wersji 2.0.0.0 tego zestawu:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Automatyczne przekierowywanie powiązań można włączyć, jeśli aplikacja jest przeznaczona dla starszych wersji .NET Framework. To zachowanie domyślne można przesłonić, dostarczając informacje o przekierowaniu powiązań w pliku App. config dla dowolnego zestawu lub wyłączając funkcję przekierowywania powiązań. Aby uzyskać informacje na temat włączania lub wyłączania tej funkcji [, zobacz How to: Włączanie i wyłączanie automatycznego przekierowywania](how-to-enable-and-disable-automatic-binding-redirection.md)powiązań.

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Pomijanie zasad wydawcy
 W razie potrzeby można zastąpić zasady wydawcy w pliku konfiguracji aplikacji. Na przykład nowe wersje zestawów, które są zgodne z poprzednimi wersjami, mogą nadal przerwać aplikację. Aby obejść zasady wydawcy, Dodaj [ \<element publisherPolicy Apply >](./file-schema/runtime/publisherpolicy-element.md) do [ \<elementu dependentAssembly >](./file-schema/runtime/dependentassembly-element.md) w pliku konfiguracji aplikacji, a następnie ustaw dla atrybutu **Zastosuj** wartość **nie**. zastępuje wszystkie poprzednie ustawienia **tak** .

 `<publisherPolicy apply="no" />`

 Pomiń zasady wydawcy, aby zachować swoją aplikację dla użytkowników, ale upewnij się, że problem został zaraportowany do dostawcy zestawu. Jeśli zestaw ma plik zasad wydawcy, dostawca powinien upewnić się, że zestaw jest zgodny z poprzednimi wersjami, a klienci mogą korzystać z nowej wersji tak jak to możliwe.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Przekierowywanie wersji zestawu na poziomie komputera
 Mogą wystąpić sytuacje sytuacje, w których administrator komputera chce, aby wszystkie aplikacje na komputerze korzystały z określonej wersji zestawu. Na przykład administrator może chcieć, aby każda aplikacja korzystała z określonej wersji zestawu, ponieważ ta wersja naprawia lukę w zabezpieczeniach. Jeśli zestaw zostanie przekierowany w pliku konfiguracyjnym maszyny, wszystkie aplikacje na tym komputerze, które używają starej wersji, będą kierowane do korzystania z nowej wersji. Plik konfiguracji komputera zastępuje plik konfiguracji aplikacji i plik zasad wydawcy. Ten plik znajduje się w katalogu% \ config*instalacji systemu plików wykonywalnych*. Zwykle .NET Framework jest instalowany w katalogu%drive%\Windows\Microsoft.NET\Framework.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Określanie powiązania zestawu w plikach konfiguracji
 Ten sam format XML służy do określania przekierowań powiązań niezależnie od tego, czy znajduje się on w pliku konfiguracji aplikacji, pliku konfiguracji komputera czy pliku zasad wydawcy. Aby przekierować jedną wersję zestawu do innej, użyj [ \<elementu bindingRedirect >](./file-schema/runtime/bindingredirect-element.md) . Atrybut **oldVersion** może określać jedną wersję zestawu lub zakres wersji. Ten `newVersion` atrybut powinien określać jedną wersję.  Na przykład `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` określa, że środowisko uruchomieniowe ma używać wersji 2.0.0.0 zamiast wersji zestawu między 1.1.0.0 i 1.2.0.0.

 Poniższy przykład kodu demonstruje różne scenariusze przekierowania powiązań. W tym przykładzie określono przekierowanie dla zakresu wersji programu `myAssembly`oraz przekierowanie pojedynczego powiązania dla. `mySecondAssembly` W przykładzie określono również, że plik zasad wydawcy nie przesłania przekierowań powiązań dla programu `myThirdAssembly`.

 Aby powiązać zestaw, należy określić ciąg "urn: schematys-Microsoft-com: ASM. v1" z atrybutem **xmlns** w [ \<tagu > zestawubinding](./file-schema/runtime/assemblybinding-element-for-runtime.md) .

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
 Można użyć atrybutu **AppliesTo** w [ \<elemencie assemblyBinding >](./file-schema/runtime/assemblybinding-element-for-runtime.md) w pliku konfiguracyjnym aplikacji, aby przekierować odwołania do powiązań zestawów do określonej wersji .NET Framework. Ten opcjonalny atrybut używa numeru wersji .NET Framework, aby wskazać, której wersji dotyczy. Jeśli nie **appliesTo** atrybut jest określony, [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) element ma zastosowanie do wszystkich wersji programu .NET Framework.

 Na przykład aby przekierować powiązanie zestawu dla zestawu .NET Framework 3,5, należy dołączyć następujący kod XML do pliku konfiguracji aplikacji.

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

 Należy wprowadzić informacje o przekierowaniu w kolejności wersji. Na przykład wprowadź informacje o przekierowaniach powiązań zestawów dla zestawów .NET Framework 3,5, a następnie zestawy .NET Framework 4,5. Na koniec wprowadź informacje o przekierowaniu powiązań zestawów dla dowolnego przekierowania zestawu .NET Framework, który nie używa atrybutu **AppliesTo** i w związku z tym ma zastosowanie do wszystkich wersji .NET Framework. W przypadku konfliktu w przekierowaniu zostanie użyta pierwsza zgodna instrukcja przekierowania w pliku konfiguracji.

 Na przykład, aby przekierować jedno odwołanie do zestawu .NET Framework 3,5 i innego odwołania do zestawu .NET Framework 4, użyj wzorca pokazanego w poniższym pseudokodzie.

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

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Włączanie i wyłączanie automatycznego przekierowywania powiązań](how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect> Element](./file-schema/runtime/bindingredirect-element.md)
- [Uprawnienia zabezpieczeń przekierowania powiązania zestawu](assembly-binding-redirection-security-permission.md)
- [Zestawy w środowisku uruchomieniowym CLR](../app-domains/assemblies-in-the-common-language-runtime.md)
- [Programowanie za pomocą zestawów](../app-domains/programming-with-assemblies.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji](index.md)
- [Schemat ustawień środowiska uruchomieniowego](./file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](./file-schema/index.md)
- [Instrukcje: Tworzenie zasad wydawcy](how-to-create-a-publisher-policy.md)
