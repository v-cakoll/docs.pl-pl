---
title: IInstallReferenceItem::GetReference — Metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9395fcc6d896114c25770edbc17761323285099f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796393"
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference — Metoda
Pobiera wskaźnik do struktury [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) reprezentowanej przez ten obiekt [IInstallReferenceItem](iinstallreferenceitem-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppRefData`  
 określoną Zwrócony `FUSION_INSTALL_REFERENCE` wskaźnik.  
  
 `dwFlags`  
 podczas Zarezerwowane do użytku w przyszłości. `dwFlags`musi mieć wartość 0 (zero).  
  
 `pvReserved`  
 podczas Zarezerwowane do użytku w przyszłości. `pvReserved`musi być odwołaniem o wartości null.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IInstallReferenceItem, interfejs](iinstallreferenceitem-interface.md)
- [FUSION_INSTALL_REFERENCE, struktura](fusion-install-reference-structure.md)
