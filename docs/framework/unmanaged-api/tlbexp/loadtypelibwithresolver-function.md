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
ms.openlocfilehash: adbb5eca3b7ffa36d0c963d0dacc3b2afdb664d4
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935563"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver — Funkcja
Ładuje bibliotekę typów i używa dostarczonego [interfejsu ITypeLibResolver](itypelibresolver-interface.md) do rozpoznawania wszelkich wewnętrznie przywoływanych bibliotek typów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>Parametry  
 `szFile`  
 podczas Ścieżka pliku biblioteki typów.  
  
 `regkind`  
 podczas Flaga [wyliczenia REGKIND](/windows/win32/api/oleauto/ne-oleauto-regkind) , która kontroluje sposób rejestrowania biblioteki typów. Możliwe wartości to:  
  
- `REGKIND_DEFAULT`: Użyj domyślnego zachowania rejestrowania.  
  
- `REGKIND_REGISTER`: Zarejestruj tę bibliotekę typów.  
  
- `REGKIND_NONE`: nie Rejestruj tej biblioteki typów.  
  
 `pTlbResolver`  
 podczas Wskaźnik do implementacji [interfejsu ITypeLibResolver](itypelibresolver-interface.md).  
  
 `pptlib`  
 określoną Odwołanie do biblioteki typów, która jest ładowana.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Jedna z wartości HRESULT wymienionych w poniższej tabeli.  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_OUTOFMEMORY`|Za mało pamięci.|  
|`E_POINTER`|Co najmniej jeden wskaźnik jest nieprawidłowy.|  
|`E_INVALIDARG`|Co najmniej jeden z argumentów jest nieprawidłowy.|  
|`TYPE_E_IOERROR`|Funkcja nie może wykonać zapisu w pliku.|  
|`TYPE_E_REGISTRYACCESS`|Nie można otworzyć bazy danych rejestracji systemu.|  
|`TYPE_E_INVALIDSTATE`|Nie można otworzyć biblioteki typów.|  
|`TYPE_E_CANTLOADLIBRARY`|Nie można załadować biblioteki typów lub biblioteki DLL.|  
  
## <a name="remarks"></a>Uwagi  
 [Tlbexp. exe (Eksporter biblioteki typów)](../../tools/tlbexp-exe-type-library-exporter.md) wywołuje funkcję `LoadTypeLibWithResolver` w procesie konwersji zestawu na typ biblioteki.  
  
 Ta funkcja ładuje określoną bibliotekę typów o minimalnym dostępie do rejestru. Funkcja następnie analizuje bibliotekę typów dla wewnętrznie przywoływanych bibliotek typów, z których każdy musi być załadowany i dodany do biblioteki typów nadrzędnych.  
  
 Przed załadowaniem przywoływanej biblioteki typów, jej ścieżka do pliku odniesienia musi zostać rozpoznana jako pełna ścieżka pliku. Jest to realizowane za pomocą [metody ResolveTypeLib —](resolvetypelib-method.md) dostarczonej przez [interfejs ITypeLibResolver](itypelibresolver-interface.md), który jest przekazywany w parametrze `pTlbResolver`.  
  
 Gdy znana jest pełna ścieżka do pliku z przywoływaną biblioteką typów, funkcja `LoadTypeLibWithResolver` ładuje i dodaje przywoływaną bibliotekę typów do biblioteki typów nadrzędnych, tworząc połączoną bibliotekę typów głównych.  
  
 Po rozpoznaniu i załadowaniu wszystkich wewnętrznie przywoływanych bibliotek typów funkcja zwraca odwołanie do głównej, rozwiązanej biblioteki typów w parametrze `pptlib`.  
  
 Funkcja `LoadTypeLibWithResolver` jest zazwyczaj wywoływana przez [Tlbexp. exe (Eksporter biblioteki typów)](../../tools/tlbexp-exe-type-library-exporter.md), która dostarcza własną wewnętrzną implementację [interfejsu ITypeLibResolver](itypelibresolver-interface.md) w parametrze `pTlbResolver`.  
  
 W przypadku wywołania `LoadTypeLibWithResolver` bezpośrednio należy podać własną implementację [interfejsu ITypeLibResolver](itypelibresolver-interface.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** TlbRef. h  
  
 **Biblioteka:** TlbRef. lib  
  
 **Wersja .NET Framework:** 3,5, 3,0, 2,0  
  
## <a name="see-also"></a>Zobacz także

- [Tlbexp, funkcje pomocy](index.md)
- [LoadTypeLibEx, funkcja](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
