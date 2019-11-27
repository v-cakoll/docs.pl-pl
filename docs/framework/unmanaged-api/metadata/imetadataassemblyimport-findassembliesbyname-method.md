---
title: IMetaDataAssemblyImport::FindAssembliesByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c12d3a7a7d1e52529435361aa12e22e4edeecf03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448288"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName — Metoda
Pobiera tablicę zestawów z określonym parametrem `szAssemblyName` przy użyciu standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego (CLR) do rozpoznawania odwołań.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szAppBase`  
 podczas Katalog główny, w którym ma zostać wyszukany dany zestaw. Jeśli ta wartość jest ustawiona na `null`, `FindAssembliesByName` będzie wyglądać tylko w globalnej pamięci podręcznej zestawów zestawu.  
  
 `szPrivateBin`  
 podczas Rozdzielana średnikami lista podkatalogów (na przykład "bin; BIN2"), w katalogu głównym, w którym ma zostać wyszukany zestaw. Te katalogi są badane dodatkowo do tych, które są określone w domyślnych regułach sondowania.  
  
 `szAssemblyName`  
 podczas Nazwa zestawu do znalezienia. Format tego ciągu jest definiowany na stronie odniesienia klasy dla <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 podczas Tablica typu [IUnknown](/cpp/atl/iunknown) , w której mają zostać umieszczone `IMetadataAssemblyImport` wskaźniki interfejsu.  
  
 `cMax`  
 określoną Maksymalna liczba wskaźników interfejsu, które można umieścić w `ppIUnk`.  
  
 `pcAssemblies`  
 określoną Liczba zwróconych wskaźników interfejsu. Oznacza to, że liczba wskaźników interfejsu faktycznie umieszczonych w `ppIUnk`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` pomyślnie zwrócone.|  
|`S_FALSE`|Brak zestawów.|  
  
## <a name="remarks"></a>Uwagi  
 Podaną nazwę zestawu, Metoda `FindAssembliesByName` odnajduje zestaw według standardowych reguł rozpoznawania odwołań do zestawów. (Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` pozwala wywołującemu konfigurować różne aspekty kontekstu programu rozpoznawania nazw, takie jak ścieżka do bazy aplikacji i wyszukiwania prywatnego.  
  
 Metoda `FindAssembliesByName` wymaga zainicjowania środowiska CLR w procesie w celu wywołania logiki rozpoznawania zestawu. W związku z tym przed wywołaniem `FindAssembliesByName`należy wywołać [CoInitializeEE —](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (przekazując COINITEE_DEFAULT), a następnie wykonać wywołanie [CoUninitializeCor —](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` zwraca wskaźnik [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) do pliku zawierającego manifest zestawu dla nazwy zestawu, która została przeniesiona. Jeśli podana nazwa zestawu nie jest w pełni określona (na przykład jeśli nie zawiera wersji), można zwrócić wiele zestawów.  
  
 `FindAssembliesByName` jest często używany przez kompilator, który próbuje znaleźć przywoływany zestaw w czasie kompilacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
