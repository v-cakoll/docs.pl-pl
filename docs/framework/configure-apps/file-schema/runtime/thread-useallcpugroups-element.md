---
title: <Thread_UseAllCpuGroups>, element
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115408"
---
# <a name="thread_useallcpugroups-element"></a>\<element > Thread_UseAllCpuGroups

Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups >**  

## <a name="syntax"></a>Składnia

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.|

## <a name="enabled-attribute"></a>Atrybut włączony

|Wartość|Opis|
|-----------|-----------------|
|`false`|Środowisko uruchomieniowe nie dystrybuuje zarządzanych wątków w wielu grupach procesorów. Domyślnie włączone.|
|`true`|Środowisko uruchomieniowe dystrybuuje wątki zarządzane do wielu grup procesorów, jeśli komputer ma wiele grup CPU i jest włączony [\<GCCpuGroup >](gccpugroup-element.md) .|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Gdy komputer ma wiele grup CPU, włączenie tego elementu powoduje, że środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora. Aby użyć tej funkcji, należy również włączyć [\<GCCpuGroup >](gccpugroup-element.md) elementu, który rozszerza odzyskiwanie pamięci do wszystkich grup CPU i pobiera wszystkie rdzenie w przypadku tworzenia i równoważenia sterty. Włączenie elementu [\<GCCpuGroup >](gccpugroup-element.md) wymaga włączenia [\<gcServer >](gcserver-element.md) elementu. Jeśli te elementy nie są włączone, włączenie elementu `<Thread_UseAllCpuGroups>` nie ma żadnego wpływu.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [\<element > GCCpuGroup](gccpugroup-element.md)
