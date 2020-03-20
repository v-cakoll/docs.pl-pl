---
title: CustomDumpItem — Struktura
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 154beef9398029f31dcb4d081019b9f292238af4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176477"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem — Struktura
Opisuje element, który ma zostać dodany do zrzutu niestandardowego w raportowaniu błędów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`itemKind`|[Wartość ECustomDumpItemKind,](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) która wskazuje rodzaj elementu do dodania.|  
|`pReserved`|Nie jest obecnie używany. Wszystkie elementy dodane do unii nie może być większy niż rozmiar wskaźnika. Jeśli `struct` a jest wymagane, należy przydzielić go oddzielnie i wskazać go.|  
  
## <a name="remarks"></a>Uwagi  
 [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) przyjmuje parametr `CustomDumpItem`typu .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** mscoree.idl  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
