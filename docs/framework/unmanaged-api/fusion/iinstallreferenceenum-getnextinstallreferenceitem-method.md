---
title: IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0dd96b10b5ee2880e0f9ee18048ec8ba2ee0b5ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779061"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a>IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda
Pobiera wskaźnik do następnego [iinstallreferenceitem —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) obiektów znajdujących się w tym [iinstallreferenceenum —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRefItem`  
 [out] Zwrócony `IInstallReferenceItem` wskaźnika.  
  
 `dwFlags`  
 [in] Zarezerwowane dla przyszłej rozszerzalności. `dwFlags` musi być równa 0 (zero).  
  
 `pvReserved`  
 [in] Zarezerwowane dla przyszłej rozszerzalności. `pvReserved` musi być odwołanie o wartości null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IInstallReferenceItem, interfejs](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [IInstallReferenceEnum, interfejs](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
