---
title: <GCCpuGroup> Element
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102895"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup> Element

Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

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

Gdy komputer ma wiele grup CPU i jest włączone odzyskiwanie pamięci serwera (zobacz [\<gcServer>](gcserver-element.md) element), włączenie tego elementu rozszerza odzyskiwanie pamięci dla wszystkich grup CPU i pobiera wszystkie rdzenie w przypadku tworzenia i równoważenia sterty.

> [!NOTE]
> Ten element ma zastosowanie tylko do wątków wyrzucania elementów bezużytecznych. Aby umożliwić środowisko uruchomieniowe dystrybuowanie wątków użytkownika między wszystkimi grupami CPU, należy również włączyć [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.

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
- [Wyłącz współbieżne wyrzucanie elementów bezużytecznych](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Stacja robocza i odzyskiwanie pamięci serwera](../../../../standard/garbage-collection/workstation-server-gc.md)
