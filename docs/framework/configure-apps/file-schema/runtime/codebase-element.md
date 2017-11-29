---
title: "&lt;codeBase&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5b30f1dc3ccade3028c31c57ffdab521802f086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcodebasegt-element"></a>&lt;codeBase&gt; — Element
Określa, gdzie znaleźć środowisko uruchomieniowe języka wspólnego zestawu.  
  
 \<Konfiguracja >  
\<Runtime >  
\<assemblybinding — >  
\<dependentAssembly >  
\<codeBase >  
  
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
|`href`|Atrybut wymagany.<br /><br /> Określa adres URL, gdzie środowiska uruchomieniowego można znaleźć określonej wersji zestawu.|  
|`version`|Atrybut wymagany.<br /><br /> Określa wersję zestawu, w którym baza kodu dotyczy. Format numeru wersji zestawu jest *główna.pomocnicza.kompilacja.poprawka*.|  
  
## <a name="version-attribute"></a>Wersja atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Prawidłowe wartości dla każdej części numer wersji to od 0 do 65535.|Nie dotyczy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`buildproviders`|Definiuje kolekcję dostawców kompilacji używana do kompilowania plików zasobów niestandardowych. Może mieć dowolną liczbę dostawcy kompilacji.|  
|`compilation`|Konfiguruje wszystkie ustawienia kompilacji używane przez program ASP.NET.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`System.web`|Określa element root dla sekcji konfiguracji ASP.NET.|  
  
## <a name="remarks"></a>Uwagi  
 Dla środowiska uruchomieniowego do użycia  **\<codeBase >** ustawienia w pliku konfiguracyjnym maszyny lub pliku zasad wydawcy, plik musi również przekierować wersja zestawu. Pliki konfiguracji aplikacji może mieć ustawienie codebase bez przekierowywanie wersji zestawu. Po ustaleniu wersji zestawu do użycia, środowisko uruchomieniowe stosuje ustawienia codebase z pliku, który określa wersję. Jeśli codebase nie jest zaznaczone, środowisko uruchomieniowe sondy dla zestawu w zwykły sposób.  
  
 Jeśli zestaw ma silną nazwę, ustawienie codebase może być dowolnym w lokalnym intranecie lub Internecie. Jeśli zestaw jest zestaw prywatny, ustawienie codebase musi być ścieżką względną wobec katalogu aplikacji.  
  
 Dla zestawów bez silnych nazw, wersja jest ignorowane, a pierwsze wystąpienie korzysta z modułu ładującego \<codebase > wewnątrz \<dependentAssembly >. Jeśli istnieje wpis w pliku konfiguracyjnym aplikacji, który przekierowuje powiązania do innego zestawu, przekierowywanie wyższy priorytet, nawet jeśli wersja zestawu nie odpowiada na żądania powiązania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób określić, gdzie środowiska uruchomieniowego można znaleźć zestawu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Określanie lokalizacji zestawu](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [Jak lokalizuje zestawów przez środowisko uruchomieniowe](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
