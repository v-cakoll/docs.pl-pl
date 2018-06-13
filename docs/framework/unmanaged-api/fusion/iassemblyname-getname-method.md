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
ms.openlocfilehash: 06c918de10f86442b10b0d85e6554bb1af0a8928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429614"
---
# <a name="iassemblynamegetname-method"></a>IAssemblyName::GetName — Metoda
Pobiera nazwę proste, niezaszyfrowanym zestawu odwołuje się ten [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lpcwBuffer`  
 [w, out] Rozmiar `pwzName` znaki dwubajtowe, w tym znak ogranicznika wartości null.  
  
 `pwzName`  
 [out] Bufor aby pomieścić nazwę przywoływanego zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IAssemblyName, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
