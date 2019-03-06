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
ms.openlocfilehash: b5825efcc613689e73fb56b6695fe7c75ff09136
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356614"
---
# <a name="codebase-element"></a>\<codeBase> Element

Określa, gdzie znaleźć zestawu środowisko uruchomieniowe języka wspólnego.

\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase>

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
|`href`|Atrybut wymagany.<br /><br /> Określa adres URL, których środowisko uruchomieniowe można znaleźć określonej wersji zestawu.|
|`version`|Atrybut wymagany.<br /><br /> Określa wersję zestawu, który dotyczy bazy kodu. Format numeru wersji zestawu to *główna.pomocnicza.kompilacja.poprawka*.|

## <a name="version-attribute"></a>Wersja atrybutu

|Wartość|Opis|
|-----------|-----------------|
|Prawidłowe wartości dla każdej części numer wersji to od 0 do 65535.|Nie dotyczy.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`buildproviders`|Definiuje kolekcję dostawców kompilacji używana do kompilowania plików zasobów niestandardowych. Może mieć dowolną liczbę dostawców kompilacji.|
|`compilation`|Konfiguruje wszystkie ustawienia kompilacji używane przez program ASP.NET.|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`System.web`|Określa element root dla sekcji konfiguracyjnej platformy ASP.NET.|

## <a name="remarks"></a>Uwagi

Użyj środowiska uruchomieniowego  **\<codeBase >** ustawienia w pliku konfiguracji komputera lub plik zasad wydawcy, plik również przekierować wersji zestawu. Pliki konfiguracyjne aplikacji może mieć ustawienie kodu bez przekierowywanie wersji zestawu. Po ustaleniu, jakiego zestawu należy użyć, środowisko uruchomieniowe ma zastosowanie z ustawieniem kodu z pliku, który określa wersja. Jeśli codebase nie jest zaznaczone, środowisko uruchomieniowe sondy dla zestawu w zwykły sposób.

Jeśli zestaw ma silną nazwą, ustawienie kodu może być dowolnym miejscu na lokalny intranet lub Internetem. Jeśli zestaw jest zestaw prywatny, ustawienie codebase musi być ścieżką względną wobec katalogu aplikacji.

Na zestawy bez silnej nazwy, wersji jest ignorowany, a moduł ładujący używa pierwszego pojawienia się \<codebase > wewnątrz \<dependentAssembly >. Jeśli istnieje wpis w pliku konfiguracyjnym aplikacji, który przekierowuje powiązanie do innego zestawu, przekierowywanie będą miały pierwszeństwo, nawet wtedy, gdy wersja zestawu nie odpowiada na żądania powiązania.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak określić, gdzie środowisko uruchomieniowe można znaleźć zestawu.

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

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Określanie lokalizacji zestawu](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
