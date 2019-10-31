---
title: ISymUnmanagedWriter5 — Interfejs
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 18371b6aefb002f5adf27d43f85194c6c35f6ef5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121640"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 — Interfejs
Interfejs ISymUnmanagedWriter5.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs zawiera następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Zamknij sekcję specjalnych danych niestandardowych dla informacji dotyczących mapowania między tokenami i źródłami. Po jego zamknięciu nie można dodać więcej informacji dotyczących mapowania.|  
|[MapTokenToSourceSpan, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|Mapuje podany token metadanych do podanego zakresu wierszy źródłowych w określonym pliku źródłowym.<br /><br /> Musi być wywoływana między wywołaniami [metody OpenMapTokensToSourceSpans —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[OpenMapTokensToSourceSpans, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Otwórz specjalną sekcję z danymi niestandardowymi, aby emitować informacje o mapowaniu między tokenami i źródłami do programu. Otwarcie tej sekcji, gdy metoda jest już otwarta lub na odwrót, jest błędem.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
