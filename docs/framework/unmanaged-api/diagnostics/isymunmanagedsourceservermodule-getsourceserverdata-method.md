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
ms.openlocfilehash: 6904271ed90cf733b9221178927bc680d76b58a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176581"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a>ISymUnmanagedSourceServerModule::GetSourceServerData — Metoda
Zwraca dane serwera źródłowego dla modułu. Rozmówca musi zwolnić zasoby `CoTaskMemFree`za pomocą programu .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDataByteCount`  
 [na zewnątrz] Wskaźnik `ULONG32` do, który odbiera rozmiar w bajtach danych serwera źródłowego.  
  
 `ppData`  
 [na zewnątrz] Wskaźnik do zwróconej `pDataByteCount` wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też

- [ISymUnmanagedSourceServerModule — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
