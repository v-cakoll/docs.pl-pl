---
title: Zgodność wersji w ramach .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: e0de18b5a40875d1fec2633c16688111d8f4b9ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73974956"
---
# <a name="version-compatibility-in-the-net-framework"></a>Zgodność wersji w ramach .NET Framework

Zgodność wsteczna oznacza, że aplikacja, która została opracowana dla określonej wersji platformy będzie działać na nowszych wersjach tej platformy. Program .NET Framework próbuje zmaksymalizować zgodność z powrotem: kod źródłowy napisany dla jednej wersji programu .NET Framework powinien być kompilowany w nowszych wersjach programu .NET Framework, a pliki binarne uruchamiane w jednej wersji programu .NET Framework powinny zachowywać się identycznie na nowszych wersji programu .NET Framework.

## <a name="version-compatibility-for-apps"></a><a name="Apps"></a>Zgodność wersji dla aplikacji

Domyślnie aplikacja jest uruchamiana w wersji programu .NET Framework, dla których została zbudowana. Jeśli tej wersji nie ma i plik konfiguracji aplikacji nie definiuje obsługiwanych wersji, może wystąpić błąd inicjowania programu .NET Framework. W takim przypadku próba uruchomienia aplikacji zakończy się niepowodzeniem.

Aby zdefiniować określone wersje, na których działa aplikacja, dodaj jeden lub więcej [ \<obsługiwanychruntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) elementów do pliku konfiguracji aplikacji. Każdy `<supportedRuntime>` element zawiera listę obsługiwanej wersji środowiska wykonawczego, z pierwszym określania najbardziej preferowanej wersji i ostatni określania najmniej preferowanej wersji.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie aplikacji do obsługi programu .NET Framework 4 lub 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Zgodność wersji dla komponentów

Aplikacja może kontrolować wersję programu .NET Framework, na której jest uruchamiana, ale składnik nie może. Składniki i biblioteki klas są ładowane w kontekście określonej aplikacji i dlatego są automatycznie uruchamiane w wersji programu .NET Framework, na których działa aplikacja.

Z powodu tego ograniczenia gwarancje zgodności są szczególnie ważne dla składników. Począwszy od programu .NET Framework 4, można określić stopień, w jakim składnik <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> ma pozostać zgodny w wielu wersjach, stosując atrybut do tego składnika. Narzędzia mogą używać tego atrybutu do wykrywania potencjalnych naruszeń gwarancji zgodności w przyszłych wersjach składnika.

## <a name="backward-compatibility-and-the-net-framework"></a>Zgodność z powrotem i program .NET Framework

.NET Framework 4.5 i nowsze wersje są wstecznie zgodne z aplikacjami, które zostały utworzone we wcześniejszych wersjach programu .NET Framework. Innymi słowy aplikacje i składniki utworzone z poprzednich wersji będzie działać bez modyfikacji w .NET Framework 4.5 i nowszych wersjach. Jednak domyślnie aplikacje są uruchamiane w wersji środowiska wykonawczego języka wspólnego, dla którego zostały opracowane, więc może być wymagane podanie pliku konfiguracji, aby umożliwić uruchamianie aplikacji w wersjach .NET Framework 4.5 lub nowszych. Aby uzyskać więcej informacji, zobacz [zgodność wersji dla aplikacji](#Apps) sekcji wcześniej w tym artykule.

W praktyce ta zgodność może być przerwana przez pozornie nieistotne zmiany w programie .NET Framework i zmiany w technikach programowania. Na przykład ulepszenia wydajności w programie .NET Framework 4.5 może uwidaczniać stan wyścigu, który nie wystąpił we wcześniejszych wersjach. Podobnie przy użyciu ścieżki zakodowane do .NET Framework zestawów, wykonywanie porównania równości z określonej wersji .NET Framework i uzyskanie wartości pola prywatnego przy użyciu odbicia nie są wstecznie zgodne praktyki. Ponadto każda wersja programu .NET Framework zawiera poprawki błędów i zmiany związane z zabezpieczeniami, które mogą mieć wpływ na zgodność niektórych aplikacji i składników.

Jeśli aplikacja lub składnik nie działa zgodnie z oczekiwaniami w programie .NET Framework 4.5 (w tym w punktach, w .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 lub 4.8), należy użyć następujących list kontrolnych:

- Jeśli aplikacja została opracowana do uruchamiania w dowolnej wersji programu .NET Framework, począwszy od programu .NET Framework 4.0, zobacz Zgodność aplikacji, aby [wygenerować](application-compatibility.md) listy zmian między docelową wersją programu .NET Framework a wersją, na której jest uruchomiona aplikacja.

- Jeśli masz aplikację .NET Framework 3.5, zobacz też [problemy z migracją programu .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md).

- Jeśli masz aplikację .NET Framework 2.0, zobacz także [Zmiany w systemie .NET Framework 3.5 z dodatkiem SP1](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10)).

- Jeśli masz aplikację .NET Framework 1.1, zobacz także [Zmiany w .NET Framework 2.0](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10)).

- Jeśli ponownie komponujesz istniejący kod źródłowy do uruchomienia w programie .NET Framework 4.5 lub jego wersjach punktowych lub jeśli tworzysz nową wersję aplikacji lub składnika przeznaczonego dla programu .NET Framework 4.5 lub jego wersji punktowych z istniejącej bazy kodu źródłowego, sprawdź, [co jest przestarzałe w bibliotece klas](../whats-new/whats-obsolete.md) dla przestarzałych typów i elementów członkowskich, i zastosuj opisane obejście. (Wcześniej skompilowany kod będzie nadal działać przeciwko typom i członkom, które zostały oznaczone jako przestarzałe).

- Jeśli okaże się, że zmiana w .NET Framework 4.5 została przerwana aplikacji, sprawdź [schemat ustawień środowiska wykonawczego](../configure-apps/file-schema/runtime/index.md), a zwłaszcza [ \<AppContextSwitchOverrides> Element](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), aby ustalić, czy można użyć ustawienia środowiska uruchomieniowego w pliku konfiguracyjnym aplikacji, aby przywrócić poprzednie zachowanie.

- Jeśli natkniesz się na problem, który nie jest udokumentowany, otwórz problem w [witrynie społeczności deweloperów dla platformy .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) lub otwórz problem w [repozytorium Microsoft/dotnet GitHub](https://github.com/microsoft/dotnet/issues).

## <a name="compatibility-and-side-by-side-execution"></a>Kompatybilność i wykonanie obok siebie

Jeśli nie możesz znaleźć odpowiedniego rozwiązania problemu, pamiętaj, że program .NET Framework 4.5 (lub jedna z jego wersji punktowych) jest uruchamiany obok wersji 1.1, 2.0 i 3.5 i jest aktualizacją w miejscu, która zastępuje wersję 4. W przypadku aplikacji docelowych w wersjach 1.1, 2.0 i 3.5 można zainstalować odpowiednią wersję programu .NET Framework na komputerze docelowym, aby uruchomić aplikację w najlepszym środowisku. Aby uzyskać więcej informacji na temat wykonywania obok siebie, zobacz [Wykonanie side-by-Side](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Zobacz też

- [Co nowego](../whats-new/index.md)
- [Przestarzałe elementy w ułatwieniach dostępu](../whats-new/whats-obsolete.md)
- [Zgodność aplikacji](../migration-guide/application-compatibility.md)
- [Oficjalna polityka wsparcia .NET Framework](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Problemy z migracją programu .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md)
