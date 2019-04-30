---
title: ISymUnmanagedReader::GetVariables — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 846ff76fb1073394cc27597c9a2015148581cc70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670004"
---
# <a name="isymunmanagedreadergetvariables-method"></a>ISymUnmanagedReader::GetVariables — Metoda
Zwraca wartość zmiennej inną niż lokalna, na jej nadrzędnej i nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `parent`  
 [in] Element nadrzędny zmiennej.  
  
 `cVars`  
 [in] Rozmiar `pVars` tablicy.  
  
 `pcVars`  
 [out] Wskaźnik do zmiennej, która odbiera liczbę zwracanych w zmiennych `pVars`.  
  
 `pVars`  
 [out] Wskaźnik do zmiennej, która odbiera zmienne.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
