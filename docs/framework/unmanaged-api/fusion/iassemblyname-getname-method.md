---
title: IAssemblyName::GetName — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e471ee99af57ef980850c0a5d3e4f5f2973967ac
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796608"
---
# <a name="iassemblynamegetname-method"></a>IAssemblyName::GetName — Metoda
Pobiera prostą, niezaszyfrowaną nazwę zestawu, do którego odwołuje się ten obiekt [IAssemblyName](iassemblyname-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpcwBuffer`  
 [in. out] Rozmiar znaków dwubajtowych, `pwzName` w tym znak końcowy o wartości null.  
  
 `pwzName`  
 określoną Bufor przechowujący nazwę przywoływanego zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyName, interfejs](iassemblyname-interface.md)
