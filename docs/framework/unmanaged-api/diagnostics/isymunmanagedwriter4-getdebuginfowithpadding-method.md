---
title: "ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9f2f0aad37fcd63e2345cd32a00b44412ed8c7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda
Działa tak samo, jak [GetDebugInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) z tą różnicą, że ciąg ścieżki jest uzupełniana zerami po znak końcowy null, aby udostępnić dane ciąg stały rozmiar `MAX_PATH`. Dopełnienie tylko otrzyma, jeśli długość ciągu ścieżki sam jest mniejsza niż `MAX_PATH`.  
  
 Ułatwia to zapisać narzędzia pliki tej różnicy PE.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Isymunmanagedwriter4 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
