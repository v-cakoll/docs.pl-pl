---
title: "IMetaDataImport::EnumMembersWithName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMembersWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b0cef8fca7be315185ab521464b251f2a94f3b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummemberswithname-method"></a>IMetaDataImport::EnumMembersWithName — Metoda
Wylicza tokenów MemberDef reprezentujący elementy członkowskie określonego typu o określonej nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [in]      LPCWSTR     szName,   
   [out]     mdToken     rMembers[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [w, out] Wskaźnik do modułu wyliczającego.  
  
 `cl`  
 [in] Element TypeDef token reprezentujący typ z elementami członkowskimi wyliczyć.  
  
 `szName`  
 [in] Nazwa elementu członkowskiego, która ogranicza zakres modułu wyliczającego.  
  
 `rMembers`  
 [out] Tablica używany do przechowywania tokenów MemberDef.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rMembers` tablicy.  
  
 `pcTokens`  
 [out] Rzeczywista liczba tokenów MemberDef zwracane w `rMembers`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wylicza pól i metod, ale nie do właściwości lub zdarzenia. W odróżnieniu od [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` odrzuca wszystkie tokeny pola i elementu członkowskiego, które nie mają określonej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs`zwrócona pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów MemberDef do wyliczenia. W takim przypadku `pcTokens` wynosi zero.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
