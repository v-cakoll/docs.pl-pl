---
title: Zgodność wersji w .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: 1a3c23a70bc7dc519c824426f8939cb15e87a7fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128055"
---
# <a name="version-compatibility-in-the-net-framework"></a>Zgodność wersji w .NET Framework

Zgodność z poprzednimi wersjami oznacza, że aplikacja opracowana dla konkretnej wersji platformy będzie działać w nowszych wersjach tej platformy. .NET Framework próbuje zmaksymalizować zgodność z poprzednimi wersjami: kod źródłowy zapisany dla jednej wersji .NET Framework powinien zostać skompilowany w nowszych wersjach .NET Framework, a pliki binarne, które działają w jednej wersji .NET Framework powinny zachowywać się identycznie. nowsze wersje .NET Framework.

## <a name="Apps"></a>Zgodność wersji aplikacji

Domyślnie aplikacja jest uruchamiana w wersji .NET Framework, dla której została skompilowana. Jeśli ta wersja nie jest obecna, a plik konfiguracji aplikacji nie definiuje obsługiwanych wersji, może wystąpić błąd inicjalizacji .NET Framework. W takim przypadku próba uruchomienia aplikacji nie powiedzie się.

Aby zdefiniować konkretne wersje, na których działa aplikacja, Dodaj co najmniej jeden [\<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) elementów do pliku konfiguracji aplikacji. Każdy element `<supportedRuntime>` zawiera obsługiwaną wersję środowiska uruchomieniowego, z pierwszym określeniem najbardziej preferowanej wersji i ostatnim określeniem najmniejszej wersji.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Aby uzyskać więcej informacji, zobacz [How to: Configure a App to Support .NET Framework 4 lub 4. x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Zgodność wersji składników

Aplikacja może kontrolować wersję .NET Framework, na którym działa, ale składnik nie może. Składniki i biblioteki klas są ładowane w kontekście określonej aplikacji i dlatego automatycznie są uruchamiane w wersji .NET Framework, na której działa aplikacja.

Z powodu tego ograniczenia gwarancje zgodności są szczególnie ważne dla składników. Począwszy od .NET Framework 4, można określić stopień, w jakim składnik powinien być zgodny w wielu wersjach, stosując atrybut <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> do tego składnika. Za pomocą tego atrybutu narzędzia mogą wykrywać potencjalne naruszenia gwarancji zgodności w przyszłych wersjach składnika.

## <a name="backward-compatibility-and-the-net-framework"></a>Zgodność z poprzednimi wersjami i .NET Framework

.NET Framework 4,5 i nowsze wersje są zgodne wstecz z aplikacjami, które zostały skompilowane ze starszymi wersjami .NET Framework. Innymi słowy aplikacje i składniki utworzone przy użyciu poprzednich wersji będą działały bez modyfikacji w .NET Framework 4,5 i nowszych wersjach. Jednak domyślnie aplikacje są uruchamiane w wersji środowiska uruchomieniowego języka wspólnego, dla którego zostały opracowane, więc może być konieczne dostarczenie pliku konfiguracji w celu umożliwienia uruchomienia aplikacji w .NET Framework 4,5 lub nowszych. Aby uzyskać więcej informacji, zobacz sekcję [zgodność wersji dla aplikacji](#Apps) wcześniej w tym artykule.

W tym celu zgodność może być uszkodzona przez pozornie zmiany w .NET Framework i zmiany w technikach programowania. Na przykład ulepszenia wydajności w .NET Framework 4,5 mogą uwidaczniać sytuację wyścigu, która nie miała miejsca we wcześniejszych wersjach. Podobnie przy użyciu zakodowanej ścieżki do .NET Framework zestawów, wykonywanie porównania równości z określoną wersją .NET Framework i pobieranie wartości pola prywatnego przy użyciu odbicia nie jest zgodne z poprzednimi wersjami. Ponadto każda wersja .NET Framework zawiera poprawki błędów i zmiany dotyczące zabezpieczeń, które mogą wpływać na zgodność niektórych aplikacji i składników.

Jeśli aplikacja lub składnik nie działa zgodnie z oczekiwaniami w .NET Framework 4,5 (łącznie z wersjami punktów, .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 lub 4,8), użyj następujących list kontrolnych:

- Jeśli aplikacja została opracowana tak, aby była uruchamiana w dowolnej wersji .NET Framework począwszy od .NET Framework 4,0, zobacz [zgodność aplikacji w .NET Framework](application-compatibility.md) , aby generować listy zmian między dodaną wersją .NET Framework i wersją, w której Twoja aplikacja jest uruchomiona.

- Jeśli masz aplikację .NET Framework 3,5, zobacz również problemy z [migracją .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md).

- Jeśli masz aplikację .NET Framework 2,0, zobacz również [zmiany w programie .NET Framework 3,5 z dodatkiem SP1](https://go.microsoft.com/fwlink/?LinkId=186989).

- Jeśli masz aplikację .NET Framework 1,1, zobacz również [zmiany w .NET Framework 2,0](https://go.microsoft.com/fwlink/?LinkID=125263).

- Jeśli ponownie kompilujesz istniejący kod źródłowy do uruchomienia w .NET Framework 4,5 lub jego wydania punktowe lub jeśli tworzysz nową wersję aplikacji lub składnika, który jest przeznaczony dla .NET Framework 4,5 lub jego wydań punktów z istniejącej bazy kodu źródłowego, sprawdź, [co Przestarzałe w bibliotece klas](../whats-new/whats-obsolete.md) dla przestarzałych typów i elementów członkowskich i zastosować opisane obejście. (Poprzednio skompilowany kod będzie kontynuował pracę względem typów i elementów członkowskich, które zostały oznaczone jako przestarzałe.)

- Jeśli określisz, że zmiana w .NET Framework 4,5 spowodowała uszkodzenie aplikacji, sprawdź [Schemat ustawień środowiska uruchomieniowego](../configure-apps/file-schema/runtime/index.md), a szczególnie [\<AppContextSwitchOverrides > elementu](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), aby określić, czy można użyć ustawienia środowiska uruchomieniowego w plik konfiguracji aplikacji, aby przywrócić poprzednie zachowanie.

- Jeśli występują problemy, które nie są udokumentowane, Otwórz problem w [witrynie społeczności deweloperów dla platformy .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) lub Otwórz problem w [repozytorium GitHub Microsoft/dotnet](https://github.com/microsoft/dotnet/issues).

## <a name="compatibility-and-side-by-side-execution"></a>Zgodność i wykonywanie równoczesne

Jeśli nie możesz znaleźć odpowiedniego obejścia problemu, pamiętaj, że .NET Framework 4,5 (lub jeden z jego wydań) działa równolegle z wersjami 1,1, 2,0 i 3,5, i jest aktualizacją w miejscu, która zastępuje wersję 4. W przypadku aplikacji przeznaczonych dla wersji 1,1, 2,0 i 3,5 można zainstalować odpowiednią wersję .NET Framework na komputerze docelowym, aby uruchomić aplikację w najlepszym środowisku. Aby uzyskać więcej informacji na temat wykonywania równoczesnego, zobacz [Wykonywanie równoczesne](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Zobacz także

- [Co nowego?](../whats-new/index.md)
- [Przestarzałe elementy w ułatwieniach dostępu](../whats-new/whats-obsolete.md)
- [Zgodność aplikacji](../migration-guide/application-compatibility.md)
- [Zasady cyklu życia obsługi Microsoft .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=248212)
- [Problemy z migracją .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md)
