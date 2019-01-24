---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15f85a6f5ab418692d747cc9ad415c637d7b96e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614370"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a>ISymUnmanagedSymbolSearchInfo::GetHRESULT — Metoda
Pobiera wartość HRESULT.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phr`  
 [out] Wskaźnik do HRESULT.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedSymbolSearchInfo, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
