---
title: ISymUnmanagedSourceServerModule::GetSourceServerData — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea8052152b08732906c707648f361bba4d83a276
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173579"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a>ISymUnmanagedSourceServerModule::GetSourceServerData — Metoda
Zwraca dane serwera źródłowego dla modułu. Obiekt wywołujący musi zwolnić zasoby przy użyciu `CoTaskMemFree`.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDataByteCount`  
 [out] Wskaźnik do `ULONG32` odbierająca rozmiar w bajtach, danych serwera źródłowego.  
  
 `ppData`  
 [out] Wskaźnik do zwracanego `pDataByteCount` wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedSourceServerModule, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
