---
title: LoadTypeLibWithResolver — Funkcja
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6a217e2212bb900d7ba83ccdd9cb00d30454baf
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211700"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver — Funkcja
Ładuje bibliotekę typów i korzysta z podanym [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) rozpoznać wszystkie biblioteki typu wewnętrznie odwołania.  
  
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
 [in] Ścieżka pliku biblioteki typów.  
  
 `regkind`  
 [in] A [wyliczenie REGKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) flagi, które kontroluje sposób zrejestrowanej biblioteki typów. Jego możliwe wartości to:  
  
-   `REGKIND_DEFAULT`: Użyj domyślnego zachowania rejestracji.  
  
-   `REGKIND_REGISTER`: Zarejestruj tej biblioteki typów.  
  
-   `REGKIND_NONE`: Nie rejestruj tej biblioteki typów.  
  
 `pTlbResolver`  
 [in] Wskaźnik do implementacji [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 [out] Odwołanie do biblioteki typów, który jest ładowany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości HRESULT, wymienione w poniższej tabeli.  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_OUTOFMEMORY`|Za mało pamięci.|  
|`E_POINTER`|Co najmniej jeden ze wskaźników są nieprawidłowe.|  
|`E_INVALIDARG`|Co najmniej jeden z argumentów są nieprawidłowe.|  
|`TYPE_E_IOERROR`|Funkcja nie można zapisać do pliku.|  
|`TYPE_E_REGISTRYACCESS`|Nie można otworzyć bazy danych rejestracji systemu.|  
|`TYPE_E_INVALIDSTATE`|Nie można otworzyć biblioteki typów.|  
|`TYPE_E_CANTLOADLIBRARY`|Nie można załadować biblioteki typów lub DLL.|  
  
## <a name="remarks"></a>Uwagi  
 [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) wywołania `LoadTypeLibWithResolver` funkcji w procesie konwersji zestawu do typu biblioteki.  
  
 Ta funkcja ładuje określonej biblioteki typu przy użyciu minimalnego dostępu do rejestru. Funkcja następnie sprawdza, czy biblioteki typów dla wewnętrznie odwołania biblioteki typów, z których każdy musi być załadowane i dodawane do biblioteki typu nadrzędnego.  
  
 Przed załadowaniem przywoływanej biblioteki typów, ścieżki pliku odwołania muszą zostać rozwiązane do pełnej ścieżki pliku. Jest to realizowane za pośrednictwem [resolvetypelib — metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) dostarczanym przez [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), która jest przekazywana w `pTlbResolver` parametru.  
  
 Gdy znana jest pełną ścieżką do pliku biblioteki typów w przywoływanych, `LoadTypeLibWithResolver` funkcji ładuje i dodaje przywoływanej biblioteki typów do biblioteki typów nadrzędnego, tworzenie biblioteki typów wzorca połączone.  
  
 Po funkcji rozpoznaje i ładuje wszystkie biblioteki wewnętrznie odwołanie typu, zwraca odwołanie do biblioteki wzorca rozpoznany typ w `pptlib` parametru.  
  
 `LoadTypeLibWithResolver` Funkcja jest zazwyczaj wywoływana przez [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), który dostarcza własnego wewnętrznego [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementacji `pTlbResolver` parametr.  
  
 Jeśli wywołasz `LoadTypeLibWithResolver` bezpośrednio, należy podać własne [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** TlbRef.h  
  
 **Biblioteka:** TlbRef.lib  
  
 **Wersja programu .NET framework:** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Zobacz też  
 [Tlbexp, funkcje pomocy](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx — funkcja](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
