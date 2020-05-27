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
ms.openlocfilehash: 832adacac4a6df9ccf21578538a1c557150f3ba1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008784"
---
# <a name="imetadatadispenserexgetoption-method"></a>IMetaDataDispenserEx::GetOption — Metoda
Pobiera wartość określonej opcji dla bieżącego zakresu metadanych. Opcja określa, jak są obsługiwane wywołania bieżącego zakresu metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `optionId`  
 podczas Wskaźnik do identyfikatora GUID, który określa opcję do pobrania. Zobacz sekcję Uwagi, aby zapoznać się z listą obsługiwanych identyfikatorów GUID.  
  
 `pValue`  
 określoną Wartość zwracanej opcji. Typ tej wartości będzie wariantem typu określonej opcji.  
  
## <a name="remarks"></a>Uwagi  
 Poniższa lista zawiera identyfikatory GUID, które są obsługiwane dla tej metody. Aby uzyskać opis, zobacz metodę [IMetaDataDispenserEx:: SetOption](imetadatadispenserex-setoption-method.md) . Jeśli `optionId` nie znajduje się na tej liście, ta metoda zwraca wartość HRESULT `E_INVALIDARG` , wskazującą nieprawidłowy parametr.  
  
- MetaDataCheckDuplicatesFor  
  
- MetaDataRefToDefCheck  
  
- MetaDataNotificationForTokenMovement  
  
- MetaDataSetENC  
  
- MetaDataErrorIfEmitOutOfOrder  
  
- MetaDataGenerateTCEAdapters  
  
- MetaDataLinkerOptions  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataDispenserEx, interfejs](imetadatadispenserex-interface.md)
- [IMetaDataDispenser — Interfejs](imetadatadispenser-interface.md)
