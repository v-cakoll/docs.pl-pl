---
title: '&lt;gcallowverylargeobjects —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 750b0dbc925ec484dd80e1796ba991435e354709
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltgcallowverylargeobjectsgt-element"></a>&lt;gcallowverylargeobjects —&gt; — Element
Na platformach 64-bitowych umożliwia tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.  
  
 \<Konfiguracja > — Element  
\<środowisko uruchomieniowe > — Element  
\<gcallowverylargeobjects — > — Element  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy włączono tablic, które są większe niż 2 GB rozmiar całkowitą na platformach 64-bitowych.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Tablice większe niż 2 GB w łącznym rozmiarze nie są włączone. Domyślnie włączone.|  
|`true`|Tablice większe niż 2 GB w łącznym rozmiarze są włączone na platformach 64-bitowych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą tego elementu w pliku konfiguracyjnym aplikacji umożliwia tablic, które są większe niż 2 GB, rozmiar, ale nie powoduje zmiany innych limity rozmiaru obiektu lub rozmiar tablicy:  
  
-   Maksymalna liczba elementów w tablicy jest <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.  
  
-   Maksymalna wartość indeksu w dowolnym pojedynczy wymiarze jest 2,147,483,591 (0x7FFFFFC7) dla tablic bajtowych i tablice struktur jednobajtowe i 2,146,435,071 (0X7FEFFFFF) dla innych typów.  
  
-   Maksymalny rozmiar ciągów i innych obiektów z systemem innym niż tablica jest bez zmian.  
  
> [!CAUTION]
>  Przed włączeniem tej funkcji, upewnij się, aplikacja nie ma niebezpieczny kod, który założono, że wszystkie tablice jest mniejszy niż rozmiar 2 GB. Na przykład niebezpieczny kod, który korzysta z tablic jako buforów może być narażony na przepełnienia buforu zostanie zapisany na założeniu, że tablice nie przekroczy 2 GB.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób włączyć tę funkcję dla aplikacji.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
