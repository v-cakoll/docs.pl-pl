---
title: Migracja z programu .NET Framework 1.1
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: f74b75827770524299f9a25a5854503186139cb4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126293"
---
# <a name="migrating-from-the-net-framework-11"></a>Migracja z programu .NET Framework 1.1

[!INCLUDE[win7](../../../includes/win7-md.md)] i nowsze wersje systemu operacyjnego Windows nie obsługują .NET Framework 1,1. W związku z tym aplikacje przeznaczone dla .NET Framework 1,1 nie będą uruchamiane bez modyfikacji [!INCLUDE[win7](../../../includes/win7-md.md)] lub nowszych wersji systemu operacyjnego. W tym temacie omówiono kroki wymagane do uruchomienia aplikacji, która jest przeznaczona dla .NET Framework 1,1 w obszarze [!INCLUDE[win7](../../../includes/win7-md.md)] i nowszych wersjach systemu operacyjnego Windows. Aby uzyskać więcej informacji na temat .NET Framework 1,1 i [!INCLUDE[win8](../../../includes/win8-md.md)], zobacz [Uruchamianie aplikacji .NET Framework 1,1 w systemie Windows 8 i nowszych wersjach](../install/run-net-framework-1-1-apps.md).

## <a name="retargeting-or-recompiling"></a>Przekierowywanie lub ponowne kompilowanie

Istnieją dwa sposoby uzyskania aplikacji skompilowanej za pomocą .NET Framework 1,1 do uruchamiania w [!INCLUDE[win7](../../../includes/win7-md.md)] lub w późniejszym systemie operacyjnym Windows:

- Można przekierować aplikację do uruchamiania w .NET Framework 4 i nowszych wersjach. Przekierowywanie wymaga dodania elementu [\<supportedRuntime >](../configure-apps/file-schema/startup/supportedruntime-element.md) do pliku konfiguracji aplikacji, który umożliwia uruchamianie go w .NET Framework 4 i nowszych wersjach. Taki plik konfiguracyjny ma następującą postać:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Możesz ponownie skompilować aplikację z kompilatorem przeznaczonym dla .NET Framework 4 lub nowszej wersji. Jeśli program Visual Studio 2003 został pierwotnie użyty do opracowania i skompilowania rozwiązania, można otworzyć rozwiązanie w programie Visual Studio 2010 (a także w późniejszych wersjach) i użyć okna dialogowego **Zgodność projektu** , aby przekonwertować rozwiązanie i pliki projektu z formaty używane przez program Visual Studio 2003 do formatu Microsoft Build Engine (MSBuild).

Bez względu na to, czy wolisz ponownie skompilować lub przekierować aplikację, musisz określić, czy na aplikacji mają wpływ jakiekolwiek zmiany wprowadzone w nowszych wersjach .NET Framework. Te zmiany są dwa rodzaje:

- Istotne zmiany, które wystąpiły między .NET Framework 1,1 i późniejszymi wersjami .NET Framework.

- Typy i elementy członkowskie typu, które zostały oznaczone jako przestarzałe lub przestarzałe między .NET Framework 1,1 i późniejszymi wersjami .NET Framework.

Bez względu na to, czy chcesz przekierować aplikację, czy ją ponownie skompilować, należy przejrzeć zarówno zmiany, jak i przestarzałe typy i elementy członkowskie dla każdej wersji .NET Framework wydanej po .NET Framework 1,1.

## <a name="breaking-changes"></a>Fundamentalne zmiany

Gdy nastąpi zmiana istotna, w zależności od określonej zmiany obejście może być dostępne zarówno w przypadku aplikacji docelowych, jak i ponownie skompilowanych. W niektórych przypadkach można dodać element podrzędny do [> elementu\<środowiska uruchomieniowego](../configure-apps/file-schema/startup/supportedruntime-element.md) w pliku konfiguracji aplikacji, aby przywrócić poprzednie zachowanie. Na przykład następujący plik konfiguracyjny przywraca zachowanie sortowania i porównywania ciągów używane w .NET Framework 1,1 i może być używane z przekierowaniem lub ponowną kompilacją aplikacji.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Jednak w niektórych przypadkach może być konieczne zmodyfikowanie kodu źródłowego i ponowne skompilowanie aplikacji.

Aby ocenić wpływ ewentualnych zmian w aplikacji, należy przejrzeć następujące listy zmian:

- Istotne [zmiany w .NET Framework 2,0](https://go.microsoft.com/fwlink/?LinkId=125263) dokumenty zmiany w .NET Framework 2,0 SP1, które mogą mieć wpływ na aplikację, która jest przeznaczona .NET Framework 1,1.

- [Zmiany w .NET Framework 3,5 z dodatkiem SP1](https://go.microsoft.com/fwlink/?LinkID=186989) zmieniają się między .NET Framework 3,5 i .NET Framework 3,5 SP1.

- [.NET Framework 4 problemy z migracją](net-framework-4-migration-issues.md) dokumentów między .NET Framework 3,5 SP1 a .NET Framework 4.

## <a name="obsolete-types-and-members"></a>Przestarzałe typy i składowe

Skutki przestarzałych typów i elementów członkowskich różnią się w zależności od aplikacji przeznaczonych do przekierowania i ponownie skompilowanych aplikacji. Użycie przestarzałych typów i elementów członkowskich nie będzie miało wpływu na przekierowanie aplikacji, chyba że przestarzały typ lub element członkowski został fizycznie usunięty z jego zestawu. Ponowne kompilowanie aplikacji używającej przestarzałych typów lub składowych zwykle powoduje ostrzeżenie kompilatora, a nie błąd kompilatora. Jednak w niektórych przypadkach generuje błąd kompilatora i kod, który używa przestarzałego typu lub elementu członkowskiego, nie kompiluje się pomyślnie. W takim przypadku należy ponownie napisać kod źródłowy, który wywołuje przestarzały typ lub element członkowski przed ponowną kompilacją aplikacji. Aby uzyskać więcej informacji na temat przestarzałych typów i członków, zobacz [co jest przestarzałe w bibliotece klas](../whats-new/whats-obsolete.md).

Aby ocenić wpływ typów i elementów członkowskich, które zostały zaniechane od czasu wydania .NET Framework 2,0 z dodatkiem SP1, zobacz, [co jest przestarzałe w bibliotece klas](../whats-new/whats-obsolete.md). Zapoznaj się z listą przestarzałych typów i elementów członkowskich dla .NET Framework 2,0 SP1, .NET Framework 3,5 i .NET Framework 4.
