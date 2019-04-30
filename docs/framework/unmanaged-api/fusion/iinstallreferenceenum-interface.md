---
title: IInstallReferenceEnum — Interfejs
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35faeb69e864a428dc40394ad89a7d50b95bbcab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757667"
---
# <a name="iinstallreferenceenum-interface"></a>IInstallReferenceEnum — Interfejs
Reprezentuje moduł wyliczający przywoływanych zestawach zainstalowane w globalnej pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetNextInstallReferenceItem, metoda](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|Pobiera wskaźnik do następnego `IInstallReferenceItem` zawarte w tym `IInstallReferenceEnum`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IInstallReferenceItem, interfejs](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
