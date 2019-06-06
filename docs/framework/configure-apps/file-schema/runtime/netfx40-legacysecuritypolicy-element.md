---
title: <NetFx40_LegacySecurityPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5bfa5449ece1b24d4f47fe3e77e36b26bbe430c
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689843"
---
# <a name="netfx40legacysecuritypolicy-element"></a>\<NetFx40_LegacySecurityPolicy> Element

Określa, czy środowisko wykonawcze używa starszego kodu zasady zabezpieczeń dostępu (CAS).

\<Konfiguracja > \
\<runtime>\
\<NetFx40_LegacySecurityPolicy>

## <a name="syntax"></a>Składnia

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko wykonawcze używa starsza zasada CAS.|

## <a name="enabled-attribute"></a>Atrybut włączony

|Wartość|Opis|
|-----------|-----------------|
|`false`|Środowisko wykonawcze nie używa starsza zasada CAS. Domyślnie włączone.|
|`true`|Środowisko wykonawcze używa starsza zasada CAS.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|

## <a name="remarks"></a>Uwagi

W .NET Framework w wersji 3.5 i wcześniejszymi wersjami urzędy certyfikacji zasad jest zawsze w obiekcie. W programie .NET Framework 4 można włączyć zasady CAS.

Urzędy certyfikacji zasad jest specyficzny dla wersji. Zasady niestandardowe urzędów certyfikacji, które istnieją we wcześniejszych wersjach programu .NET Framework musi obowiązywać w programie .NET Framework 4.

Stosowanie `<NetFx40_LegacySecurityPolicy>` element do zestawu .NET Framework 4 nie wpływa na [kod o przezroczystym poziomie bezpieczeństwa](../../../../../docs/framework/misc/security-transparent-code.md); nadal mają zastosowanie zasady przejrzystości.

> [!IMPORTANT]
> Stosowanie `<NetFx40_LegacySecurityPolicy>` elementu może spowodować istotnie poprawiającą wydajność dla zestawów obrazu natywnego, utworzone przez [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) nie są zainstalowane w [globalnej pamięci podręcznej zestawów ](../../../../../docs/framework/app-domains/gac.md). Spadek wydajności jest spowodowany brakiem możliwości środowiska uruchomieniowego ładować zestawy jako obrazy natywne, jeśli ten atrybut jest stosowany, co spowoduje ich załadowanych zespołów jako just-in-time.

> [!NOTE]
> Jeśli określisz docelowego .NET Framework w wersji starszej niż .NET Framework 4 w ustawieniach projektu dla projektu programu Visual Studio, urzędów certyfikacji, zasady zostaną włączone, w tym wszystkie niestandardowe zasady urzędów certyfikacji, wskazana dla danej wersji. Jednak nie można używać nowych typów programu .NET Framework 4 i elementów członkowskich. Można również określić przy użyciu wcześniejszej wersji programu .NET Framework [ \<supportedRuntime > element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) w schemat ustawień uruchamiania w swojej [pliku konfiguracji aplikacji](../../../../../docs/framework/configure-apps/index.md).

> [!NOTE]
> Składni plików konfiguracji jest uwzględniana wielkość liter. Należy użyć składni, zgodnie z postanowieniami w sekcjach składnię i przykład.

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób Włącz starszą zasadę dla aplikacji.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
