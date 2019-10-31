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
ms.openlocfilehash: c2ce4b95de75bef3928e144656b565676568caa0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137909"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode — Metoda
Pobiera wystąpienie ICorDebugCode, które reprezentuje kod języka pośredniego firmy Microsoft (MSIL) skojarzony z tym obiektem ICorDebugFunction.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppCode`  
 określoną Wskaźnik do wystąpienia `ICorDebugCode` lub wartość null, jeśli funkcja nie została skompilowana do MSIL.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja Edytuj i Kontynuuj jest dozwolona dla tej funkcji, Metoda `GetILCode` pobierze kod MSIL odpowiadający edytowanej wersji kodu w środowisku uruchomieniowym języka wspólnego (CLR).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
