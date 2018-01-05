---
title: "LoadTypeLibWithResolver — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadTypeLibWithResolver
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: LoadTypeLibWithResolver
helpviewer_keywords: LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f069d09f25575c39db097024384ad1bf14eaaf02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver — Funkcja
Ładuje bibliotekę typów i używa podane [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) rozwiązywać żadnych bibliotek typu wewnętrznie występującego w odwołaniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szFile`  
 [in] Ścieżka do pliku biblioteki typów.  
  
 `regkind`  
 [in] A [wyliczenie REGKIND](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) flagę, która kontroluje sposób zrejestrowanej biblioteki typów. Możliwe wartości to:  
  
-   `REGKIND_DEFAULT`: Użyj domyślnego zachowania rejestracji.  
  
-   `REGKIND_REGISTER`: Zarejestrować tej biblioteki typów.  
  
-   `REGKIND_NONE`: Nie rejestruj tej biblioteki typów.  
  
 `pTlbResolver`  
 [in] Wskaźnik do wykonania [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 [out] Odwołanie do biblioteki typów, który jest ładowany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości HRESULT wymienione w poniższej tabeli.  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_OUTOFMEMORY`|Za mało pamięci.|  
|`E_POINTER`|Co najmniej jeden wskaźniki są nieprawidłowe.|  
|`E_INVALIDARG`|Co najmniej jeden z argumentów jest nieprawidłowa.|  
|`TYPE_E_IOERROR`|Funkcja nie można zapisać do pliku.|  
|`TYPE_E_REGISTRYACCESS`|Nie można otworzyć bazy danych rejestracji systemu.|  
|`TYPE_E_INVALIDSTATE`|Nie można otworzyć biblioteki typów.|  
|`TYPE_E_CANTLOADLIBRARY`|Nie można załadować biblioteki typów lub DLL.|  
  
## <a name="remarks"></a>Uwagi  
 [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) wywołania `LoadTypeLibWithResolver` funkcji podczas procesu konwersji zestawu do typu biblioteki.  
  
 Ta funkcja ładuje określonej biblioteki typów minimalnego dostępu do rejestru. Funkcja następnie sprawdza, czy biblioteki typów dla typu wewnętrznie występującego w odwołaniu biblioteki, z których każdy musi być załadowany i dodawane do biblioteki typu nadrzędnego.  
  
 Przed załadowaniem przywoływanej biblioteki typów, ścieżki pliku odniesienia można rozwiązać pełną ścieżkę. Jest to realizowane przez [ResolveTypeLib — metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) dostarczanym przez [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), który jest przekazywany w `pTlbResolver` parametru.  
  
 Gdy znany jest pełna ścieżka pliku biblioteki typów do którego istnieje odwołanie, `LoadTypeLibWithResolver` funkcja ładuje i dodaje do biblioteki typu nadrzędnego, tworzenia biblioteki Scalonej typu głównego przywoływanej biblioteki typów.  
  
 Po funkcja rozpoznaje i ładuje wszystkie biblioteki typu wewnętrznie występującego w odwołaniu, zwraca odwołanie do biblioteki typów rozpoznać wzorca w `pptlib` parametru.  
  
 `LoadTypeLibWithResolver` Funkcja jest zazwyczaj wywoływana przez [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), który dostarcza własnego wewnętrznego [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementacja `pTlbResolver` parametr.  
  
 Jeśli należy wywołać `LoadTypeLibWithResolver` bezpośrednio, należy podać własne [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** TlbRef.h  
  
 **Biblioteka:** TlbRef.lib  
  
 **Wersja platformy .NET framework:** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Zobacz też  
 [Tlbexp, funkcje pomocy](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [Funkcja LoadTypeLibEx](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)
