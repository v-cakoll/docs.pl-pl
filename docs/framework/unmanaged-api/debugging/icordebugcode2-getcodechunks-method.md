---
title: ICorDebugCode2::GetCodeChunks — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bbc7ac7d87c6a5d36dc3432c603bb7d16d62c00
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747427"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks — Metoda
Pobiera fragmentów kodu, który składa się ten obiekt kodu z.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbufSize`  
 [in] Rozmiar `chunks` tablicy.  
  
 `pcnumChunks`  
 [out] Liczba fragmentów zwracane w `chunks` tablicy.  
  
 `chunks`  
 [out] Tablica struktur "codechunkinfo —", z których każdy reprezentuje jeden fragment kodu. Jeśli wartość `cbufSize` wynosi 0, ten parametr może mieć wartości null.  
  
## <a name="remarks"></a>Uwagi  
 Fragmenty kodu będzie nigdy nie nakładają się na siebie, a zostanie postępuj zgodnie z kolejności, w którym ich będzie mieć zostały połączone przez [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md). Obiekt kodu języka intermediate language (MSIL) firmy Microsoft, w .NET Framework w wersji 2.0 będzie zawierać fragmentów pojedynczego kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
