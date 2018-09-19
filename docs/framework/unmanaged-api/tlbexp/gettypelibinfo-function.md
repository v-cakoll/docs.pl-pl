---
title: GetTypeLibInfo — Funkcja
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ec28c581b8e6e0aff3a2765720b6e9795be931b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003103"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo — Funkcja
Zwraca informacje dotyczące określonej biblioteki typu, sprawdzając jego [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szFile`  
 [in] Nazwa pliku biblioteki typów.  
  
 `pTypeLibID`  
 [out] Identyfikator GUID biblioteki typów.  
  
 `pTypeLibLCID`  
 [out] Identyfikator lokalizacji biblioteki typów.  
  
 `pTypeLibPlatform`  
 [out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flagę, która identyfikuje docelowego systemu operacyjnego dla biblioteki typów. Typowe wartości to SYS_WIN32 i SYS_WIN64.  
  
 `pTypeLibMajorVer`  
 [out] Główny numer wersji biblioteki typów. Na przykład w przypadku wersji *x.y*, główny numer wersji jest *x*.  
  
 `pTypeLibMinorVer`  
 [out] Pomocniczy numer wersji biblioteki typów. Na przykład w przypadku wersji *x.y*, pomocniczy numer wersji jest *y*.  
  
## <a name="remarks"></a>Uwagi  
 `GetTypeLibInfo` Funkcja jest wywoływana przez [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md). To narzędzie generuje bibliotekę typów opisującą typy w zestawie środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.  
  
 Jeśli którykolwiek z parametrów ma wartość null, funkcja zwraca `HRESULT` z `E_POINTER`. W przeciwnym razie zwraca `S_OK`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** TlbRef.h  
  
 **Biblioteka:** TlbRef.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tlbexp, funkcje pomocy](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx — funkcja](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
