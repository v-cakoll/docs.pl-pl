---
title: ISymUnmanagedWriter5 — Interfejs
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5fd7c2bd4fae94d1ef5021b558a04b734803b68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430560"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 — Interfejs
Isymunmanagedwriter5 — interfejs.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs zawiera następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Zamknij sekcji specjalne dane niestandardowe dla tokenu do źródła obejmuje informacje dotyczące mapowania. Po zamknięciu, można dodać nie więcej informacji o mapowaniu.|  
|[MapTokenToSourceSpan, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|Map zakres token metadanych do wiersza danego źródłowego określony plik źródłowy.<br /><br /> Musi zostać wywołana między wywołań [OpenMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[OpenMapTokensToSourceSpans, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Otwórz sekcję specjalne danych niestandardowych można wyemitować informacji mapowaniem token do źródła do. Otwieranie w tej sekcji, gdy metoda jest już otwarty lub odwrotnie, jest to błąd.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter4, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
