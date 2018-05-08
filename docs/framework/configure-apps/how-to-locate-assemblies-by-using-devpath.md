---
title: 'Porady: lokalizowanie zestawów za pomocą DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 918acf069c63d3aa8187f0f04e1f6c55ec961458
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Porady: lokalizowanie zestawów za pomocą DEVPATH
Deweloperzy mogą chcieć upewnij się, że współużytkowanego zespołu, które są one tworzenie działa poprawnie z wieloma aplikacjami. Zamiast stale umieszczanie zestawu w pamięci podręcznej GAC podczas cyklu programowania, deweloper może utworzyć zmienną środowiskową DEVPATH wskazujące budowy katalogu wyjściowego dla zestawu.  
  
 Załóżmy na przykład, czy tworzysz zestaw udostępnionego o nazwie MySharedAssembly i katalog wyjściowy jest C:\MySharedAssembly\Debug. Możesz też zaznaczyć C:\MySharedAssembly\Debug za pomocą DEVPATH zmiennej. Następnie należy określić [ \<developmentmode — >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) elementu w pliku konfiguracji komputera. Ten element określa, że środowisko uruchomieniowe języka wspólnego do użycia DEVPATH do lokalizowania zestawów.  
  
 Zestaw udostępnionego musi być wykrywalny przez środowisko uruchomieniowe.  Aby określić katalog prywatnej w celu rozwiązania użyj odwołania do zestawu [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) lub [ \<sondowanie > elementu](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) w pliku konfiguracji, zgodnie z opisem w temacie [Określanie lokalizacji zestawu](../../../docs/framework/configure-apps/specify-assembly-location.md).  Można również umieścić zestaw w podkatalogu w katalogu aplikacji. Aby uzyskać więcej informacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
>  Jest to zaawansowana funkcja przeznaczona tylko dla rozwoju.  
  
 Poniższy przykład pokazuje, jak spowodować środowiska uruchomieniowego do wyszukiwania zestawów w katalogach określonej przez zmienną środowiskową DEVPATH.  
  
## <a name="example"></a>Przykład  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Domyślnie to ustawienie na wartość false.  
  
> [!NOTE]
>  Tego ustawienia należy używać tylko w czasie opracowywania. Środowisko uruchomieniowe nie sprawdza wersje zestawów o silnych nazwach w DEVPATH. Po prostu używa pierwszego zestawu znalezione.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie aplikacji programu .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
