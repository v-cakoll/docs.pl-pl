---
title: Migracja z programu .NET Framework 1.1
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9671dd87e3185e9d4b997e2ea75770f756605efb
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833517"
---
# <a name="migrating-from-the-net-framework-11"></a>Migracja z programu .NET Framework 1.1

[!INCLUDE[win7](../../../includes/win7-md.md)] i nowszymi wersjami systemu operacyjnego Windows nie obsługują programu .NET Framework 1.1. W rezultacie aplikacji przeznaczonych dla środowiska .NET Framework 1.1 nie będzie działać bez żadnych modyfikacji na [!INCLUDE[win7](../../../includes/win7-md.md)] lub nowszej wersji systemu operacyjnego. W tym temacie omówiono kroki wymagane do uruchamiania aplikacji, który jest przeznaczony dla .NET Framework 1.1 w obszarze [!INCLUDE[win7](../../../includes/win7-md.md)] i nowszych wersjach systemu operacyjnego Windows. Aby uzyskać więcej informacji na temat programu .NET Framework 1.1 i [!INCLUDE[win8](../../../includes/win8-md.md)], zobacz [systemem 1.1 aplikacji programu .NET Framework w systemie Windows 8 i nowszych wersjach](../../../docs/framework/install/run-net-framework-1-1-apps.md).

## <a name="retargeting-or-recompiling"></a>Retargeting i ponowna kompilacja

Istnieją dwa sposoby uzyskania aplikacji skompilowanej przy użyciu programu .NET Framework 1.1 w celu uruchamiania [!INCLUDE[win7](../../../includes/win7-md.md)] lub nowszej wersji systemu operacyjnego Windows:

- Można przekierować aplikację do uruchamiania w .NET Framework 4 i nowsze wersje. Trwa przekierowywanie wymaga dodania [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementu do pliku konfiguracji aplikacji, który umożliwia jego uruchomienie w ramach programu .NET Framework 4 i nowsze wersje. Taki plik konfiguracyjny ma następującą postać:

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0"/>
       </startup>
    </configuration>
    ```

- Można ponownie skompilować aplikację za pomocą kompilatora przeznaczonego do .NET Framework 4 lub nowszy. Jeśli początkowo używano programu Visual Studio 2003 do utworzenia i skompilowania rozwiązania, można otworzyć rozwiązanie w programie Visual Studio 2010 (i ewentualnie nowsze wersje zbyt) i używać **zgodności projektu** okno dialogowe, aby skonwertować rozwiązanie i pliki projektu z formatów używanych przez program Visual Studio 2003 na format aparatu Microsoft Build Engine (MSBuild).

Niezależnie od tego, czy wolisz ponownie skompilować czy przekierować aplikację musisz określić, czy aplikacja jest wpływ na wszelkie zmiany wprowadzone w nowszych wersjach programu .NET Framework. Zmiany te mają dwie formy:

- Fundamentalne zmiany między .NET Framework 1.1 i nowszych wersjach programu .NET Framework.

- Typy i składowe typu, które zostały oznaczone jako przestarzałe, lub w programie .NET Framework 1.1 i nowszych wersjach programu .NET Framework.

Czy przekierować aplikację, lub ponownie ją kompilując, należy przejrzeć zarówno przełomowe zmiany oraz przestarzałe typy i członków dla każdej wersji programu .NET Framework, która została wydana po .NET Framework 1.1.

## <a name="breaking-changes"></a>Fundamentalne zmiany

Gdy wystąpi zmiana podziału, w zależności od określonej zmiany obejście tego problemu może być dostępne zarówno dla przekierowano element i ponownie kompilowanych. W niektórych przypadkach można dodać elementu podrzędnego do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element pliku konfiguracji aplikacji, aby przywrócić poprzednie zachowanie. Na przykład następujący plik konfiguracji przywraca sortowanie ciągów i zachowanie porównania używane w .NET Framework 1.1 i może być używany z przebudowanymi pod inne środowisko lub ponownie skompilowanymi aplikacji.

```xml
<configuration>
   <runtime>
      <CompatSortNLSVersion enabled="4096"/>
   </runtime>
</configuration>
```

Jednak w niektórych przypadkach trzeba zmodyfikować kod źródłowy i ponownie skompilować aplikację.

W celu oceny wpływu możliwych przełomowych zmian w swojej aplikacji, należy przejrzeć następujące listy zmian:

- [Istotne zmiany w programie .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkId=125263) dokumentuje zmiany w .NET Framework 2.0 z dodatkiem SP1, który może wpływać na aplikację, który jest przeznaczony dla .NET Framework 1.1.

- [Zmiany w .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkID=186989) dokumentuje zmiany między .NET Framework 3.5 i .NET Framework 3.5 SP1.

- [Zagadnienia dotyczące migracji programu .NET framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) dokumentuje zmiany między .NET Framework 3.5 SP1 i .NET Framework 4.

## <a name="obsolete-types-and-members"></a>Przestarzałe typy i członkowie

Wpływ zdeprecjonowanych typów i składowych jest nieco inny dla aplikacji przekierowanych i ponownie kompilowanych. Korzystanie z przestarzałych typów i elementów członkowskich nie wpłynie na zmienianą aplikację, chyba że przestarzałego typu lub składowej został fizycznie usunięty z zestawu. Konieczności ponownego kompilowania aplikacji korzystającej z przestarzałe typy lub członków zwykle powoduje ostrzeżenia kompilatora, nie błędu kompilatora. Jednak w niektórych przypadkach generuje błąd kompilatora i kod, który używa przestarzałego typu lub składowej nie jest kompilowany pomyślnie. W takim przypadku należy przepisać kod źródłowy, który wywołuje przestarzały typ lub członka, przed ponownym skompilowaniem aplikacji. Aby uzyskać więcej informacji na temat przestarzałych typów i członków, zobacz [What's Obsolete in biblioteki klas](../../../docs/framework/whats-new/whats-obsolete.md).

Aby ocenić wpływ typów i elementów członkowskich, które zostały zaniechane od czasu wersji programu .NET Framework 2.0 z dodatkiem SP1, zobacz [What's Obsolete in biblioteki klas](../../../docs/framework/whats-new/whats-obsolete.md). Przejrzyj listy przestarzałych typów i członków dla platformy .NET Framework 2.0 z dodatkiem SP1, .NET Framework 3.5 i .NET Framework 4.
