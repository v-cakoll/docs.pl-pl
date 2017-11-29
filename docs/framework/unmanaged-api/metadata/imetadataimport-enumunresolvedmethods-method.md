---
title: "IMetaDataImport::EnumUnresolvedMethods — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUnresolvedMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3c7709180e5b7811379c25977f8a8d23b91adb3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a>IMetaDataImport::EnumUnresolvedMethods — Metoda
Wylicza tokenów MemberDef reprezentujący nierozwiązane metod w bieżącym zakresie metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, out] Wskaźnik do modułu wyliczającego. Musi to być wartość NULL dla pierwsze wywołanie tej metody.  
  
 `rMethods`  
 [out] Tablica używany do przechowywania tokenów MemberDef.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rMethods` tablicy.  
  
 `pcTokens`  
 [out] Liczba tokenów MemberDef zwracane w `rMethods`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumUnresolvedMethods`zwrócona pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów do wyliczenia. W takim przypadku `pcTokens` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 Nierozpoznane metody to taki, który został zadeklarowany, ale nie jest zaimplementowana. Jeśli metoda jest oznaczona jako metoda znajduje się w wyliczeniu `miForwardRef` i `mdPinvokeImpl` lub `miRuntime` jest ustawiony na zero. Innymi słowy, nierozpoznane metoda jest metodą klasy oznaczonej jako `miForwardRef` , ale które nie jest zaimplementowana w niezarządzanym kodzie (Osiągnięto za pomocą funkcji PInvoke) ani nie zaimplementowana wewnętrznie przez środowisko wykonawcze  
  
 Wyliczanie nie obejmuje wszystkie metody, które są zdefiniowane w zakresie modułu (globalne) lub interfejsy lub klasy abstrakcyjne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
