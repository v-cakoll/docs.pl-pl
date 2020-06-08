---
title: IMetaDataImport::GetClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 36c0ffef2d984604be4ae19899e8f3f912cee123
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491475"
---
# <a name="imetadataimportgetclasslayout-method"></a>IMetaDataImport::GetClassLayout — Metoda
Pobiera informacje o układzie dla klasy, do której odwołuje się określony token TypeDef.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 podczas Token TypeDef dla klasy z układem, który ma zostać zwrócony.  
  
 `pdwPackSize`  
 określoną Jedna z wartości 1, 2, 4, 8 lub 16 reprezentuje rozmiar pakietu klasy.  
  
 `rFieldOffset`  
 określoną Tablica wartości [COR_FIELD_OFFSET](cor-field-offset-structure.md) .  
  
 `cMax`  
 podczas Maksymalny rozmiar `rFieldOffset` tablicy.  
  
 `pcFieldOffset`  
 określoną Liczba elementów zwróconych w `rFieldOffset` .  
  
 `pulClassSize`  
 określoną Rozmiar w bajtach klasy reprezentowanej przez `td` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
