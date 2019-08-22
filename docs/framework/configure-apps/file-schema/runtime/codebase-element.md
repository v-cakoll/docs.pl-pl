---
title: <codeBase>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: a06daa0b2aa5374c9959cbbe778d62856819a40e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663865"
---
# <a name="codebase-element"></a>\<codeBase> Element

Określa, gdzie środowisko uruchomieniowe języka wspólnego może znaleźć zestaw.

\<Configuration > \<Runtime > \<assemblyBinding > \<dependentAssembly > \<codebase >

## <a name="syntax"></a>Składnia

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`href`|Atrybut wymagany.<br /><br /> Określa adres URL, pod którym środowisko uruchomieniowe może znaleźć określoną wersję zestawu.|
|`version`|Atrybut wymagany.<br /><br /> Określa wersję zestawu, którego dotyczy baza kodu. Format numeru wersji zestawu to *główna. pomocnicza. kompilacja. poprawka*.|

## <a name="version-attribute"></a>Atrybut wersji

|Wartość|Opis|
|-----------|-----------------|
|Prawidłowe wartości dla każdej części numeru wersji to 0 – 65535.|Nie dotyczy.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`buildproviders`|Definiuje kolekcję dostawców kompilacji używanych do kompilowania niestandardowych plików zasobów. Możesz mieć dowolną liczbę dostawców kompilacji.|
|`compilation`|Konfiguruje wszystkie ustawienia kompilacji, które są używane przez ASP.NET.|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`System.web`|Określa element główny dla sekcji konfiguracji ASP.NET.|

## <a name="remarks"></a>Uwagi

Aby środowisko uruchomieniowe korzystało z  **\<bazy kodu >** w pliku konfiguracyjnym komputera lub w pliku zasad wydawcy, plik musi również przekierować wersję zestawu. Pliki konfiguracji aplikacji mogą mieć ustawienie bazy kodu bez przekierowywania wersji zestawu. Po ustaleniu, która wersja zestawu ma być używana, środowisko uruchomieniowe stosuje ustawienie bazy kodu z pliku, który określa wersję. Jeśli nie jest wskazana baza kodu, sondy środowiska uruchomieniowego dla zestawu w zwykły sposób.

Jeśli zestaw ma silną nazwę, ustawienie codebase może znajdować się w dowolnym miejscu w lokalnym intranecie lub w Internecie. Jeśli zestaw jest zestawem prywatnym, ustawienie bazy kodu musi być ścieżką względną do katalogu aplikacji.

W przypadku zestawów bez silnej nazwy wersja jest ignorowana, a moduł ładujący używa pierwszego \<wyglądu kodu bazowej \<> wewnątrz dependentAssembly >. Jeśli w pliku konfiguracyjnym aplikacji znajduje się wpis służący do przekierowywania powiązań do innego zestawu, przekierowania będzie miało pierwszeństwo, nawet jeśli wersja zestawu nie jest zgodna z żądaniem powiązania.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić, gdzie środowisko uruchomieniowe może znaleźć zestaw.

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Określanie lokalizacji zestawu](../../specify-assembly-location.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../deployment/how-the-runtime-locates-assemblies.md)
