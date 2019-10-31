---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 274bf79175bda9e880b1ef3cf8f125a017ad0734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121662"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>ISymUnmanagedWriter4::GetDebugInfoWithPadding — Metoda
Działa tak samo jak [Metoda GetDebugInfo —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , z tą różnicą, że ciąg ścieżki jest dopełniany zerami po zamykającym znaku null, aby dane ciągu miały stały rozmiar `MAX_PATH`. Uzupełnienie jest nadawane tylko wtedy, gdy sama długość ciągu ścieżki jest mniejsza niż `MAX_PATH`.  
  
 Ułatwia to pisanie narzędzi, które różnicuje pliki PE.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter4, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
