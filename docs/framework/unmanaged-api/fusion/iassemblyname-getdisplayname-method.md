---
title: IAssemblyName::GetDisplayName — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 323c883b4010f3ddd4c575e5d5fc40a3419e57c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697410"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName — Metoda
Pobiera nazwę zrozumiałą dla użytkownika, zestawu odwołuje się ten [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szDisplayName`  
 [out] Buforu ciągu, który zawiera nazwę przywoływanego zestawu.  
  
 `pccDisplayName`  
 [out w] Rozmiar `szDisplayName` znaków dwubajtowych, w tym znak terminator o wartości null.  
  
 `dwDisplayFlags`  
 [in] Bitowa kombinacja [asm_display_flags —](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) wartości, które wpływają na funkcje `szDisplayName`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyName, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [Wyliczenia łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
