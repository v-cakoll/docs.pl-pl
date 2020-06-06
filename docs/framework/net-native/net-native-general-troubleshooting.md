---
title: Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
ms.openlocfilehash: 2bea81e380fed6c456898e9883658ef874c8dd97
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128239"
---
# <a name="net-native-general-troubleshooting"></a>Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native

W tym temacie opisano sposób rozwiązywania potencjalnych problemów, które mogą wystąpić podczas opracowywania aplikacji z .NET Native.

- **Problem:** Okno dane wyjściowe kompilacji nie zostało prawidłowo zaktualizowane.

  **Rozwiązanie:** Okno dane wyjściowe kompilacji nie jest aktualizowane, dopóki kompilacja nie zostanie ukończona. Czasy kompilacji mogą przypadać do kilku minut, więc może wystąpić opóźnienie wyświetlania aktualizacji.

- **Problem:** Czas kompilacji detalicznej aplikacji dla platformy ARM wzrósł.

  **Rozwiązanie:** Po wdrożeniu aplikacji na urządzeniu ARM zostanie wywołana infrastruktura .NET Native. Ta kompilacja wykonuje dużą liczbę optymalizacji przy jednoczesnym zapewnieniu, że niestatyczna semantyka, taka jak odbicie nadal działa. Ponadto część .NET Framework, z której korzysta aplikacja, jest statycznie połączona w celu uzyskania optymalnej wydajności i musi być również skompilowana w kodzie natywnym. To właśnie kompilacja trwa dłużej.

  Czasy kompilacji są jednak nadal w ciągu minuty standardowej kompilacji dla większości aplikacji na standardowej maszynie programistycznej.  Zwykle generowanie obrazów natywnych dla .NET Framework na standardowej maszynie deweloperskiej trwa kilka minut.  Nawet w przypadku wszystkich optymalizacji w celu poprawienia wygenerowanego kodu i uwzględnienia .NET Framework czasy kompilacji aplikacji są zwykle minuty lub dwa.

  Kontynuujemy pracę nad ulepszaniem wydajności kompilacji, badając kompilacje wielowątkowe i inne optymalizacje.

- **Problem:** Nie wiesz, czy Twoja aplikacja została skompilowana przy użyciu .NET Native.

  **Rozwiązanie:** Jeśli kompilator .NET Native jest wywoływany, zobaczysz dłuższe czasy kompilacji, a Menedżer zadań będzie wyświetlał różne .NET Native procesy składników, takie jak ILC {0}. exe i nutc_driver. exe.

  Po pomyślnym skompilowaniu projektu przy użyciu .NET Native można znaleźć dane wyjściowe w obszarze \\ *config* \  *arch* \\ *ProjectName*. ilc\out.  Ostateczną zawartość pakietu natywnego można znaleźć w sekcji bin \\ *Arch* \\ *config*\AppX. Końcowa zawartość pakietu natywnego znajduje się w obszarze \\ *arch* \\ \AppX*pliku konfiguracji*, jeśli aplikacja została wdrożona.

- **Problem:** Aplikacja skompilowana przez .NET Native ma zgłaszać wyjątki środowiska uruchomieniowego (zazwyczaj wyjątki [MissingMetadataException](missingmetadataexception-class-net-native.md) lub [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) ), które nie zostały wyrzucane podczas kompilacji bez .NET Native.

  **Rozwiązanie:** Wyjątki są zgłaszane, ponieważ .NET Native nie dostarczył metadanych lub kodu implementacji, który jest w inny sposób dostępny w wyniku odbicia. (Aby uzyskać więcej informacji, zobacz [.NET Native i kompilacja](net-native-and-compilation.md)). Aby wyeliminować wyjątek, należy dodać wpis do [pliku dyrektywy środowiska uruchomieniowego (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md) , dzięki czemu łańcuch narzędzi .NET Native może sprawić, że metadane lub kod implementacji będą dostępne w czasie wykonywania. Dostępne są dwa narzędzia do rozwiązywania problemów, które spowodują wygenerowanie niezbędnego wpisu do dodania do pliku dyrektywy środowiska uruchomieniowego:

  - [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) dla typów.

  - [Narzędzie do rozwiązywania problemów z MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) .

  Aby uzyskać więcej informacji, zobacz [odbicie i .NET Native](reflection-and-net-native.md).

## <a name="see-also"></a>Zobacz także

- [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](migrating-your-windows-store-app-to-net-native.md)
