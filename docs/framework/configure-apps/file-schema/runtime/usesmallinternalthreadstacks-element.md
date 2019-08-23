---
title: <UseSmallInternalThreadStacks>, element
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ee4df12a017429de333dd4e93df27973b658dad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920679"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks, element >
Żądania, które zmniejszają użycie pamięci przez środowisko uruchomieniowe języka wspólnego (CLR) przez określenie jawnych rozmiarów stosu podczas tworzenia niektórych wątków, które używają wewnętrznie, zamiast używania domyślnego rozmiaru stosu dla tych wątków.  
  
 \<> elementu konfiguracji  
\<Element > środowiska uruchomieniowego  
\<UseSmallInternalThreadStacks, element >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|dostępny|Atrybut wymagany.<br /><br /> Określa, czy należy zażądać, aby środowisko CLR używało jawnych rozmiarów stosu zamiast domyślnego rozmiaru stosu, gdy tworzy pewne wątki używane wewnętrznie. Jawne rozmiary stosu są mniejsze niż domyślny rozmiar stosu wynoszący 1 MB.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Żądaj jawnych rozmiarów stosu.|  
|false|Użyj domyślnego rozmiaru stosu. Jest to wartość domyślna dla .NET Framework 4.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji jest używany do żądania zredukowania użycia pamięci wirtualnej w procesie, ponieważ jawne rozmiary wątków używane przez środowisko CLR dla wewnętrznych wątków, jeśli żądanie jest honorowane, są mniejsze niż rozmiar domyślny.  
  
> [!IMPORTANT]
> Ten element konfiguracji jest żądaniem do środowiska CLR, a nie bezwzględnym wymaganiem. W .NET Framework 4 żądanie jest uznawane za tylko dla architektury x86. Ten element może zostać całkowicie zignorowany w przyszłych wersjach środowiska CLR lub zastąpiony przez jawne rozmiary stosu, które są zawsze używane dla wybranych wewnętrznych wątków.  
  
 Określenie tego elementu konfiguracji zapewnia niezawodność dla mniejszej ilości pamięci wirtualnej, jeśli środowisko CLR honoruje żądanie, ponieważ mniejsze rozmiary stosu mogą potencjalnie spowodować przepełnienie stosu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zażądać, aby środowisko CLR używało jawnych rozmiarów stosu dla niektórych wątków używanych wewnętrznie.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
