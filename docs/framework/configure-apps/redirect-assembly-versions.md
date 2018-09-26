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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c4c96b874456297ede61c96e46fee8d90ebcafb6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231226"
---
# <a name="redirecting-assembly-versions"></a>Przekierowywanie wersji zestawu

Możesz przekierować odwołania związane z czasem kompilacji do zestawów .NET Framework, zestawów innych firm lub zestawów Twojej własnej aplikacji. Można przekierować aplikację do używania różnych wersji zestawu na różne sposoby: za pomocą zasad wydawcy, za pomocą pliku konfiguracji aplikacji; lub za pomocą pliku konfiguracji komputera. W tym artykule omówiono, jak działa powiązanie zestawu w programie .NET Framework i jak można skonfigurować.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Unifikacja zestawów i powiązania domyślne
 Powiązania do zestawów .NET Framework czasami są przekierowywane w procesie zwanym *unifikacja zestawu*. .NET Framework składa się z wersją środowiska uruchomieniowego języka wspólnego i około dwóch tuzinów zestawów .NET Framework, które tworzą bibliotekę typów. Te zestawy .NET Framework są traktowane w czasie wykonywania jako pojedyncza jednostka. Domyślnie gdy aplikacja jest uruchamiana, wszystkie odwołania do typów w kodzie wykonywanym przez środowisko uruchomieniowe są kierowane do zestawów .NET Framework, które mają ten sam numer wersji środowiska uruchomieniowego, który jest załadowany w procesie. Przekierowań, które występują w tym modelu są domyślnym zachowaniem dla środowiska uruchomieniowego.

 Na przykład, jeśli aplikacja odwołuje się do typów w przestrzeni nazw System.XML i została skompilowana przy użyciu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zawiera odwołania statyczne do zestawu System.XML, który jest dostarczany za pomocą środowiska uruchomieniowego w wersji 4.5. Chcąc przekierować odwołanie powiązania tak, aby wskazywać zestaw System.XML dostarczany z .NET Framework 4, możesz umieścić informacje o przekierowaniu w pliku konfiguracji aplikacji. Przekierowanie powiązania w pliku konfiguracji dla ujednoliconego zestawu .NET Framework anuluje ujednolicenie dla tego zestawu.

 Ponadto możesz chcieć ręcznie przekierować powiązanie zestawu dla zestawów innych firm, jeśli istnieje wiele wersji.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Przekierowanie wersji zestawu przy użyciu zasad wydawcy
 Dostawcy zestawów mogą przekierować aplikacje do nowszej wersji zestawu, dołączając plik zasad wydawcy z nowego zestawu. Plik zasad wydawcy, który znajduje się w globalnej pamięci podręcznej, zawiera ustawienia przekierowywania zestawu.

 Każdy *głównych*. *drobne* wersja zestawu ma swój własny plik zasad wydawcy. Na przykład przekierowania z wersji 2.0.2.222 do 2.0.3.000 i z wersji 2.0.2.321 do wersji 2.0.3.000 idą do tego samego pliku, ponieważ są one związane z wersją 2.0. Jednakże przekierowanie z wersji 3.0.0.999 do wersji 4.0.0.000 wchodzi przechodzi do pliku dla wersji 3.0.999. Każda główna wersja środowiska .NET Framework ma swój własny plik zasad wydawcy.

 Jeśli plik zasad wydawcy istnieje dla zestawu, środowisko uruchomieniowe sprawdza ten plik po sprawdzeniu pliku konfiguracji aplikacji i manifest zestawu. Dostawcy powinni używać plików zasad wydawcy tylko wtedy, gdy nowy zestaw jest zgodny z poprzednimi wersjami z przekierowywanego zestawu.

 Można pominąć zasad wydawcy dla twojej aplikacji poprzez określenie ustawień w pliku konfiguracji aplikacji, zgodnie z opisem w [pomijanie sekcji zasad wydawcy](#bypass_PP).

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Przekierowanie wersji zestawu na poziomie aplikacji
 Istnieje kilka różnych technik zmieniania zachowania powiązania dla swojej aplikacji za pomocą pliku konfiguracji aplikacji: możesz ręcznie edytować plik, możesz polegać na automatyczne przekierowywanie powiązań lub możesz określić zachowanie powiązania, pomijając zasady wydawcy.

### <a name="manually-editing-the-app-config-file"></a>Ręczna Edycja pliku konfiguracyjnego aplikacji
 Można ręcznie edytować pliku konfiguracji aplikacji w celu rozwiązania problemów ze złożeniem. Na przykład jeśli dostawca wydaje nowszą wersję zestawu, który aplikacja używa bez podania zasad wydawcy, ponieważ nie gwarantują one zgodności z poprzednimi wersjami, należy skierować aplikację do korzystania z nowszej wersji zestawu poprzez umieszczenie zestawu powiązania następujące informacje w pliku konfiguracyjnym aplikacji.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Opierając się na automatyczne przekierowywanie powiązań

Po utworzeniu aplikacji klasycznej w programie Visual Studio przeznaczonych [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] lub jego nowsza wersja aplikacji używa automatycznego przekierowywania powiązań. Oznacza to, że jeśli dwa składniki odwołują się do różnych wersji tego samego zestawu z silną nazwą, — środowisko uruchomieniowe automatycznie dodaje przekierowanie powiązań do nowszej wersji zestawu w pliku konfiguracyjnym (app.config) danych wyjściowych aplikacji. Przekierowanie zastępuje unifikację zestawów, w przeciwnym razie może mieć miejsce. Źródłowy plik app.config nie jest modyfikowany. Załóżmy na przykład, że Twoja aplikacja bezpośrednio odwołuje się do składnik .NET Framework out-of-band ale używa biblioteki innej firmy, który jest przeznaczony dla starszej wersji tego samego składnika. Podczas kompilowania aplikacji wyjściowy plik konfiguracji aplikacji jest modyfikowany do przez dołączenie przekierowania powiązania do nowszej wersji składnika. Jeśli tworzysz aplikację sieci web, pojawi się ostrzeżenie kompilacji dotyczące konfliktu powiązania, co z kolei daje możliwość dodania niezbędnego przekierowania powiązania do źródłowego pliku konfiguracji sieci web.

Jeśli ręcznie dodasz przekierowania powiązań do pliku app.config źródła, w czasie kompilacji, Visual Studio próbuje ujednolicić zestawy w oparciu o przekierowania powiązań dodane. Załóżmy na przykład, że wstawiasz następujące przekierowanie powiązania dla zestawu:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Jeśli w wersji 1.0.0.0 tego samego zestawu odwołuje się do innego projektu w aplikacji, automatyczne przekierowywanie powiązań dodaje następujący wpis do pliku wyjściowego app.config, tak, aby aplikacja jest jednolita w wersji 2.0.0.0 tego zestawu:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Można włączyć automatyczne przekierowywanie powiązań, jeśli aplikacja jest przeznaczona na starsze wersje programu .NET Framework. To zachowanie domyślne można przesłonić, podając informacje o przekierowaniach powiązań w pliku app.config do dowolnego złożenia lub przez wyłączenie funkcji przekierowania powiązania. Aby dowiedzieć się, jak włączyć tę funkcję, lub wyłączyć, zobacz [porady: Włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Pomijanie zasad wydawcy
 Można nadpisać zasady publikowania w pliku konfiguracji aplikacji, jeśli to konieczne. Na przykład nowe wersje zestawów, które uważają się zgodne z poprzednimi wersjami mogą nadal zerwać działanie aplikacji. Jeśli chcesz pominąć zasad wydawcy, Dodaj [ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu [ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) elementu w pliku konfiguracji aplikacji, a zestaw **zastosować** atrybutu **nie**, co zastępuje wszystkie poprzednie **tak** ustawienia.

 `<publisherPolicy apply="no" />`

 Omiń zasady wydawcy, aby zachować swoją aplikację dla użytkowników, ale upewnij się, że możesz zgłosić problem dostawcy zestawu. Jeśli zestaw ma plik zasad wydawcy, dostawca powinien upewnić się, że zestaw jest zgodny z poprzednimi wersjami i że klienci mogą używać nowej wersji, jak to możliwe.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Przekierowanie wersji zestawu na poziomie komputera
 Może istnieć rzadkich przypadkach, gdy administrator komputera chce, aby wszystkie aplikacje na komputerze, aby użyć określonej wersji zestawu. Na przykład administrator może być każda aplikacja korzystała z określonej wersji zestawu, ponieważ ta wersja naprawia lukę w zabezpieczeniach. Jeśli zestaw jest przekierowany w pliku konfiguracyjnym komputera, wszystkie aplikacje na tym komputerze, które używają starej wersji nastąpi przekierowanie do nowej wersji. Plik konfiguracji komputera zastępuje plik konfiguracji aplikacji i plik zasad wydawcy. Ten plik znajduje się w folderze %*ścieżka instalacji środowiska uruchomieniowego*%\Config katalogu. Zazwyczaj program .NET Framework jest instalowany w katalogu %drive%\Windows\Microsoft.NET\Framework.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Określanie powiązania zestawu w plikach konfiguracji
 Możesz użyć tego samego formatu XML do określenia przekierowań powiązania, czy znajduje się w pliku konfiguracji aplikacji, plik konfiguracji komputera lub plik zasad wydawcy. Przekierowywanie wersji zestawu do innego, należy użyć [ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) elementu. **OldVersion** atrybutu można określić jedną wersję zestawu lub zakres wersji. `newVersion` Atrybut powinien określać jedną wersję.  Na przykład `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` Określa, że środowisko uruchomieniowe powinno używać wersji 2.0.0.0 zamiast wersji zestawu między 1.1.0.0 a 1.2.0.0.

 Poniższy przykład kodu demonstruje różne scenariusze przekierowywania powiązań. Przykład określa przekierowanie zakresu wersji zestawu `myAssembly`i Przekierowanie pojedynczego powiązania dla `mySecondAssembly`. W przykładzie określono również, że plik zasad wydawcy nie spowoduje zastąpienia przekierowań powiązań dla zestawu `myThirdAssembly`.

 Do powiązania zestawu, należy określić ciąg "urn: schemas-microsoft-com:asm.v1" za pomocą **xmlns** atrybutu w [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) tagu.

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

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Ograniczanie powiązania zestawu do określonej wersji
 Możesz użyć **appliesTo** atrybutu na [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) elementu w pliku konfiguracji aplikacji do przekierowywania odwołań do powiązań zestawów do określonej wersji programu .NET Struktura. Ten atrybut opcjonalny używa numeru wersji .NET Framework, aby wskazać dla której wersji dotyczy. Jeśli nie **appliesTo** atrybut jest określony, [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element ma zastosowanie do wszystkich wersji programu .NET Framework.

 Na przykład aby przekierować powiązanie zestawu dla zestawu .NET Framework 3.5, należy dołączyć następujący kod XML w pliku konfiguracyjnym aplikacji.

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

 Informacje o przekierowaniach należy wprowadzić w kolejności wersji. Na przykład wprowadź informacje o przekierowaniach powiązań zestawów dla zestawów .NET Framework 3.5, następuje zestawów .NET Framework 4.5. Na koniec wprowadź informacje o przekierowaniach powiązań zestawów dla przekierowania z zestawu .NET Framework, która nie korzysta z **appliesTo** atrybut i dlatego ma zastosowanie do wszystkich wersji programu .NET Framework. Jeśli istnieje konflikt w przekierowania, jest używana pierwsza pasująca instrukcja przekierowania w pliku konfiguracji.

 Na przykład aby przekierować jedno odwołanie do zestawu .NET Framework 3.5 a inne odwołanie do zestawu .NET Framework 4, użyj wzoru pokazanego w poniższym pseudokodzie.

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!—.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!—.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a>Zobacz też

- [Instrukcje: włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect > Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Uprawnienia zabezpieczeń przekierowania powiązania zestawu](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)
- [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji](../../../docs/framework/configure-apps/index.md)
- [Konfigurowanie aplikacji programu .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
- [Schemat ustawień środowiska uruchomieniowego](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)
- [Instrukcje: tworzenie zasad wydawcy](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
