---
title: Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9599ee25e77bf6f44e5c6733deed8dc23fc0d022
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662324"
---
# <a name="net-native-general-troubleshooting"></a>Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native

W tym temacie opisano sposób rozwiązywania potencjalnych problemów, które można napotkać podczas tworzenia aplikacji przy użyciu platformy .NET Native.

- **Problem:** Okno danych wyjściowych kompilacji nie są prawidłowo aktualizowane.

  **Rozwiązanie:** W oknie danych wyjściowych kompilacji nie są aktualizowane, do momentu ukończenia kompilacji. Czasy kompilacji może pochodzić maksymalnie kilka minut, więc mogą wystąpić opóźnienia w widzisz aktualizacji.

- **Problem:** Został zwiększony czas kompilacji detalicznej Twojej aplikacji dla ARM.

  **Rozwiązanie:** Gdy wdrażasz aplikację z urządzeniem ARM, jest wywoływana infrastrukturę programu .NET Native. Tej kompilacji wykonuje dużej liczby optymalizacje przy jednoczesnym zapewnieniu tej semantyki niestatyczna, takich jak odbicie w dalszym ciągu działać. Ponadto część .NET Framework, która aplikacja używa statycznie połączone w celu uzyskania optymalnej wydajności i musi być kompilowane do kodu macierzystego, jak również. Jest to, dlaczego Kompilacja trwa dłużej.

  Czasy kompilacji są jednak nadal w ciągu minuty kompilacji standardowych dla większości aplikacji na maszynie deweloperskiej standardowych.  Po prostu generowanie obrazów macierzystych na platformie .NET na maszynie deweloperskiej standardowych zazwyczaj trwa kilka minut.  Nawet w przypadku wszystkich optymalizacji usprawniających wygenerowany kod i za pomocą programu .NET Framework w tym aplikacji, czasy kompilacji są zazwyczaj minutę lub dwie.

  Kontynuujemy pracę nad poprawa wydajności kompilacji, badając wielowątkowych kompilacji i inne optymalizacje.

- **Problem:** Nie wiem, jeśli aplikacja został skompilowany przy użyciu platformy .NET Native.

  **Rozwiązanie:** Wywoływany jest kompilator platformy .NET Native, można zauważyć, że różne procesy składnik .NET Native, takie jak ILC.exe i nutc_driver.exe będzie wyświetlana dłuższe czasy kompilacji i Menedżera zadań.

  Po pomyślnie skompilować projekt przy użyciu platformy .NET Native, znajdują się dane wyjściowe w obszarze obj\\*config*\ *arch*\\*projectname*. ilc\out.  Zawartość pakietu natywnej końcowego można znaleźć w bin\\*arch*\\*config*\AppX. Zawartość pakietu natywnej końcowego podlegają \bin\\*arch*\\*config*\AppX Jeśli aplikacja została wdrożona.

- **Problem:** Aplikacja platformy .NET Native skompilowany zgłasza wyjątki środowiska uruchomieniowego (zazwyczaj [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) lub [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki), nie generują kiedy skompilowany bez. NET Native.

  **Rozwiązanie:** Wyjątki są zgłaszane, ponieważ .NET Native nie dostarczył metadanych lub kod implementacji, który jest dostępny za pośrednictwem odbicia. (Aby uzyskać więcej informacji, zobacz [.NET Native i kompilacja](../../../docs/framework/net-native/net-native-and-compilation.md).) Aby wyeliminować wyjątek, należy dodać wpis do swojej [środowiska uruchomieniowego (rd.xml) dyrektywy pliku](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) tak, aby .NET Native łańcucha narzędzi można udostępnić metadanych lub wykonania kodu w czasie wykonywania. Dostępne są dwa narzędzia do rozwiązywania problemów, spowoduje wygenerowanie niezbędnych wpis, aby dodać do pliku dyrektyw środowiska uruchomieniowego:

  - [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.

  - [MissingMetadataException narzędzia do rozwiązywania problemów](https://dotnet.github.io/native/troubleshooter/method.html) dla metod.

  Aby uzyskać więcej informacji, zobacz [odbicia i platforma .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).

## <a name="see-also"></a>Zobacz także

- [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
