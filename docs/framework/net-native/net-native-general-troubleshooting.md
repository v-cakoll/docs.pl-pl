---
title: Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6bc5697e20c21d988afe6017d05e0e4de53d40d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614918"
---
# <a name="net-native-general-troubleshooting"></a>Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native
W tym temacie opisano sposób rozwiązywania potencjalnych problemów, które można napotkać podczas tworzenia aplikacji przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
- **Problem:** Okno danych wyjściowych kompilacji nie są prawidłowo aktualizowane.  
  
     **Rozwiązanie:** W oknie danych wyjściowych kompilacji nie są aktualizowane, do momentu ukończenia kompilacji. Czasy kompilacji może pochodzić maksymalnie kilka minut, więc mogą wystąpić opóźnienia w widzisz aktualizacji.  
  
- **Problem:** Został zwiększony czas kompilacji detalicznej Twojej aplikacji dla ARM.  
  
     **Rozwiązanie:** W przypadku wdrażania aplikacji z urządzeniem ARM [!INCLUDE[net_native](../../../includes/net-native-md.md)] infrastruktury jest wywoływana. Tej kompilacji wykonuje dużej liczby optymalizacje przy jednoczesnym zapewnieniu tej semantyki niestatyczna, takich jak odbicie w dalszym ciągu działać. Ponadto część .NET Framework, która aplikacja używa statycznie połączone w celu uzyskania optymalnej wydajności i musi być kompilowane do kodu macierzystego, jak również. Jest to, dlaczego Kompilacja trwa dłużej.  
  
     Czasy kompilacji są jednak nadal w ciągu minuty kompilacji standardowych dla większości aplikacji na maszynie deweloperskiej standardowych.  Po prostu generowanie obrazów macierzystych na platformie .NET na maszynie deweloperskiej standardowych zazwyczaj trwa kilka minut.  Nawet w przypadku wszystkich optymalizacji usprawniających wygenerowany kod i za pomocą programu .NET Framework w tym aplikacji, czasy kompilacji są zazwyczaj minutę lub dwie.  
  
     Kontynuujemy pracę nad poprawa wydajności kompilacji, badając wielowątkowych kompilacji i inne optymalizacje.  
  
- **Problem:** Nie wiem, jeśli aplikacja została skompilowana przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
     **Rozwiązanie:** Jeśli [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilator jest wywoływany, można zauważyć już kompilowany razy i Menedżera zadań opisano różne [!INCLUDE[net_native](../../../includes/net-native-md.md)] składnika procesy, takie jak ILC.exe i nutc_driver.exe.  
  
     Po utworzeniu projektu za pomocą [!INCLUDE[net_native](../../../includes/net-native-md.md)], znajdują się dane wyjściowe w obszarze obj\\*config*\ *arch* \\  *projectname*. ilc\out.  Zawartość pakietu natywnej końcowego można znaleźć w bin\\*arch*\\*config*\AppX. Zawartość pakietu natywnej końcowego podlegają \bin\\*arch*\\*config*\AppX Jeśli aplikacja została wdrożona.  
  
- **Problem:** Aplikacja platformy .NET Native skompilowany zgłasza wyjątki środowiska uruchomieniowego (zazwyczaj [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) lub [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki), nie generują kiedy skompilowany bez. NET Native.  
  
     **Rozwiązanie:** Wyjątki są zgłaszane, ponieważ .NET Native nie dostarczył metadanych lub kod implementacji, który jest dostępny za pośrednictwem odbicia. (Aby uzyskać więcej informacji, zobacz [.NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).) Aby wyeliminować wyjątek, należy dodać wpis do swojej [środowiska uruchomieniowego (rd.xml) dyrektywy pliku](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) tak, aby .NET Native łańcucha narzędzi można udostępnić metadanych lub wykonania kodu w czasie wykonywania. Dostępne są dwa narzędzia do rozwiązywania problemów, spowoduje wygenerowanie niezbędnych wpis, aby dodać do pliku dyrektyw środowiska uruchomieniowego:  
  
    - [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
    - [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
     Aby uzyskać więcej informacji, zobacz [odbicia i platforma .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).  
  
## <a name="see-also"></a>Zobacz także

- [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
