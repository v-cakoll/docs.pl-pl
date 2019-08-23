---
title: 'Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913001"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH
Deweloperzy mogą chcieć upewnić się, że kompiluje się zestaw współużytkowany działa prawidłowo z wieloma aplikacjami. Zamiast ciągłego umieszczania zestawu w globalnej pamięci podręcznej zestawów podczas cyklu projektowania, deweloper może utworzyć zmienną środowiskową DEVPATH, która wskazuje katalog wyjściowy kompilacji dla zestawu.  
  
 Załóżmy na przykład, że tworzysz zestaw współużytkowany o nazwie MySharedAssembly, a katalog wyjściowy to C:\MySharedAssembly\Debug. Możesz umieścić C:\MySharedAssembly\Debug w zmiennej DEVPATH. Następnie należy określić [ \<element developmentmode >](./file-schema/runtime/developmentmode-element.md) w pliku konfiguracji maszyny. Ten element zawiera informacje o tym, że środowisko uruchomieniowe języka wspólnego używa DEVPATH do lokalizowania zestawów.  
  
 Zestaw współużytkowany musi być wykrywalny przez środowisko uruchomieniowe.  Aby określić katalog prywatny do rozpoznawania odwołań do zestawów, użyj [ \<kodu bazowej > elementu](./file-schema/runtime/codebase-element.md) lub [ \<>](./file-schema/runtime/probing-element.md) do sondowania w pliku konfiguracji, zgodnie z opisem w temacie [Określanie lokalizacji zestawu](specify-assembly-location.md).  Możesz również umieścić zestaw w podkatalogu katalogu aplikacji. Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
> Jest to zaawansowana funkcja przeznaczona tylko do programowania.  
  
 Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.  
  
## <a name="example"></a>Przykład  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 To ustawienie domyślnie ma wartość false.  
  
> [!NOTE]
> Tego ustawienia należy używać tylko w czasie projektowania. Środowisko uruchomieniowe nie sprawdza wersji w zestawach o silnej nazwie znalezionych w DEVPATH. Po prostu używa pierwszego zestawu, który znajdzie.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie aplikacji przy użyciu plików konfiguracji](index.md)
