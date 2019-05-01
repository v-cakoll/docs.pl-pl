---
title: Zgodność wersji w programie .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dda2cf99bdd3152e234bec4a143a7ab5ebd4cae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870204"
---
# <a name="version-compatibility-in-the-net-framework"></a>Zgodność wersji w programie .NET Framework

Zgodność ze starszymi wersjami oznacza, że aplikacja opracowana dla konkretnej wersji platformy będzie działać w nowszych wersjach tej platformy. .NET Framework próbuje zapewnić maksymalną zgodność z poprzednimi wersjami: Kod źródłowy napisany dla jednej wersji programu .NET Framework powinien kompilować się w nowszych wersjach .NET Framework i pliki binarne, które działają w jednej wersji programu .NET Framework powinny działać identycznie w nowszych wersjach .NET Framework.

## <a name="Apps"></a> Zgodność wersji aplikacji

Domyślnie aplikacja jest uruchamiana w wersji programu .NET Framework, która została skompilowana. Jeśli ta wersja nie jest obecny i pliku konfiguracji aplikacji nie definiuje obsługiwanych wersji, może wystąpić błąd inicjalizacji programu .NET Framework. W tym przypadku próba uruchomienia aplikacji nie powiedzie się.

Aby zdefiniować określonych wersji, na których dana aplikacja działa, Dodaj jeden lub kilka [ \<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) elementy do pliku konfiguracji aplikacji. Każdy `<supportedRuntime>` element zawiera listę obsługiwanych wersji środowiska uruchomieniowego, przy czym pierwsze określenie najbardziej preferowaną wersję, a ostatni Określanie najmniej preferowaną wersję.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Aby uzyskać więcej informacji, zobacz [jak: Konfiguracja aplikacji do obsługi platformy .NET Framework 4 lub 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Zgodność wersji składników

Aplikacja może kontrolować wersję .NET Framework, na którym działa, ale składnik nie może. Składniki i biblioteki klas są ładowane w kontekście określonej aplikacji i dlatego automatycznego uruchamiania, od używanej wersji programu .NET Framework, która jest uruchamiana aplikacja.

Ze względu na to ograniczenie gwarancje zgodności są szczególnie ważne dla składników. Począwszy od programu .NET Framework 4, można określić stopień, w jakim składnik powinien być zgodny w wielu wersjach, stosując <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> atrybutu do tego składnika. Narzędzia ten atrybut służy do wykrywania potencjalnych naruszeń zgodności gwarantuje w przyszłych wersjach składnika.

## <a name="backward-compatibility-and-the-net-framework"></a>Zgodność z poprzednimi wersjami i .NET Framework

.NET Framework 4.5 i nowsze wersje są zgodne wstecz z aplikacjami, które zostały utworzone w starszych wersjach programu .NET Framework. Innymi słowy aplikacje i składniki utworzone w starszych wersjach będą działać bez żadnych modyfikacji na .NET Framework 4.5 lub nowszy. Jednak domyślnie aplikacje działają w wersjach środowiska CLR, dla którego zostały opracowane, więc może trzeba będzie podać plik konfiguracji, aby umożliwić aplikacji uruchamiania na .NET Framework 4.5 lub nowszy. Aby uzyskać więcej informacji, zobacz [zgodność wersji aplikacji](#Apps) sekcji we wcześniejszej części tego artykułu.

W praktyce tę zgodność można zaburzyć przez niekonsekwentne zmiany w .NET Framework i zmiany w technikach programowania. Ulepszenia wydajności w .NET Framework 4.5 można na przykład ujawnić wyścigu, która nie nastąpiła we wcześniejszych wersjach. Podobnie za pomocą ustalona ścieżka do zestawów .NET Framework, wykonywania porównania z określoną wersą .NET Framework i pobierania wartości pola prywatnego przy użyciu odbicia nie są praktykami zgodności z poprzednimi wersjami. Ponadto każda wersja programu .NET Framework zawiera poprawki i zmiany dotyczące zabezpieczeń, które mogą wpływać na zgodność niektórych aplikacji i składników.

Jeśli aplikacja lub składnik nie działa zgodnie z oczekiwaniami w .NET Framework 4.5 (w tym jego wydania punktowe, .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 lub 4.8), użyj poniższych list kontrolnych:

- Jeśli aplikacja została opracowana działają w dowolnej wersji programu .NET Framework, począwszy od programu .NET Framework 4.0, zobacz [zgodność aplikacji w programie .NET Framework](application-compatibility.md) do wygenerowania listy zmian między wersjami usługi wersję docelową .NET Framework i wersja, na którym uruchomiona jest aplikacja.

- Jeśli masz aplikację .NET Framework 3.5, zobacz też [zagadnienia dotyczące migracji programu .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md).

- Jeśli masz aplikację .NET Framework 2.0, zobacz też [zmiany w .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkId=186989).

- Jeśli masz aplikację .NET Framework 1.1, zobacz też [zmiany w programie .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkID=125263).

- Sprawdź, czy w przypadku konieczności ponownego kompilowania istniejący kod źródłowy do uruchamiania na .NET Framework 4.5 lub jego punktu wersji, czy tworzysz nową wersję aplikacji lub składnika, który jest przeznaczony dla .NET Framework 4.5 lub jego wydania punktowe z istniejącej bazy kodu źródłowego, [What's Obsolete in biblioteki klas](../whats-new/whats-obsolete.md) opis przestarzałych typów i członków i zastosuj opisane obejście. (Wcześniej skompilowany kod będzie wykonywany dla typów i członków, którzy zostali oznaczeni jako przestarzali.)

- Jeśli okaże się, że zmiany w .NET Framework 4.5 zniszczyła aplikację, sprawdź [schemat ustawień środowiska uruchomieniowego](../configure-apps/file-schema/runtime/index.md), a szczególnie [ \<AppContextSwitchOverrides > Element](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), Ustal, czy możesz użyć ustawienia środowiska uruchomieniowego w pliku konfiguracyjnym aplikacji, można przywrócić poprzednie zachowanie.

- Jeśli trafisz na problem, który nie jest udokumentowany, otwórz problem na [witrynę społeczność deweloperów rozwiązań dla platformy .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) lub Otwórz problem w [repozytorium GitHub Microsoft/dotnet](https://github.com/microsoft/dotnet/issues).

## <a name="compatibility-and-side-by-side-execution"></a>Zgodność i side-by-side wykonywania

Jeśli nie możesz znaleźć odpowiedniego obejścia problemu, należy pamiętać, że działa równocześnie z wersjami 1.1, 2.0 i 3.5 programu .NET Framework 4.5 (lub jeden z jego wydania punktowe) i stanowi aktualizację w miejscu, która zastępuje wersję 4. W przypadku aplikacji przeznaczonych dla wersji 1.1, 2.0 i 3.5 można zainstalować odpowiednią wersję programu .NET Framework na komputerze docelowym, aby uruchomić aplikację w najlepszym środowisku. Aby uzyskać więcej informacji na temat wykonywania side-by-side zobacz [Side-by-Side Execution](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Zobacz także

- [Co nowego](../whats-new/index.md)
- [Przestarzałe elementy w ułatwieniach dostępu](../whats-new/whats-obsolete.md)
- [Zgodność aplikacji](../migration-guide/application-compatibility.md)
- [Microsoft .NET Framework Support Lifecycle Policy](https://go.microsoft.com/fwlink/p/?LinkId=248212)
- [Zagadnienia dotyczące migracji programu .NET framework 4](../migration-guide/net-framework-4-migration-issues.md)
