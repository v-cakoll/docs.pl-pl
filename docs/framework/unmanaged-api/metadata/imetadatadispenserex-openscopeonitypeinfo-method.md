---
title: "IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45c65d0194ed44122a87dcd000359187fc020d0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a>IMetaDataDispenserEx::OpenScopeOnITypeInfo — Metoda
Ta metoda nie jest zaimplementowana. Wywołuje się, zwraca E_NOTIMPL.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pITI`  
 [in] Wskaźnik do [ITypeInfo](http://msdn.microsoft.com/library/f3356463-3373-4279-bae1-953378aa2680) interfejs, który zawiera informacje o typie, na którym ma zostać otwarty zakresu.  
  
 `dwOpenFlags`  
 [in] Flagi trybu otwartego.  
  
 `riid`  
 [in] Żądany interfejs.  
  
 `ppIUnk`  
 [out] Wskaźnik na wskaźnik do interfejsu zwrócony.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataDispenserEx, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataDispenser, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
