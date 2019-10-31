---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 004e1ddae8a6c0262846422a2eeb4314a4c82f65
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121614"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a>ISymUnmanagedWriter5::OpenMapTokensToSourceSpans — Metoda
Otwórz specjalną sekcję z danymi niestandardowymi, aby emitować informacje o mapowaniu między tokenami i źródłami do programu. Otwarcie tej sekcji, gdy metoda jest już otwarta lub na odwrót, jest błędem.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter5, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
