---
title: <NetFx40_LegacySecurityPolicy>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: d5192eb56bb8b640544bdc52a0bb9d8a5277efef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116252"
---
# <a name="netfx40_legacysecuritypolicy-element"></a>\<NetFx40_LegacySecurityPolicy> Element

Określa, czy środowisko uruchomieniowe korzysta ze starszych zasad zabezpieczeń dostępu kodu (CAS).

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**  

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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe używa starszych zasad CAS.|

## <a name="enabled-attribute"></a>Atrybut włączony

|Wartość|Opis|
|-----------|-----------------|
|`false`|Środowisko uruchomieniowe nie używa starszych zasad CAS. Domyślnie włączone.|
|`true`|Środowisko uruchomieniowe używa starszych zasad CAS.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|

## <a name="remarks"></a>Uwagi

W .NET Framework wersja 3,5 i wcześniejsze wersje zasady CAS są zawsze włączone. W .NET Framework 4 należy włączyć zasady CAS.

Zasady CAS są specyficzne dla wersji. Zasady niestandardowych urzędów certyfikacji, które istnieją we wcześniejszych wersjach .NET Framework muszą zostać określone w .NET Framework 4.

Zastosowanie `<NetFx40_LegacySecurityPolicy>` elementu do zestawu .NET Framework 4 nie wpływa na [kod przezroczysty dla bezpieczeństwa](../../../misc/security-transparent-code.md); nadal obowiązują reguły przezroczystości.

> [!IMPORTANT]
> Zastosowanie `<NetFx40_LegacySecurityPolicy>` elementu może spowodować znaczny wpływ na wydajność zestawów obrazów natywnych utworzonych przez [Generator obrazu natywnego (Ngen. exe)](../../../tools/ngen-exe-native-image-generator.md) , które nie są zainstalowane w [globalnej pamięci podręcznej zestawów](../../../app-domains/gac.md). Spadek wydajności jest spowodowany przez niezdolność środowiska uruchomieniowego do załadowania zestawów jako obrazów natywnych podczas stosowania atrybutu, co spowoduje ich załadowanie jako zestawów just in Time.

> [!NOTE]
> Jeśli określisz wersję docelową .NET Framework, która jest wcześniejsza niż .NET Framework 4 w ustawieniach projektu dla projektu programu Visual Studio, zostaną włączone zasady CAS, w tym wszelkie niestandardowe zasady dotyczące urzędów certyfikacji określone dla tej wersji. Nie będzie jednak można używać nowych typów i elementów członkowskich .NET Framework 4. Możesz również określić wcześniejszą wersję .NET Framework za pomocą [ \<supportedRuntime> elementu](../startup/supportedruntime-element.md) w schemacie ustawienia uruchamiania w [pliku konfiguracyjnym aplikacji](../../index.md).

> [!NOTE]
> W składni pliku konfiguracji jest rozróżniana wielkość liter. Należy użyć składni podanej w sekcjach składnia i przykład.

## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można używać tylko w pliku konfiguracji aplikacji.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak włączyć zasady starszych urzędów certyfikacji dla aplikacji.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
