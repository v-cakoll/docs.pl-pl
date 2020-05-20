---
title: IBindingDisplay::InitializeForProcess — Metoda
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442153"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess — Metoda
Inicjuje obiekt [IBindingDisplay](ibindingdisplay-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pid`  
 podczas Identyfikator procesu.  
  
## <a name="remarks"></a>Uwagi  
 Debuger wywołuje `InitializeForProcess` metodę w czasie tworzenia w celu zainicjowania wyświetlania powiązania. `InitializeForProcess`musi być wywoływana w czasie tworzenia przed wywołaniem innej metody na `IBindingDisplay` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** BindingDisplay. h  
  
 **Biblioteka:** BindingDisplay. idl  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IBindingDisplay — Interfejs](ibindingdisplay-interface.md)
