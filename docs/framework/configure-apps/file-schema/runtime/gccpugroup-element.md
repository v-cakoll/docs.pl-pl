---
title: <GCCpuGroup>, element
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102895"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup> Element

Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU.

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>GCCpuGroup**

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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU.|

## <a name="enabled-attribute"></a>Atrybut włączony

|Wartość|Opis|
|-----------|-----------------|
|`false`|Wyrzucanie elementów bezużytecznych nie obsługuje wielu grup procesora CPU. Domyślnie włączone.|
|`true`|Wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU, jeśli jest włączone wyrzucanie elementów bezużytecznych serwera.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Gdy komputer ma wiele grup procesora CPU i jest włączone wyrzucanie elementów bezużytecznych serwera (zobacz [ \<gcServer>](gcserver-element.md) element), włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach procesora CPU i uwzględnia wszystkie rdzenie podczas tworzenia i równoważenia sterty.

> [!NOTE]
> Ten element ma zastosowanie tylko do wątków wyrzucania elementów bezużytecznych. Aby włączyć środowisko uruchomieniowe do dystrybucji wątków użytkownika we wszystkich grupach procesora CPU, należy również włączyć [ \<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak włączyć wyrzucanie elementów bezużytecznych dla wielu grup procesora CPU.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Wyłącz równoczesne wyrzucanie elementów bezużytecznych](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Wyrzucanie elementów bezużytecznych stacji roboczych i serwera](../../../../standard/garbage-collection/workstation-server-gc.md)
