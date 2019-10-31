---
title: IAssemblyName::SetProperty — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
ms.openlocfilehash: ffa1fa2f5e141728a56f1b598a1aae9602b2ac86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108217"
---
# <a name="iassemblynamesetproperty-method"></a>IAssemblyName::SetProperty — Metoda
Ustawia wartość właściwości, do której odwołuje się określony identyfikator właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `PropertyId`  
 podczas Unikatowy identyfikator właściwości, której wartość zostanie ustawiona.  
  
 `pvProperty`  
 podczas Wartość, dla której ma zostać ustawiona właściwość, do której odwołuje się `PropertyId`.  
  
 `cbProperty`  
 podczas Rozmiar w bajtach `pvProperty`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyName, interfejs](iassemblyname-interface.md)
