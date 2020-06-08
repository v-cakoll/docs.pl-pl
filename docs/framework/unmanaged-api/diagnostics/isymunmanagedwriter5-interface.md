---
title: ISymUnmanagedWriter5 — Interfejs
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: d9204457b71b670e1c96ed228ad11116bdf41fe6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493581"
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
|[CloseMapTokensToSourceSpans, metoda](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Zamknij sekcję specjalnych danych niestandardowych dla informacji dotyczących mapowania między tokenami i źródłami. Po jego zamknięciu nie można dodać więcej informacji dotyczących mapowania.|  
|[MapTokenToSourceSpan, metoda](isymunmanagedwriter5-maptokentosourcespan-method.md)|Mapuje podany token metadanych do podanego zakresu wierszy źródłowych w określonym pliku źródłowym.<br /><br /> Musi być wywoływana między wywołaniami [metody OpenMapTokensToSourceSpans —](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) i [CloseMapTokensToSourceSpans —](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[OpenMapTokensToSourceSpans, metoda](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Otwórz specjalną sekcję z danymi niestandardowymi, aby emitować informacje o mapowaniu między tokenami i źródłami do programu. Otwarcie tej sekcji, gdy metoda jest już otwarta lub na odwrót, jest błędem.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 — Interfejs](isymunmanagedwriter4-interface.md)
