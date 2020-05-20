---
title: ISymUnmanagedWriter4 — Interfejs
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: eaf2e8e60d9812ab6a31fb3b9050cbaae0f1a9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609472"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 — Interfejs
Interfejs ISymUnmanagedWriter4.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs zawiera następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDebugInfoWithPadding, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Działa tak samo jak [Metoda GetDebugInfo —](isymunmanagedwriter-getdebuginfo-method.md) , z tą różnicą, że ciąg ścieżki jest dopełniany zerami po zamykającym znaku null, aby dane ciągu miały stały rozmiar `MAX_PATH` . Uzupełnienie jest udzielane tylko wtedy, gdy sama długość ciągu ścieżki jest mniejsza niż `MAX_PATH` .<br /><br /> Ułatwia to pisanie narzędzi, które różnicuje pliki PE.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3 — Interfejs](isymunmanagedwriter3-interface.md)
