---
title: Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b53150c90e473e7c4ed32991c43ff0b8ca5b75b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="net-native-general-troubleshooting"></a>Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native
W tym temacie opisano sposoby rozwiązywania potencjalnych problemów, które można napotkać podczas opracowywania aplikacji za pomocą [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   **Problem:** okna danych wyjściowych kompilacji nie jest poprawnie zaktualizować.  
  
     **Rozwiązanie:** w oknie danych wyjściowych kompilacji nie zostały zaktualizowane dopiero po zakończeniu kompilacji. Kompilacji może trwać kilka minut, może wystąpić opóźnienie wyświetlenie aktualizacji.  
  
-   **Problem:** handlowej aplikacji dla wzrosło RAMIĘ czas kompilacji.  
  
     **Rozwiązanie:** podczas wdrażania aplikacji na urządzeniu ARM [!INCLUDE[net_native](../../../includes/net-native-md.md)] infrastruktury jest wywoływany. Ta kompilacja wykonuje dużą liczbą optymalizacji przy jednoczesnym zapewnieniu tego semantyki niestatyczna, takie jak odbicia w dalszym ciągu działać. Ponadto część .NET Framework, która aplikacja używa statycznie połączone w celu uzyskania optymalnej wydajności i musi można skompilować kodu natywnego, a także. Jest to, dlaczego Kompilacja trwa dłużej.  
  
     Jednak czas kompilacji jest nadal w ciągu minuty kompilacji standardowych dla większości aplikacji na maszynie standardzie.  Zwykle po prostu generowania obrazów macierzystych dla programu .NET Framework na komputerze standardzie może zająć kilka minut.  Nawet w przypadku wszystkich optymalizacji, które poprawiają wygenerowanego kodu i o tym programie .NET Framework czas kompilacji aplikacji jest zwykle minutę lub dwie.  
  
     Firma Microsoft trwają prace na temat zwiększania wydajności kompilacji polega badaniu kompilacji wielowątkowej i inne funkcje optymalizacji.  
  
-   **Problem:** nie wiadomo, jeśli aplikacja została skompilowana przy użyciu [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
     **Rozwiązanie:** Jeśli [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilatora jest wywoływany, można zauważyć już kompilacji razy i Menedżera zadań będą wyświetlane w różnych [!INCLUDE[net_native](../../../includes/net-native-md.md)] składnika procesy, takie jak ILC.exe i nutc_driver.exe.  
  
     Po utworzeniu projektu za pomocą [!INCLUDE[net_native](../../../includes/net-native-md.md)], znajdują się dane wyjściowe w obszarze obj\\*config*\ *arch* \\  *projectname*. ilc\out.  Zawartość natywnego pakiet można znaleźć w bin\\*arch*\\*config*\AppX. Zawartość natywnego pakiet podlegają \bin\\*arch*\\*config*\AppX Jeśli aplikacja została wdrożona.  
  
-   **Problem:** platformy .NET Native skompilowana aplikacja jest zgłaszanie wyjątków środowiska uruchomieniowego (zazwyczaj [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) lub [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątkami), który nie zgłosiła podczas kompilacji bez platformy .NET Native.  
  
     **Rozwiązanie:** są zgłaszane wyjątki, ponieważ platforma .NET Native nie dostarczyła metadanych lub kod implementacji, który jest dostępny za pośrednictwem odbicia. (Aby uzyskać więcej informacji, zobacz [platformy .NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).) Aby wyeliminować wyjątek, należy dodać wpis do Twojej [środowiska uruchomieniowego (rd.xml) dyrektywy pliku](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) tak, aby platforma .NET Native łańcucha narzędzi można udostępnić metadanych lub wykonania kodu w czasie wykonywania. Dostępne są dwa narzędzia do rozwiązywania problemów który wygeneruje wymaganego wpisu do dodania do pliku dyrektyw środowiska uruchomieniowego:  
  
    -   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/type.html) dla typów.  
  
    -   [MissingMetadataException Rozwiązywanie problemów z](http://dotnet.github.io/native/troubleshooter/method.html) dla metod.  
  
     Aby uzyskać więcej informacji, zobacz [odbicie i platforma .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
