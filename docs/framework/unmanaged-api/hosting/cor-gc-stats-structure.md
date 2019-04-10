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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d335a62545f06a66d4044b59aa9499d3f7ede515
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208478"
---
# <a name="corgcstats-structure"></a>COR_GC_STATS — Struktura
Przedstawia dane statystyczne dotyczące mechanizmu kolekcji wyrzucania elementów środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`Flags`|Wskazuje wartości pola, które powinny być obliczany i zwracany.|  
|`ExplicitGCCount`|Wskazuje liczbę wyrzucania elementów bezużytecznych, które zostały zmuszeni przez zewnętrzne żądanie.|  
|`GenCollectionsTaken`|Wskazuje liczbę wyrzucania elementów bezużytecznych wykonywane dla każdej generacji.|  
|`CommittedKBytes`|Całkowita liczba kilobajtów zatwierdzone we wszystkich stertach.|  
|`ReservedKBytes`|Całkowita liczba kilobajtów zastrzeżone we wszystkich stertach.|  
|`Gen0HeapSizeKBytes`|Rozmiar w kilobajtach sterty generowania od zera.|  
|`Gen1HeapSizeKBytes`|Rozmiar w kilobajtach sterty jeden generacji.|  
|`Gen2HeapSizeKBytes`|Rozmiar w kilobajtach sterty pokolenia 2.|  
|`LargeObjectHeapSizeKBytes`|Rozmiar w kilobajtach stertę dużego obiektu.|  
|`KBytesPromotedFromGen0`|Rozmiar w kilobajtach obiektów promowane z generacji 0 do generowania jednego.|  
|`KBytesPromotedFromGen1`|Rozmiar w kilobajtach obiektów promowane z generowania jeden generacji dwa.|  
  
## <a name="remarks"></a>Uwagi  
 [Iclrgcmanager::getstats —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metoda wymaga `Flags` pole `COR_GC_STATS` struktury, należy ustawić jedną lub więcej wartości [cor_gc_stat_types —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wyliczeniu, aby określić, które statystyki mają być tworzone.  
  
 Poniższa tabela zawiera mapowanie dostarczonych przez tę strukturę do dwóch statystyk [cor_gc_stat_types —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wartości wyliczenia `COR_GC_COUNTS` i `COR_GC_MEMORYUSAGE`.  
  
|Określony przez COR_GC_COUNTS|Określony przez COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Przykład użycia jest następująca:  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — Struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Automatyczne zarządzanie pamięcią](../../../../docs/standard/automatic-memory-management.md)
- [Odzyskiwanie pamięci](../../../../docs/standard/garbage-collection/index.md)
