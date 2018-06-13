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
ms.openlocfilehash: 00a95646323a5ee08d6758b0f6a7c493c661705d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431779"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName — Metoda
Pobiera nazwę zrozumiałą zestawu odwołuje się ten [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szDisplayName`  
 [out] Bufor ciąg zawierający nazwę przywoływanego zestawu.  
  
 `pccDisplayName`  
 [w, out] Rozmiar `szDisplayName` znaki dwubajtowe, w tym znaków terminatorem null.  
  
 `dwDisplayFlags`  
 [in] Bitowe połączenie [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) wartości wpływających na funkcje `szDisplayName`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IAssemblyName, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Wyliczenia łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
