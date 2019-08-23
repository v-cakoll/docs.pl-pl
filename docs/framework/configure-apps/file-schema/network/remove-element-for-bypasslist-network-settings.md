---
title: <remove>, element dla bypasslist (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 99c18bd5b779845d52831b4a9591eaf4d5e5530b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920965"
---
# <a name="remove-element-for-bypasslist-network-settings"></a>\<Usuń element > dla BypassList (Ustawienia sieci)

Usuwa adres IP lub nazwę DNS z listy obejścia serwera proxy.

\<> konfiguracji \
\<system.net>\
\<defaultProxy>\
\<BypassList > \
\<remove>

## <a name="syntax"></a>Składnia

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|**Atrybut**|**Opis**|
|-------------------|---------------------|
|`address`|Wyrażenie regularne opisujące adres IP lub nazwę DNS.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|**Element**|**Opis**|
|-----------------|---------------------|
|[bypasslist](bypasslist-element-network-settings.md)|Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.|

## <a name="remarks"></a>Uwagi

`remove` Element usuwa wyrażenia regularne opisujące adresy IP lub nazwy serwerów DNS z listy adresów, które pomijają serwer proxy. Adresy zostały zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.

Wartość `address` atrybutu powinna być wyrażeniem regularnym opisującym zestaw adresów IP lub nazw hostów.

Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../standard/base-types/regular-expressions.md).

## <a name="configuration-files"></a>Pliki konfiguracji

Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).

## <a name="example"></a>Przykład

Poniższy przykład usuwa wszystkie poprzednie definicje domeny adventure-works.com, a następnie dodaje domenę contoso.com do listy pomijania.

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
