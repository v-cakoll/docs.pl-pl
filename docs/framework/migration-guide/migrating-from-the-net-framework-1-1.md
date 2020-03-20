---
title: Migracja z programu .NET Framework 1.1
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
ms.openlocfilehash: 11fe9ba36d32a4c9fe363b48f76a8bb2b24f073b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73974968"
---
# <a name="migrate-from-the-net-framework-11"></a>Migrowanie z programu .NET Framework 1.1

Windows 7 i nowsze wersje systemu operacyjnego Windows nie obsługują programu .NET Framework 1.1. W rezultacie aplikacje przeznaczone dla programu .NET Framework 1.1 nie będą uruchamiane bez modyfikacji w wersjach systemu operacyjnego Windows 7 lub nowszych. W tym temacie omówiono kroki wymagane do uruchomienia aplikacji przeznaczonej dla programu .NET Framework 1.1 w systemie Windows 7 i nowszych wersjach systemu operacyjnego Windows. Aby uzyskać więcej informacji na temat programu .NET Framework 1.1 i Windows 8, zobacz [Uruchamianie aplikacji .NET Framework 1.1 w systemie Windows 8 i nowszych wersjach](../install/run-net-framework-1-1-apps.md).

## <a name="retarget-or-recompile"></a>Ponowne kierowanie lub ponowne komplety

Istnieją dwa sposoby, aby uzyskać aplikację, która została skompilowana przy użyciu programu .NET Framework 1.1 do uruchomienia w systemie Windows 7 lub nowszym systemie operacyjnym Windows:

- Ponownie kieruj aplikację do uruchomienia w ramach platformy .NET Framework 4 i nowszych wersji. Retargeting wymaga [ \<dodania obsługiwaneruntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) element do pliku konfiguracyjnego aplikacji, który umożliwia jego uruchamianie w ramach .NET Framework 4 i nowszych wersjach. Taki plik konfiguracyjny ma następującą formę:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Ponownie skompiluj aplikację za pomocą kompilatora przeznaczonego dla programu .NET Framework 4 lub nowszej. Jeśli pierwotnie użyto programu Visual Studio 2003 do opracowania i skompilowania rozwiązania, można otworzyć rozwiązanie w programie Visual Studio 2010 (i ewentualnie nowsze wersje też) i użyć okna dialogowego Zgodności projektu do **konwersji** plików rozwiązania i projektu z formatów używanych przez program Visual Studio 2003 do formatu Microsoft Build Engine (MSBuild).

Niezależnie od tego, czy wolisz ponownie skompilować lub ponownie przekierować aplikację, należy określić, czy aplikacja jest narażony na zmiany wprowadzone w nowszych wersjach programu .NET Framework. Zmiany te są dwojaki:

- Przerywanie zmian, które wystąpiły między .NET Framework 1.1 i nowszych wersjach programu .NET Framework.

- Typy i typ elementów członkowskich, które zostały oznaczone jako przestarzałe lub przestarzałe między .NET Framework 1.1 i nowszych wersjach programu .NET Framework.

Niezależnie od tego, czy ponownie celujesz aplikację, czy ponownie ją skompilować, należy przejrzeć zarówno zmiany podziału, jak i przestarzałe typy i elementy członkowskie dla każdej wersji programu .NET Framework, która została wydana po wydaniu programu .NET Framework 1.1.

## <a name="breaking-changes"></a>Zmiany powodujące niezgodność

W przypadku zmiany podziału, w zależności od konkretnej zmiany, obejście może być dostępne zarówno dla retargetowanych, jak i ponownie skompilowanych aplikacji. W niektórych przypadkach można dodać element podrzędny do [ \<środowiska wykonawczego>](../configure-apps/file-schema/startup/supportedruntime-element.md) element pliku konfiguracyjnego aplikacji, aby przywrócić poprzednie zachowanie. Na przykład następujący plik konfiguracji przywraca zachowanie sortowania i porównywania ciągów używane w programie .NET Framework 1.1 i może być używane z ponownie kierowaną lub ponownie skompilowanym aplikacją.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Jednak w niektórych przypadkach może być trzeba zmodyfikować kod źródłowy i ponownie skompilować aplikację.

Aby ocenić wpływ ewentualnych zmian w aplikacji, należy przejrzeć następujące listy zmian:

- [Breaking Zmiany w .NET Framework 2.0](https://docs.microsoft.com/previous-versions/aa570326(v=msdn.10)) dokumentów zmian w .NET Framework 2.0 SP1, które mogą mieć wpływ na aplikację, która jest przeznaczona dla platformy .NET Framework 1.1.

- Zmiany w dokumentach [.NET Framework 3.5 z SP1](https://docs.microsoft.com/previous-versions/dotnet/articles/dd310284(v=msdn.10)) zmieniają się między programem .NET Framework 3.5 a programem .NET Framework 3.5 SP1.

- [Problemy z migracją programu .NET Framework 4](net-framework-4-migration-issues.md) dokumentuje zmiany między programem .NET Framework 3.5 SP1 a programem .NET Framework 4.

## <a name="obsolete-types-and-members"></a>Przestarzałe typy i elementy członkowskie

Wpływ przestarzałych typów i elementów członkowskich jest nieco inny w przypadku aplikacji retargetowanych i ponownie skompilowanych aplikacji. Użycie przestarzałych typów i elementów członkowskich nie wpłynie na ponownie kierowaną aplikację, chyba że przestarzały typ lub element członkowski został fizycznie usunięty z zestawu. Ponowne kompilowanie aplikacji, która używa przestarzałych typów lub elementów członkowskich zwykle generuje ostrzeżenie kompilatora, a nie błąd kompilatora. Jednak w niektórych przypadkach generuje błąd kompilatora i kod, który używa przestarzałego typu lub elementu członkowskiego nie kompiluje pomyślnie. W takim przypadku należy przepisać kod źródłowy, który wywołuje przestarzały typ lub element członkowski przed ponownym skompilowania aplikacji. Aby uzyskać więcej informacji na temat przestarzałych typów i elementów członkowskich, zobacz [Co jest przestarzałe w bibliotece klas](../whats-new/whats-obsolete.md).

Aby ocenić wpływ typów i elementów członkowskich, które zostały przestarzałe od czasu wydania dodatku SP1 .NET Framework 2.0, zobacz [Co jest przestarzałe w bibliotece klas](../whats-new/whats-obsolete.md). Przejrzyj listy przestarzałych typów i członków programu .NET Framework 2.0 SP1, programu .NET Framework 3.5 i .NET Framework 4.
