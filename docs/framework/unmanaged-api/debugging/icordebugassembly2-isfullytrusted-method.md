---
title: ICorDebugAssembly2::IsFullyTrusted — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd3b977a894f8cb1fc9a866f5a43265d917db513
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645568"
---
# <a name="icordebugassembly2isfullytrusted-method"></a>ICorDebugAssembly2::IsFullyTrusted — Metoda
Pobiera wartość wskazującą, czy zestaw ma udzielone pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbFullyTrusted`  
 [out] `true` Jeśli zestaw ma udzielone pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość HRESULT z CORDBG_E_NOTREADY Jeśli zasady zabezpieczeń dla zestawu nie została jeszcze rozwiązane, oznacza to, jeśli żaden kod w zestawie ma jeszcze uruchomione.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
