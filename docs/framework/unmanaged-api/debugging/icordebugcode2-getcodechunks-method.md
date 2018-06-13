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
ms.openlocfilehash: bdfcd45b15ddc1491b12de0fa42901b6d3f7fe9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413156"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks — Metoda
Pobiera fragmentów kodu, który składa się ten obiekt kodu z.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbufSize`  
 [in] Rozmiar `chunks` tablicy.  
  
 `pcnumChunks`  
 [out] Liczba fragmentów zwracane w `chunks` tablicy.  
  
 `chunks`  
 [out] Tablica struktury "CodeChunkInfo", z których każdy reprezentuje jednego fragmentu kodu. Jeśli wartość `cbufSize` wynosi 0, ten parametr może mieć wartości null.  
  
## <a name="remarks"></a>Uwagi  
 Fragmenty kodu nigdy nie będzie nakłada, a użytkownicy zastosują kolejność, w którym one będzie mieć został połączony przez [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md). Obiekt kodu języka pośredniego (MSIL) firmy Microsoft, w programie .NET Framework w wersji 2.0 obejmuje fragmentu kodu pojedynczego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
