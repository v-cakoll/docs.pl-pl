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
ms.openlocfilehash: e32ce10b708afa5741d83cbd05f14accb4b2014f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754668"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode — Metoda
Pobiera wystąpienie ICorDebugCode, który reprezentuje kod intermediate language (MSIL) firmy Microsoft, które są skojarzone z tym obiektem ICorDebugFunction.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppCode`  
 [out] Wskaźnik do `ICorDebugCode` wystąpienia lub wartość null, jeśli funkcja nie został skompilowany w MSIL.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zezwolono Edytuj i Kontynuuj dla tej funkcji `GetILCode` metody zostanie wyświetlony kod MSIL odpowiadający tej funkcji edytowaną wersją kodu w środowisku uruchomieniowym języka (wspólnego CLR).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
