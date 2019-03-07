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
ms.openlocfilehash: c23494f8c0a977624b899f01e843ba3545a22fbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501654"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a>IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda
Pobiera wskaźnik do następnego [iinstallreferenceitem —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) obiektów znajdujących się w tym [iinstallreferenceenum —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
