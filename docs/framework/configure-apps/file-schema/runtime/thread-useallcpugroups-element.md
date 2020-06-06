---
title: <Thread_UseAllCpuGroups>, element
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115408"
---
# <a name="thread_useallcpugroups-element"></a>\<Thread_UseAllCpuGroups> Element

Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

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
|`true`|Środowisko uruchomieniowe dystrybuuje wątki zarządzane do wielu grup procesorów, jeśli komputer ma wiele grup CPU, a [\<GCCpuGroup>](gccpugroup-element.md) element jest włączony.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Gdy komputer ma wiele grup CPU, włączenie tego elementu powoduje, że środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora. Aby użyć tej funkcji, należy również włączyć [\<GCCpuGroup>](gccpugroup-element.md) element, który rozszerza wyrzucanie elementów bezużytecznych do wszystkich grup CPU i pobiera wszystkie rdzenie do konta podczas tworzenia i równoważenia sterty. Włączenie [\<GCCpuGroup>](gccpugroup-element.md) elementu wymaga włączenia [\<gcServer>](gcserver-element.md) elementu. Jeśli te elementy nie są włączone, włączenie `<Thread_UseAllCpuGroups>` elementu nie ma żadnego wpływu.

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
- [\<GCCpuGroup>Postaci](gccpugroup-element.md)
