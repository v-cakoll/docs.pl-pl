---
title: <GCCpuGroup>, element
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee56b23b6d5fca6d0527d509c9b6a6fc6dd82336
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920779"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup> Element

Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.

\<> konfiguracji \
\<> środowiska uruchomieniowego \
\<GCCpuGroup>

## <a name="syntax"></a>Składnia

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.|

## <a name="enabled-attribute"></a>Atrybut włączony

|Wartość|Opis|
|-----------|-----------------|
|`false`|Wyrzucanie elementów bezużytecznych nie obsługuje wielu grup procesorów. Domyślnie włączone.|
|`true`|Wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów, jeśli jest włączone odzyskiwanie pamięci serwera.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Jeśli na komputerze jest włączona wiele grup CPU i wyrzucanie elementów bezużytecznych serwera (zobacz [ \<gcServer >](gcserver-element.md) element), włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach CPU i pobiera wszystkie rdzenie podczas tworzenia i Zrównoważ sterty.

> [!NOTE]
> Ten element ma zastosowanie tylko do wątków wyrzucania elementów bezużytecznych. Aby umożliwić środowisko uruchomieniowe dystrybuowanie wątków użytkownika między wszystkimi grupami CPU, należy również włączyć [ \<element > Thread_UseAllCpuGroups](thread-useallcpugroups-element.md) .

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak włączyć odzyskiwanie pamięci dla wielu grup procesorów.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Stacja robocza i odzyskiwanie pamięci serwera](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
