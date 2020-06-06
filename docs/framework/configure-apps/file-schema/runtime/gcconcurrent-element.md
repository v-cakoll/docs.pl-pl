---
title: gcConcurrent, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102921"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent>, element

Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia odzyskiwanie pamięci w osobnym wątku.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

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
|`enabled`|Atrybut wymagany.<br /><br />Określa, czy środowisko uruchomieniowe uruchamia odzyskiwanie pamięci jednocześnie.|

#### <a name="enabled-attribute"></a>włączony atrybut

|Wartość|Opis|
|-----------|-----------------|
|`false`|Nie uruchamia współbieżnego wyrzucania elementów bezużytecznych.|
|`true`|Uruchamia odzyskiwanie pamięci jednocześnie. Domyślnie włączone.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|

## <a name="remarks"></a>Uwagi

Przed .NET Framework 4, wyrzucanie elementów bezużytecznych stacji roboczych obsługiwało współbieżne wyrzucanie elementów bezużytecznych, które przeprowadzono odzyskiwanie pamięci w tle w osobnym wątku. W .NET Framework 4 współbieżne wyrzucanie elementów bezużytecznych zostało zastąpione przez w tle GC, co również wykonuje odzyskiwanie pamięci w tle w osobnym wątku. Począwszy od .NET Framework 4,5, zbieranie w tle stało się dostępne w wyrzucaniu elementów bezużytecznych serwera. Element **gcConcurrent** określa, czy środowisko uruchomieniowe wykonuje współbieżne lub w tle odzyskiwanie pamięci, jeśli jest dostępne, lub czy wykonuje odzyskiwanie pamięci na pierwszym planie.

### <a name="to-disable-background-garbage-collection"></a>Aby wyłączyć wyrzucanie elementów bezużytecznych w tle

> [!WARNING]
> Począwszy od .NET Framework 4, współbieżne wyrzucanie elementów bezużytecznych jest zastępowane przez odzyskiwanie pamięci w tle. Terminy *współbieżne* i *tła* są używane zamiennie w dokumentacji .NET Framework. Aby wyłączyć wyrzucanie elementów bezużytecznych w tle, należy użyć elementu **gcConcurrent** , zgodnie z opisem w tym artykule.

Domyślnie środowisko uruchomieniowe używa współbieżnych lub w tle wyrzucania elementów bezużytecznych, które jest zoptymalizowane pod kątem opóźnień. Jeśli aplikacja wymaga dużej interakcji z użytkownikiem, Włącz współbieżne wyrzucanie elementów bezużytecznych, aby zminimalizować czas wstrzymania aplikacji w celu wykonania odzyskiwania pamięci. Jeśli ustawisz `enabled` atrybut elementu **gcConcurrent** na `false` , środowisko uruchomieniowe używa niewspółbieżnego wyrzucania elementów bezużytecznych, które jest zoptymalizowane pod kątem przepływności.

Następujący plik konfiguracji wyłącza wyrzucanie elementów bezużytecznych w tle:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

Jeśli istnieje ustawienie **gcConcurrentSetting** w pliku konfiguracji komputera, definiuje wartość domyślną dla wszystkich aplikacji .NET Framework. Ustawienie pliku konfiguracji komputera zastępuje ustawienie pliku konfiguracji aplikacji.

Aby uzyskać więcej informacji na temat współbieżnych i wyrzucania elementów bezużytecznych, zobacz [odzyskiwanie pamięci w tle](../../../../standard/garbage-collection/background-gc.md).

## <a name="example"></a>Przykład

Poniższy przykład włącza wyrzucanie elementów bezużytecznych w tle:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Podstawy dotyczące odzyskiwania pamięci](../../../../standard/garbage-collection/fundamentals.md)
