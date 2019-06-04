---
title: <UseSmallInternalThreadStacks>, element
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70113d98c5a4ab41700f6c9842dba89e2b49c297
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489331"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks> Element
Użyj żądania, że środowisko uruchomieniowe języka wspólnego (CLR), zmniejszyć pamięci, określając stosu jawnych rozmiarów, podczas tworzenia niektórych wątków, które używa wewnętrznie, zamiast korzystać z domyślnego rozmiaru stosu dla tych wątków.  
  
 \<Konfiguracja > Element  
\<środowisko uruchomieniowe > Element  
\<UseSmallInternalThreadStacks> Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Włączone|Atrybut wymagany.<br /><br /> Określa, czy żądanie rozmiary CLR Użyj jawnego stosu zamiast domyślnego rozmiaru stosu podczas tworzenia niektórych wątków, które używa wewnętrznie. Rozmiary jawne stosu są mniejsze niż domyślny rozmiar stosu 1 MB.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Żądanie stosu jawnych rozmiarów.|  
|false|Użyj domyślnego rozmiaru stosu. Jest to wartość domyślna dla programu .NET Framework 4.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji służy do żądania użyj ograniczoną ilość pamięci wirtualnej w procesie, ponieważ rozmiary jawne wątków, które środowisko CLR używa wewnętrznego wątków, jeśli żądanie zostanie uznane, są mniejsze niż domyślny rozmiar.  
  
> [!IMPORTANT]
>  Ten element konfiguracji to żądanie do środowiska CLR zamiast bezwzględnie. W programie .NET Framework 4, żądanie zostanie uznane tylko w przypadku x86 architektury. Ten element może być całkowicie ignorowane w przyszłych wersjach środowiska CLR lub zastępuje rozmiary jawne stosu, które są zawsze używane dla wybranych wątków wewnętrznego.  
  
 Określanie, czy ten element konfiguracji zamienia niezawodność mniejsze użycie pamięci wirtualnej, jeśli środowisko CLR honoruje żądania, ponieważ mniejsze rozmiary stos może sprawić stosu najprawdopodobniej przepełnienia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak żądanie stosu jawnego użycia CLR rozmiarów dla niektórych wątków, które używa wewnętrznie.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
