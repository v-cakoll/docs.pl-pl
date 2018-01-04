---
title: "ResolveTypeLib — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ResolveTypeLib
api_location: tlbref.dll
f1_keywords: ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b668610f50c32373790130def17928b8b3b3d8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib — Metoda
Rozpoznaje prostą nazwę biblioteki typów, przywracając jego w pełni kwalifikowaną ścieżkę.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrSimpleName`  
 [in] A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) zawierającą prostą nazwę biblioteki typów.  
  
 `tlbid`  
 [in] Identyfikator GUID przypisane do biblioteki typów w rejestrze.  
  
 `lcid`  
 [in] Identyfikator lokalizacji biblioteki typów.  
  
 `wMajorVersion`  
 [in] Numer wersji głównej biblioteki typów. Na przykład w przypadku wersji *x.y*, numer wersji głównej jest *x*.  
  
 `wMinorVersion`  
 [in] Podrzędny numer wersji biblioteki typów. Na przykład w przypadku wersji *x.y*, podrzędny numer wersji jest *y*.  
  
 `syskind`  
 [in] A [SYSKIND](http://msdn.microsoft.com/en-us/662048b2-59a8-48ca-9e4f-2f9a5306faa1) Flaga, która identyfikuje środowisku operacyjnym. Typowe wartości to SYS_WIN32 i SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 [out] Wskaźnik do [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) zawiera pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.  
  
## <a name="remarks"></a>Uwagi  
 `ResolveTypeLib` Metoda jest wywoływana przez [loadtypelibwithresolver — funkcja](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) podczas [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) przetwarzania.  
  
 Niestandardowe implementacje tego interfejsu musi zwracać [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) zawiera pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** TlbRef.idl, TlbRef.h  
  
 **Biblioteka:** TlbRef.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tlbexp, funkcje pomocy](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx](http://msdn.microsoft.com/en-us/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
