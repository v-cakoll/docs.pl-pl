---
title: IMetaDataImport::EnumPermissionSets — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7d9874d4a609c353ae772b75a48af632bf4e85d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756545"
---
# <a name="imetadataimportenumpermissionsets-method"></a>IMetaDataImport::EnumPermissionSets — Metoda
Wylicza uprawnienia dla obiektów w zakresie określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,   
   [in]      mdToken       tk,   
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out w] Wskaźnik do modułu wyliczającego. Musi to być wartość NULL dla pierwszego wywołania tej metody.  
  
 `tk`  
 [in] Token metadanych, który ogranicza zakres wyszukiwania lub wartość NULL, wyszukiwanie najszerszego zakresu możliwe.  
  
 `dwActions`  
 [in] Flagi reprezentujący <xref:System.Security.Permissions.SecurityAction> wartości, które mają zostać objęte `rPermission`, lub wartość zero, aby zwrócić wszystkie akcje.  
  
 `rPermission`  
 [out] Tablica do przechowywania tokenów uprawnień.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rPermission` tablicy.  
  
 `pcTokens`  
 [out] Liczba tokenów uprawnienie zwracane w `rPermission`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumPermissionSets` pomyślnie zwrócił.|  
|`S_FALSE`|Nie ma żadnych tokeny do wyliczenia. W takim przypadku `pcTokens` wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
