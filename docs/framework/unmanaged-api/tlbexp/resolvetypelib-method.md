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
ms.openlocfilehash: 46cd8b5c22f48ba45c4da7fa8876d6807a21f2b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124146"
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
 określoną Wskaźnik do typu [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , który zawiera pełną ścieżkę biblioteki typów o nazwie w parametrze `bstrSimpleName`.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `ResolveTypeLib` jest wywoływana przez [funkcję LoadTypeLibWithResolver —](loadtypelibwithresolver-function.md) podczas przetwarzania [Tlbexp. exe (Eksporter biblioteki typów)](../../tools/tlbexp-exe-type-library-exporter.md) .  
  
 Niestandardowe implementacje tego interfejsu muszą zwracać typ [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) , który zawiera pełną ścieżkę biblioteki typów o nazwie w parametrze `bstrSimpleName`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** TlbRef. idl, TlbRef. h  
  
 **Biblioteka:** TlbRef. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Tlbexp, funkcje pomocy](index.md)
- [LoadTypeLibEx](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
