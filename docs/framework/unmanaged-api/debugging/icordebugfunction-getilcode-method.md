---
title: ICorDebugFunction::GetILCode — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac34fbca56c8a0f00ee3a7e0f898b8ee03287b11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412288"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode — Metoda
Pobiera wystąpienie ICorDebugCode, który reprezentuje kod języka pośredniego (MSIL) firmy Microsoft, które są skojarzone z tym obiektem ICorDebugFunction.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppCode`  
 [out] Wskaźnik do `ICorDebugCode` wystąpienia, lub wartość null, jeśli funkcja nie został skompilowany do MSIL.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zezwolono Edytuj i Kontynuuj dla tej funkcji `GetILCode` metoda pobierze kod MSIL odpowiadającego tej funkcji zmodyfikowaną wersję kodu w środowisku uruchomieniowym języka (wspólnego CLR).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
