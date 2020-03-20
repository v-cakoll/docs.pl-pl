---
title: COR_GC_STATS — Struktura
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176529"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS — Struktura
Zawiera statystyki dotyczące mechanizmu wyrzucania elementów bezużytecznych środowiska wykonawczego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`Flags`|Wskazuje, które wartości pól powinny być obliczane i zwracane.|  
|`ExplicitGCCount`|Wskazuje liczbę wyrzucanych elementów bezużytecznych, które zostały wymuszone przez żądanie zewnętrzne.|  
|`GenCollectionsTaken`|Wskazuje liczbę wyrzucanych elementów bezużytecznych wykonanych dla każdej generacji.|  
|`CommittedKBytes`|Całkowita liczba kilobajtów popełnionych we wszystkich stertach.|  
|`ReservedKBytes`|Całkowita liczba kilobajtów zarezerwowanych na wszystkich stertach.|  
|`Gen0HeapSizeKBytes`|Rozmiar w kilobajtach sterty zerowej generacji.|  
|`Gen1HeapSizeKBytes`|Rozmiar w kilobajtach sterty generacji.|  
|`Gen2HeapSizeKBytes`|Rozmiar w kilobajtach sterty generacji two.|  
|`LargeObjectHeapSizeKBytes`|Rozmiar ( kilobajtów) sterty dużego obiektu.|  
|`KBytesPromotedFromGen0`|Rozmiar w kilobajtach obiektów promowanych od generacji od zera do generacji.|  
|`KBytesPromotedFromGen1`|Rozmiar w kilobajtach obiektów promowanych od pierwszej do drugiej generacji.|  
  
## <a name="remarks"></a>Uwagi  
 [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) Metoda wymaga `Flags` pola `COR_GC_STATS` struktury, które mają być ustawione na jedną lub więcej wartości [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wyliczenia, aby określić, które statystyki mają być ustawione.  
  
 W poniższej tabeli przedstawiono statystyki dostarczone przez tę strukturę na `COR_GC_COUNTS` dwie `COR_GC_MEMORYUSAGE` [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wartości wyliczenia i .  
  
|Określony przez COR_GC_COUNTS|Określony przez COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Przykład użycia jest następujący:  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Automatyczne zarządzanie pamięcią](../../../standard/automatic-memory-management.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
