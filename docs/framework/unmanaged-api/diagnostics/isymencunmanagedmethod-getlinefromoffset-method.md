---
title: "ISymENCUnmanagedMethod::GetLineFromOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetLineFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f18357b3a58a5409da93d4d2491997e9ca1cc70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymENCUnmanagedMethod — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
