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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29990ad6a94f063577236bdbc84d02d4d2b4b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426136"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset — Metoda
Pobiera informacje o wiersz skojarzony z przesunięciem. Jeśli parametr offset (`dwOffset`) nie jest punktu sekwencji, ta metoda pobiera informacje o wiersz skojarzony z poprzednich przesunięcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwOffset`  
 [in] A `ULONG32` zawiera przesunięcie.  
  
 `pline`  
 [out] Wskaźnik do `ULONG32` odbierająca wiersza.  
  
 `pcolumn`  
 [out] Wskaźnik do `ULONG32` odbierająca kolumny.  
  
 `pendLine`  
 [out] Wskaźnik do `ULONG32` odbierająca zakończyć wiersza.  
  
 `pendColumn`  
 [out] Wskaźnik do `ULONG32` odbierająca końcowa kolumny.  
  
 `pdwStartOffset`  
 [out] Wskaźnik do `ULONG32` odbierająca punktu skojarzone sekwencji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymENCUnmanagedMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
