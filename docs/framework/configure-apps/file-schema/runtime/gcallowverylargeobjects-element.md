---
title: '&lt;gcAllowVeryLargeObjects&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16a6b497136b6cffabeb4151e54bec8d80928b5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549122"
---
# <a name="ltgcallowverylargeobjectsgt-element"></a>&lt;gcAllowVeryLargeObjects&gt; — Element
Na platformach 64-bitowych umożliwia tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.  
  
 \<Konfiguracja > Element  
\<środowisko uruchomieniowe > Element  
\<gcAllowVeryLargeObjects> Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy tablic, które są większe niż 2 GB w łącznym rozmiarze są włączone na platformach 64-bitowych.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Większa niż 2 GB łącznego rozmiaru tablic nie są włączone. Domyślnie włączone.|  
|`true`|Tablic większych niż 2 GB w łącznym rozmiarze są włączone na platformach 64-bitowych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Przy użyciu tego elementu w pliku konfiguracyjnym aplikacji umożliwia tablic, które są większe niż 2 GB, rozmiar, ale nie zmienia się inne ograniczenia dotyczące rozmiaru obiektu lub rozmiar tablicy:  
  
-   Maksymalna liczba elementów w tablicy to <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.  
  
-   Maksymalna wartość indeksu w dowolnym jeden wymiar jest 2,147,483,591 (0x7FFFFFC7) dla tablic bajtów i tablic struktur jednobajtowe i 2,146,435,071 (0X7FEFFFFF) w przypadku innych typów.  
  
-   Maksymalny rozmiar dla ciągów i innych obiektów inny niż tablica jest bez zmian.  
  
> [!CAUTION]
>  Przed włączeniem tej funkcji, upewnij się, czy aplikacja nie zawiera niebezpieczny kod, który przyjęto założenie, że wszystkie tablice są mniejsze niż rozmiar 2 GB. Na przykład niebezpieczny kod, który używa tablic jako buforów może być podatny na przepełnienia buforu, zostanie zapisany na założeniu, że tablice nie przekroczy 2 GB.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak włączyć tę funkcję dla aplikacji.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
