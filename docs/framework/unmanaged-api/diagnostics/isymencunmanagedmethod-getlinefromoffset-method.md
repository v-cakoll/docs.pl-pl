---
title: ISymENCUnmanagedMethod::GetLineFromOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 94a571a4bc01b805387aebe5a6e23bad0b735313
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448640"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset — Metoda
Pobiera informacje o wierszu skojarzone z przesunięciem. Jeśli parametr przesunięcia (`dwOffset`) nie jest punktem sekwencji, ta metoda pobiera informacje o wierszu skojarzone z poprzednim przesunięcia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwOffset`  
 podczas `ULONG32`, który zawiera przesunięcie.  
  
 `pline`  
 określoną Wskaźnik do `ULONG32`, który odbiera wiersz.  
  
 `pcolumn`  
 określoną Wskaźnik do `ULONG32`, który odbiera kolumnę.  
  
 `pendLine`  
 określoną Wskaźnik do `ULONG32`, który odbiera linię końcową.  
  
 `pendColumn`  
 określoną Wskaźnik do `ULONG32`, który odbiera kolumnę końcową.  
  
 `pdwStartOffset`  
 określoną Wskaźnik do `ULONG32`, który odbiera skojarzony punkt sekwencji.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymENCUnmanagedMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
