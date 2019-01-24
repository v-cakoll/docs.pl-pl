---
title: IMetaDataDispenserEx::GetOption — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6287b7adf0ef6f6269a51f608657444f5fa7f74e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580229"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption — Metoda
Pobiera wartość określonej opcji dla bieżącego zakresu metadanych. Opcja określa, jak wywołania z bieżących zakresem metadane są obsługiwane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `optionId`  
 [in] Wskaźnik do identyfikator GUID, który określa opcje, które mają zostać pobrane. Zobacz sekcję Spostrzeżenia, aby listę obsługiwanych identyfikatorów GUID.  
  
 `pValue`  
 [out] Wartość zwrócona opcji. Typ tej wartości będą wariant określoną opcję typu.  
  
## <a name="remarks"></a>Uwagi  
 Poniższa lista zawiera identyfikatory GUID, które są obsługiwane w przypadku tej metody. Aby uzyskać opis, zobacz [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody. Jeśli `optionId` jest nie ma na tej liście, ta metoda zwraca wartość HRESULT `E_INVALIDARG`, wskazując określono nieprawidłowy parametr.  
  
-   MetaDataCheckDuplicatesFor  
  
-   MetaDataRefToDefCheck  
  
-   MetaDataNotificationForTokenMovement  
  
-   MetaDataSetENC  
  
-   MetaDataErrorIfEmitOutOfOrder  
  
-   MetaDataGenerateTCEAdapters  
  
-   MetaDataLinkerOptions  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
