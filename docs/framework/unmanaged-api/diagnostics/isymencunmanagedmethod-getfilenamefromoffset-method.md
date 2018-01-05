---
title: "ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f4b760f2782cf75cf0ab0879eb77e185a93b8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a>ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda
Pobiera nazwę pliku dla wiersz skojarzony z przesunięciem.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwOffset`  
 [in] A `ULONG32` zawiera przesunięcie.  
  
 `cchName`  
 [in] A `ULONG32` wskazuje, że rozmiar `szName` buforu.  
  
 `pcchName`  
 [out] Wskaźnik do `ULONG32` rozmiaru, który odbiera w znaki buforu, muszą zawierać nazw plików.  
  
 `szName`  
 [out] Buforu, który zawiera nazwy pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymENCUnmanagedMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
