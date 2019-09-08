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
ms.openlocfilehash: ce0f11547d4b16516b7c78d1b1947f5c4bc831a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798801"
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib — Metoda
Rozpoznaje prostą nazwę biblioteki typów przez zwrócenie jej w pełni kwalifikowanej ścieżki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a>Parametry  
 `bstrSimpleName`  
 podczas [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , który zawiera prostą nazwę biblioteki typów.  
  
 `tlbid`  
 podczas Identyfikator GUID przypisany do biblioteki typów w rejestrze.  
  
 `lcid`  
 podczas Identyfikator lokalizacji biblioteki typów.  
  
 `wMajorVersion`  
 podczas Numer wersji głównej biblioteki typów. Na przykład w przypadku wersji *x. y*główny numer wersji to *x*.  
  
 `wMinorVersion`  
 podczas Numer wersji pomocniczej biblioteki typów. Na przykład w przypadku wersji *x. y*pomocniczy numer wersji to *y*.  
  
 `syskind`  
 podczas Flaga [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) , która identyfikuje środowisko operacyjne. Wspólne wartości to SYS_WIN32 i SYS_WIN64.  
  
 `pbstrResolvedTlbName`  
 określoną Wskaźnik do typu [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , który zawiera pełną ścieżkę do biblioteki typów o nazwie w `bstrSimpleName` parametrze.  
  
## <a name="remarks"></a>Uwagi  
 Metoda jest wywoływana przez [funkcję LoadTypeLibWithResolver —](loadtypelibwithresolver-function.md) podczas przetwarzania [Tlbexp. exe (Eksporter biblioteki typów).](../../tools/tlbexp-exe-type-library-exporter.md) `ResolveTypeLib`  
  
 Niestandardowe implementacje tego interfejsu muszą zwracać element [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , który zawiera pełną ścieżkę biblioteki typów o nazwie w `bstrSimpleName` parametrze.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** TlbRef. idl, TlbRef. h  
  
 **Biblioteki** TlbRef.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Tlbexp, funkcje pomocy](index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
