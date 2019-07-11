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
ms.openlocfilehash: 916d62a2b79a44d92611e735c6f9bbb3e01970e2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782738"
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo — Funkcja
Zwraca informacje dotyczące określonej biblioteki typu, sprawdzając jego [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a>Parametry  
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
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** TlbRef.h  
  
 **Biblioteka:** TlbRef.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Tlbexp, funkcje pomocy](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx — funkcja](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
