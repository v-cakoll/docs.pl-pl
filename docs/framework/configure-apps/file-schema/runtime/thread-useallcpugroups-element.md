---
title: <Thread_UseAllCpuGroups> Element
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e964f1b2861926803b0449be06cbfd9567ac74a3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252273"
---
# <a name="thread_useallcpugroups-element"></a>\<Thread_UseAllCpuGroups> Element

Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)\
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
|`true`|Środowisko uruchomieniowe dystrybuuje wątki zarządzane między wiele grup CPU, jeśli komputer ma wiele grup CPU i [ \<GCCpuGroup element >](gccpugroup-element.md) jest włączony.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Gdy komputer ma wiele grup CPU, włączenie tego elementu powoduje, że środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora. Aby użyć tej funkcji, należy również włączyć [ \<GCCpuGroup >](gccpugroup-element.md) , który rozszerza odzyskiwanie pamięci do wszystkich grup CPU i pobiera wszystkie rdzenie w przypadku tworzenia i równoważenia sterty. Włączenie elementu > [ GCCpuGroupwymagawłączeniaelementugcServer>.\<](gcserver-element.md) [ \<](gccpugroup-element.md) Jeśli te elementy nie są włączone, włączenie `<Thread_UseAllCpuGroups>` elementu nie ma żadnego wpływu.

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
- [\<GCCpuGroup> Element](gccpugroup-element.md)
