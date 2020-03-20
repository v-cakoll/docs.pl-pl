---
title: <gcAllowVeryLargeObjects>, element
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154130"
---
# <a name="gcallowverylargeobjects-element"></a>\<gcAllowVeryLargeObjects> Element
Na platformach 64-bitowych włącza macierze o całkowitym rozmiarze większym niż 2 gigabajty (GB).  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy tablice o całkowitym rozmiarze większym niż 2 GB są włączone na platformach 64-bitowych.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Tablice o całkowitym rozmiarze większe niż 2 GB nie są włączone. Domyślnie włączone.|  
|`true`|Macierze o całkowitym rozmiarze większej niż 2 GB są włączone na platformach 64-bitowych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Użycie tego elementu w pliku konfiguracji aplikacji umożliwia tablice o rozmiarze większym niż 2 GB, ale nie zmienia innych limitów rozmiaru obiektu lub rozmiaru tablicy:  
  
- Maksymalna liczba elementów w <xref:System.UInt32.MaxValue?displayProperty=nameWithType>tablicy to .  
  
- Maksymalny indeks w dowolnym pojedynczym wymiarze wynosi 2 147 483 591 (0x7FFFFFC7) dla tablic bajtowych i tablic struktur jedno bajtowych oraz 2 146 435 071 (0X7FEFFFFF) dla innych typów.  
  
- Maksymalny rozmiar ciągów i innych obiektów innych niż tablica pozostaje niezmieniony.  
  
> [!CAUTION]
> Przed włączeniem tej funkcji upewnij się, że aplikacja nie zawiera niebezpieczny kod, który zakłada, że wszystkie tablice są mniejsze niż 2 GB w rozmiarze. Na przykład niebezpieczny kod, który używa tablic jako buforów może być podatny na przekroczenia buforu, jeśli jest napisane przy założeniu, że tablice nie przekroczy 2 GB.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak włączyć tę funkcję dla aplikacji.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a>Obsługiwane w

.NET Framework 4.5 i nowsze wersje

## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
