---
title: EmitManifest — Metoda
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 051b5f47db05301f3a3326a2cc4cc5cf5c8b1ec2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137829"
---
# <a name="emitmanifest-method"></a>EmitManifest — Metoda
Emituje końcowego manifestu. Po zaimportowaniu wszystkich innych plików i ustawieniu wszystkich opcji, należy wywołać tę metodę. Nie wywołuj tej metody dla modułów niepowiązanej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu.  
  
 `pdwReserveSize`  
 Odbiera rozmiar do zarezerwowania w pliku zestawu pobierane [strongnamesignaturesize — funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).  
  
 `ptkManifest`  
 Opcjonalnie odbiera token manifestu zestawu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h.  
  
## <a name="see-also"></a>Zobacz także

- [IALink — Interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 — Interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink — interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
