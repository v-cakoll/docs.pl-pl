---
title: IAssemblyEnum::GetNextAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73c531378355100fdfca264ea9f96ff4d7c7ceda
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796689"
---
# <a name="iassemblyenumgetnextassembly-method"></a>IAssemblyEnum::GetNextAssembly — Metoda
Pobiera wskaźnik do następnego [IAssemblyName](iassemblyname-interface.md) zawartego w tym obiekcie [IAssemblyEnum](iassemblyenum-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pvReserved`  
 podczas Zarezerwowane do użytku w przyszłości. `pvReserved`musi być odwołaniem o wartości null.  
  
 `ppName`  
 określoną Zwrócony `IAssemblyName` wskaźnik.  
  
 `dwFlags`  
 podczas Zarezerwowane do użytku w przyszłości. `dwFlags`musi mieć wartość 0 (zero).  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyName, interfejs](iassemblyname-interface.md)
- [IAssemblyEnum, interfejs](iassemblyenum-interface.md)
