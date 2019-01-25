---
title: ResolveTypeLib — Metoda
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6558d27f10e5b93dfe2c8053bb96434d49fd3c4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537217"
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
 [in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) zawierający prostą nazwę biblioteki typów.  
  
 `tlbid`  
 [in] Identyfikator GUID jest przypisany do biblioteki typów w rejestrze.  
  
 `lcid`  
 [in] Identyfikator lokalizacji biblioteki typów.  
  
 `wMajorVersion`  
 [in] Główny numer wersji biblioteki typów. Na przykład w przypadku wersji *x.y*, główny numer wersji jest *x*.  
  
 `wMinorVersion`  
 [in] Pomocniczy numer wersji biblioteki typów. Na przykład w przypadku wersji *x.y*, pomocniczy numer wersji jest *y*.  
  
 `syskind`  
 [in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flagę, która identyfikuje środowisko operacyjne. Typowe wartości to SYS_WIN32 i SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 [out] Wskaźnik do [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) zawierającą pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.  
  
## <a name="remarks"></a>Uwagi  
 `ResolveTypeLib` Metoda jest wywoływana przez [loadtypelibwithresolver — funkcja](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) podczas [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) przetwarzania.  
  
 Niestandardowe implementacje tego interfejsu musi zwracać [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) zawierającą pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** TlbRef.idl, TlbRef.h  
  
 **Biblioteka:** TlbRef.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Tlbexp, funkcje pomocy](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
