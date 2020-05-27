---
title: IMetaDataEmit::SetHandler — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 4fa227d18b8cb10936d93fda9bcaf413ce63ca3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003954"
---
# <a name="imetadataemitsethandler-method"></a>IMetaDataEmit::SetHandler — Metoda
Ustawia metodę przywoływaną przez określony `IUnknown` wskaźnik jako wywołanie zwrotne powiadomienia o ponownym mapowaniu tokenu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pUnk`  
 podczas Procedura obsługi do rejestracji.  
  
## <a name="remarks"></a>Uwagi  
 Aparat metadanych wysyła powiadomienie przy użyciu metody dostarczonej przez `SetHandler` , do kompilatorów, które nie generują rekordów w sposób zoptymalizowany i który chce zoptymalizować zapisane rekordy.  
  
 Jeśli nie podano metody wywołania zwrotnego za pośrednictwem programu `SetHandler` , nie będzie przeprowadzana żadna Optymalizacja przy zapisywaniu, z wyjątkiem sytuacji, gdy kilka zakresów importu zostało scalonych przy użyciu `IMapToken` scalania dla każdego zakresu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
