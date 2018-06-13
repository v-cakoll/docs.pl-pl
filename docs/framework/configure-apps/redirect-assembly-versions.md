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
manager: markl
ms.openlocfilehash: 3459ebd2f1df38ac70e9211fd4865e227cd996cb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759273"
---
# <a name="redirecting-assembly-versions"></a>Przekierowywanie wersji zestawu
Można przekierować powiązanie kompilacji odwołania do zestawów platformy .NET Framework, zestawy innych firm lub zestawy własnych aplikacji. Można przekierować aplikację, aby użyć innej wersji zestawu na kilka sposobów: za pomocą zasad wydawcy, za pomocą pliku konfiguracji aplikacji; lub za pomocą pliku konfiguracji komputera. W tym artykule omówiono sposób działania powiązań zestawów w programie .NET Framework i jak można je skonfigurować.  
  
<a name="BKMK_Assemblyunificationanddefaultbinding"></a>   
## <a name="assembly-unification-and-default-binding"></a>Ujednolicenie zestawu i powiązanie domyślnej  
 W procesie nazywanym czasem przekierowywania powiązań dla zestawów platformy .NET Framework *ujednolicenie zestawu*. .NET Framework składa się z wersję środowiska CLR i o dwadzieścia zestawy .NET Framework, które tworzą biblioteki typów. Te zestawy .NET Framework są traktowane przez środowisko uruchomieniowe jako pojedyncza jednostka. Domyślnie gdy aplikacja jest uruchamiana, wszystkie odwołania do typów w kodzie uruchomienia przez środowisko uruchomieniowe są przekierowywane do zestawy .NET Framework, które mają ten sam numer wersji, co środowiska uruchomieniowego, który jest ładowany w procesie. Przekierowań, które występują w przypadku tego modelu są domyślne zachowanie środowiska uruchomieniowego.  
  
 Na przykład jeśli aplikacja odwołuje się do typów w przestrzeni nazw zestawów System.XML i został skompilowany przy użyciu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zawiera statyczny odwołania do zestawu zestawów System.XML, który jest dostarczany z środowiska wykonawczego w wersji 4.5. Jeśli chcesz przekierowywać odwołanie powiązanie, aby do zestawów System.XML, dostarczanych z programem .NET Framework 4, możesz umieścić informacji przekierowania w pliku konfiguracyjnym aplikacji. Przekierowanie powiązania w pliku konfiguracji dla ujednoliconego zestawu .NET Framework anuluje ujednolicenie dla tego zestawu.  
  
 Ponadto można ręcznie przekierowania powiązań dla zestawów innych firm, jeśli istnieje wiele wersji zestawów.  
  
<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>   
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Przekierowywanie wersji zestawu przy użyciu zasad wydawcy  
 Dostawców zestawy może bezpośrednia aplikacji do nowszej wersji zestawu przez dołączenie pliku zasad wydawcy z nowego zestawu. Plik zasad wydawcy, który znajduje się w globalnej pamięci podręcznej zestawów, zawiera ustawienia przekierowywania zestawu.  
  
 Każdy *głównych*. *drobne* wersja zestawu ma własny plik zasad wydawcy. Na przykład przekierowań wersji 2.0.2.222 do 2.0.3.000 i z wersji 2.0.2.321 na wersję 2.0.3.000 zarówno przejść do tego samego pliku, ponieważ są one powiązane z wersji 2.0. Jednak przekierowanie z wersji 3.0.0.999 do wersji 4.0.0.000 przechodzi do pliku dla wersji 3.0.999. Każda wersja główna systemu .NET Framework ma własny plik zasad wydawcy.  
  
 Jeśli plik zasad wydawcy zestawu, środowisko uruchomieniowe sprawdza ten plik po sprawdzeniu zestawu pliku konfiguracji manifestu i aplikacji. Dostawców należy używać pliki zasad wydawcy, tylko wtedy, gdy nowy zestaw jest zgodny z zestawu, nastąpi przekierowanie.  
  
 Można pominąć zasad wydawcy dla aplikacji, określając ustawienia w pliku konfiguracji aplikacji, zgodnie z opisem w [pomijanie sekcji zasad wydawcy](#bypass_PP).  
  
<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>   
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Przekierowywanie wersji zestawu na poziomie aplikacji  
 Istnieje kilka różnych technik zmieniające zachowanie wiązania dla aplikacji za pomocą pliku konfiguracji aplikacji: można ręcznie edytować plik, może polegać na automatycznego przekierowania powiązań lub można określić zachowanie wiązania, pomijając zasad wydawcy.  
  
### <a name="manually-editing-the-app-config-file"></a>Ręczna Edycja pliku konfiguracji aplikacji  
 Można ręcznie edytować pliku konfiguracji aplikacji, aby rozwiązać problemy z zestawu. Na przykład jeśli dostawca może zwolnić nowszej wersji zestawu, który aplikacja używa bez podawania zasad wydawcy, ponieważ nie gwarantują zgodność z poprzednimi wersjami, można kierować aplikacji umieszczanie zestawu za pomocą nowszej wersji zestawu powiązania następujące informacje w pliku konfiguracyjnym aplikacji.  
  
```xml  
<dependentAssembly>  
  <assemblyIdentity name="someAssembly"  
    publicKeyToken="32ab4ba45e0a69a1"  
    culture="en-us" />  
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />  
</dependentAssembly>  
```  
  
### <a name="relying-on-automatic-binding-redirection"></a>Zależne automatycznego przekierowania powiązań  
 Począwszy od [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], nowych aplikacji klasycznych, które odnoszą się do [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] Użyj automatycznego przekierowania powiązań. Oznacza to, że dwa składniki odwołać różne wersje tego samego zestawu o silnej nazwie, środowisko uruchomieniowe automatycznie dodaje przekierowania powiązania do nowszej wersji zestawu w pliku konfiguracyjnym (app.config) dane wyjściowe aplikacji. Przekierowanie przesłania ujednolicenie zestawu, które w przeciwnym razie może mieć miejsce. Źródłowy plik app.config nie jest modyfikowany. Załóżmy na przykład, że aplikacji bezpośrednio odwołuje się do składników .NET Framework poza pasmem, ale korzysta z biblioteki innej firmy, który jest przeznaczony dla starszej wersji tego samego składnika. Podczas kompilowania aplikacji pliku konfiguracji aplikacji dane wyjściowe są modyfikowane w celu zawierają przekierowania powiązania do nowszej wersji składnika. Jeśli utworzysz aplikację sieci web, pojawi się ostrzeżenie kompilacji dotyczące konflikt powiązania, który z kolei pozwala dodać przekierowanie powiązania niezbędne do źródłowego pliku konfiguracji sieci web.  
  
 Jeśli ręcznie Dodaj przekierowania powiązania do pliku app.config źródło w czasie kompilacji [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] próbuje ujednolicenie zestawów, w oparciu o przekierowania powiązania dodane. Załóżmy na przykład, że Wstaw następujący przekierowania powiązania dla zestawu:  
  
 `<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`  
  
 Jeśli ten sam zestaw w wersji 1.0.0.0 odwołuje się do innego projektu w aplikacji, automatycznego przekierowania powiązań dodaje następujący wpis do pliku app.config wyjściowego tak, aby aplikacja jest unified w wersji 2.0.0.0 tego zestawu:  
  
 `<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`  
  
 Można włączyć automatycznego przekierowania powiązań, jeśli aplikacja jest przeznaczony dla starszej wersji programu .NET Framework w [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]. Można zastąpić to zachowanie domyślne, podając informacje o powiązaniu przekierowania w pliku app.config żadnych zestawów lub wyłączyć funkcję przekierowanie powiązania. Aby dowiedzieć się, jak włączyć tę funkcję, lub wyłączyć, zobacz [porady: Włączanie i wyłączanie automatycznego przekierowania powiązania](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).  
  
<a name="bypass_PP"></a>   
### <a name="bypassing-publisher-policy"></a>Pomijanie zasad wydawcy  
 Można zastąpić zasad wydawcy w pliku konfiguracji aplikacji, jeśli to konieczne. Na przykład nowe wersje zestawy, które zgodne ze starszymi wersjami mogą nadal być dzielone aplikacji. Jeśli chcesz pominąć zasad wydawcy, Dodaj [ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu [ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) element w pliku konfiguracji aplikacji i zestaw **zastosować** atrybutu **nie**, co zastępuje wszelkie poprzednie **tak** ustawienia.  
  
 `<publisherPolicy apply="no" />`  
  
 Obejście zasad wydawcy, aby zapewnić działanie aplikacji dla użytkowników, ale upewnij się, że zgłosić problem z dostawcą zestawu. Jeśli zestaw ma pliku zasad wydawcy, dostawcy upewnij się, że zestaw jest zgodne z poprzednimi wersjami i że klienci mogą używać nowej wersji, jak to możliwe.  
  
<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>   
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Przekierowywanie wersji zestawu na poziomie komputera  
 Czasami mogą wystąpić, gdy administrator maszyny oczekuje, że wszystkie aplikacje na komputerze do określonej wersji zestawu. Na przykład administrator może być każdej aplikacji przy użyciu wersji określonego zestawu, ponieważ ta wersja poprawki luka w zabezpieczeniach. Jeśli zestaw jest przekierowanie w pliku konfiguracji komputera, wszystkie korzystających na tej maszynie starej wersji zostanie przekierowany do nowej wersji. Plik konfiguracji maszyny przesłania pliku konfiguracji aplikacji i pliku zasad wydawcy. Ten plik znajduje się w folderze %*ścieżka instalacji środowiska uruchomieniowego*%\Config katalogu. Zazwyczaj program .NET Framework jest instalowany w katalogu %drive%\Windows\Microsoft.NET\Framework.  
  
<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>   
## <a name="specifying-assembly-binding-in-configuration-files"></a>Określanie powiązania w plikach konfiguracji zestawów  
 Używasz tego samego formatu XML do określenia przekierowania powiązania, czy znajduje się w pliku konfiguracji aplikacji, pliku konfiguracji komputera lub pliku zasad wydawcy. Aby przekierować jednej wersji zestawu do innego, należy użyć [ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) elementu. **OldVersion** atrybutu można określić wersji zestawu jednej lub zakres wersji. `newVersion` Atrybut powinien określać jednej wersji.  Na przykład `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` Określa, że środowisko wykonawcze należy używać wersji 2.0.0.0 zamiast wersji zestawu między 1.1.0.0 i 1.2.0.0.  
  
 Poniższy przykład kodu pokazuje różnych scenariuszy przekierowania powiązania. W przykładzie określono przekierowanie dla zakresu wersji dla `myAssembly`i przekierowania jednego powiązania dla `mySecondAssembly`. W przykładzie określa również tego pliku zasad wydawcy nie spowoduje zastąpienia przekierowania powiązania dla `myThirdAssembly`.  
  
 Aby powiązać zestawu, należy określić ciąg "urn: schemas-microsoft-com:asm.v1" z **xmlns** atrybutu w [ \<assemblybinding — >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) tagu.  
  
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
  
### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Ograniczanie powiązań zestawów do określonej wersji  
 Można użyć **appliesTo** atrybutu [ \<assemblybinding — >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) w pliku konfiguracji aplikacji do przekierowania powiązania odwołania do zestawów do określonej wersji programu .NET Struktura. Ten opcjonalny atrybut używa numeru wersji .NET Framework w celu wskazania dotyczy wersji. Jeśli nie **appliesTo** określono atrybut [ \<assemblybinding — >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element ma zastosowanie do wszystkich wersji platformy .NET Framework.  
  
 Na przykład aby przekierować zestawu powiązania dla zestawu .NET Framework 3.5, można dołączyć następujący kod XML w pliku konfiguracyjnym aplikacji.  
  
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
  
 Wprowadź informacje o przekierowania w kolejności wersji. Na przykład wprowadź informacje przekierowania powiązania zestawu dla zestawów platformy .NET Framework 3.5, następuje zestawów platformy .NET Framework 4.5. Na koniec wprowadź informacje dotyczące przekierowania powiązania zestawu dla przekierowania zestawu .NET Framework, które nie są używane **appliesTo** atrybut i dlatego ma zastosowanie do wszystkich wersji platformy .NET Framework. Jeśli występuje konflikt podczas przekierowywania, pierwsza instrukcja pasującego przekierowania w pliku konfiguracji jest używany.  
  
 Na przykład aby przekierować jedno odwołanie do zestawu .NET Framework 3.5 i inne odwołanie do zestawu .NET Framework 4, należy użyć wzorzec pokazano w poniższych pseudocode.  
  
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
 [Instrukcje: włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [\<w parametrze bindingRedirect > — Element](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [Uprawnienia zabezpieczeń przekierowania powiązania zestawu](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurowanie aplikacji](../../../docs/framework/configure-apps/index.md)  
 [Konfigurowanie aplikacji programu .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Schemat ustawień środowiska uruchomieniowego](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Instrukcje: tworzenie zasad wydawcy](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
