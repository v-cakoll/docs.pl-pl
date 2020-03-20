---
title: gcCzłonek koncurrent
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400044"
---
# <a name="gcconcurrent-element"></a>\<gcWliczna> element

Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia wyrzucanie elementów bezużytecznych w oddzielnym wątku.

[\<>konfiguracyjne](../configuration-element.md)\
&nbsp;&nbsp;[\<>czasu wykonywania](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<> gcConcurrent

## <a name="syntax"></a>Składnia

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br />Określa, czy środowisko uruchomieniowe uruchamia wyrzucanie elementów bezużytecznych jednocześnie.|

#### <a name="enabled-attribute"></a>włączony atrybut

|Wartość|Opis|
|-----------|-----------------|
|`false`|Nie uruchamia wyrzucania elementów bezużytecznych jednocześnie.|
|`true`|Uruchamia wyrzucania elementów bezużytecznych jednocześnie. Domyślnie włączone.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Przed .NET Framework 4, wyrzucania elementów bezużytecznych stacji roboczej obsługiwane równoczesnych wyrzucania elementów bezużytecznych, który wykonywane wyrzucania elementów bezużytecznych w tle w oddzielnym wątku. W programie .NET Framework 4 równoczesnych wyrzucania elementów bezużytecznych został zastąpiony przez gc tła, który wykonuje również wyrzucania elementów bezużytecznych w tle w oddzielnym wątku. Począwszy od programu .NET Framework 4.5, zbieranie w tle stało się dostępne w wyrzucaniu elementów bezużytecznych serwera. **GcConcurrent** element kontroluje, czy środowisko wykonawcze wykonuje równoczesnych lub w tle wyrzucania elementów bezużytecznych, jeśli jest dostępny lub czy wykonuje wyrzucania elementów bezużytecznych na pierwszym planie.

### <a name="to-disable-background-garbage-collection"></a>Aby wyłączyć wyrzucanie elementów bezużytecznych w tle

> [!WARNING]
> Począwszy od programu .NET Framework 4, równoczesnych wyrzucania elementów bezużytecznych jest zastępowany przez wyrzucanie elementów bezużytecznych w tle. Terminy *równoczesnych* i *tła* są używane zamiennie w dokumentacji programu .NET Framework. Aby wyłączyć wyrzucanie elementów bezużytecznych w tle, należy użyć **gcConcurrent** element, jak omówiono w tym artykule.

Domyślnie środowisko wykonawcze używa równoczesnych lub w tle wyrzucania elementów bezużytecznych, który jest zoptymalizowany pod kątem opóźnienia. Jeśli aplikacja obejmuje intensywnej interakcji użytkownika, pozostawić równoczesnych wyrzucania elementów bezużytecznych włączone, aby zminimalizować czas wstrzymania aplikacji do wykonywania wyrzucania elementów bezużytecznych. Jeśli ustawisz `enabled` atrybut **gcConcurrent** element `false`do , środowisko wykonawcze używa niebieżne wyrzucania elementów bezużytecznych, który jest zoptymalizowany pod kątem przepływności.

Następujący plik konfiguracyjny wyłącza wyrzucanie elementów bezużytecznych w tle:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

Jeśli w pliku konfiguracji komputera znajduje się ustawienie **gcConcurrentSetting,** definiuje wartość domyślną dla wszystkich aplikacji .NET Framework. Ustawienie pliku konfiguracji komputera zastępuje ustawienie pliku konfiguracji aplikacji.

Aby uzyskać więcej informacji na temat równoczesnych i tła wyrzucania elementów bezużytecznych, zobacz [równoczesnych wyrzucania elementów](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) [bezużytecznych, Tło wyrzucania elementów bezużytecznych stacji roboczej](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)i [części wyrzucania elementów bezużytecznych serwera w](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sekcji Podstawy [wyrzucania elementów bezużytecznych](../../../../standard/garbage-collection/fundamentals.md) artykułu.

## <a name="example"></a>Przykład

Poniższy przykład umożliwia wyrzucanie elementów bezużytecznych w tle:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Podstawy dotyczące odzyskiwania pamięci](../../../../standard/garbage-collection/fundamentals.md)
