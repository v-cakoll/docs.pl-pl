---
title: Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45a053d2aefa8a295e0e8d52818472647e4ef834
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347594"
---
# <a name="net-native-general-troubleshooting"></a>Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native
W tym temacie opisano sposób rozwiązywania potencjalnych problemów, które można napotkać podczas tworzenia aplikacji przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   **Problem:** oknie danych wyjściowych kompilacji nie są prawidłowo aktualizowane.  
  
     **Rozwiązanie:** w oknie danych wyjściowych kompilacji nie zostały zaktualizowane do momentu ukończenia kompilacji. Czasy kompilacji może pochodzić maksymalnie kilka minut, więc mogą wystąpić opóźnienia w widzisz aktualizacji.  
  
-   **Problem:** handlu detalicznego Twojej aplikacji dla ARM został zwiększony czas kompilacji.  
  
     **Rozwiązanie:** podczas wdrażania aplikacji na urządzeniu ARM [!INCLUDE[net_native](../../../includes/net-native-md.md)] infrastruktury jest wywoływana. Tej kompilacji wykonuje dużej liczby optymalizacje przy jednoczesnym zapewnieniu tej semantyki niestatyczna, takich jak odbicie w dalszym ciągu działać. Ponadto część .NET Framework, która aplikacja używa statycznie połączone w celu uzyskania optymalnej wydajności i musi być kompilowane do kodu macierzystego, jak również. Jest to, dlaczego Kompilacja trwa dłużej.  
  
     Czasy kompilacji są jednak nadal w ciągu minuty kompilacji standardowych dla większości aplikacji na maszynie deweloperskiej standardowych.  Po prostu generowanie obrazów macierzystych na platformie .NET na maszynie deweloperskiej standardowych zazwyczaj trwa kilka minut.  Nawet w przypadku wszystkich optymalizacji usprawniających wygenerowany kod i za pomocą programu .NET Framework w tym aplikacji, czasy kompilacji są zazwyczaj minutę lub dwie.  
  
     Kontynuujemy pracę nad poprawa wydajności kompilacji, badając wielowątkowych kompilacji i inne optymalizacje.  
  
-   **Problem:** nie wiesz, jeśli aplikacja została skompilowana przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
     **Rozwiązanie:** Jeśli [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilator jest wywoływany, można zauważyć już kompilowany razy i Menedżera zadań opisano różne [!INCLUDE[net_native](../../../includes/net-native-md.md)] składnika procesy, takie jak ILC.exe i nutc_driver.exe.  
  
     Po utworzeniu projektu za pomocą [!INCLUDE[net_native](../../../includes/net-native-md.md)], znajdują się dane wyjściowe w obszarze obj\\*config*\ *arch* \\  *projectname*. ilc\out.  Zawartość pakietu natywnej końcowego można znaleźć w bin\\*arch*\\*config*\AppX. Zawartość pakietu natywnej końcowego podlegają \bin\\*arch*\\*config*\AppX Jeśli aplikacja została wdrożona.  
  
-   **Problem:** aplikację platformy .NET Native skompilowany zgłasza wyjątki środowiska uruchomieniowego (zazwyczaj [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) lub [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki), nie generują gdy kompilowany bez .NET Native.  
  
     **Rozwiązanie:** wyjątki są zgłaszane, ponieważ .NET Native nie dostarczył metadanych lub kod implementacji, który jest dostępny za pośrednictwem odbicia. (Aby uzyskać więcej informacji, zobacz [.NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).) Aby wyeliminować wyjątek, należy dodać wpis do swojej [środowiska uruchomieniowego (rd.xml) dyrektywy pliku](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) tak, aby .NET Native łańcucha narzędzi można udostępnić metadanych lub wykonania kodu w czasie wykonywania. Dostępne są dwa narzędzia do rozwiązywania problemów, spowoduje wygenerowanie niezbędnych wpis, aby dodać do pliku dyrektyw środowiska uruchomieniowego:  
  
    -   [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
    -   [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
     Aby uzyskać więcej informacji, zobacz [odbicia i platforma .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
