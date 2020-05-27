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
ms.openlocfilehash: 05902436c09d082f90af01f48c7e918650317ce7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009421"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName — Metoda
Pobiera tablicę zestawów z określonym `szAssemblyName` parametrem przy użyciu standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego (CLR) do rozpoznawania odwołań.  
  
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
 podczas Katalog główny, w którym ma zostać wyszukany dany zestaw. Jeśli ta wartość jest ustawiona na `null` , `FindAssembliesByName` będzie wyglądać tylko w globalnej pamięci podręcznej zestawów dla zestawu.  
  
 `szPrivateBin`  
 podczas Rozdzielana średnikami lista podkatalogów (na przykład "bin; BIN2"), w katalogu głównym, w którym ma zostać wyszukany zestaw. Te katalogi są badane dodatkowo do tych, które są określone w domyślnych regułach sondowania.  
  
 `szAssemblyName`  
 podczas Nazwa zestawu do znalezienia. Format tego ciągu jest definiowany na stronie odwołania do klasy dla <xref:System.Reflection.AssemblyName> .  
  
 `ppIUnk`  
 podczas Tablica typu [IUnknown](/cpp/atl/iunknown) , w której mają zostać umieszczone `IMetadataAssemblyImport` wskaźniki interfejsu.  
  
 `cMax`  
 określoną Maksymalna liczba wskaźników interfejsu, które mogą być umieszczone w `ppIUnk` .  
  
 `pcAssemblies`  
 określoną Liczba zwróconych wskaźników interfejsu. Oznacza to, że liczba wskaźników interfejsu jest umieszczonych w rzeczywistości `ppIUnk` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`pomyślnie zwrócono.|  
|`S_FALSE`|Brak zestawów.|  
  
## <a name="remarks"></a>Uwagi  
 Dana nazwa zestawu, `FindAssembliesByName` Metoda znajduje się w zestawie, zgodnie ze standardowymi regułami dotyczącymi rozpoznawania odwołań do zestawów. (Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName`umożliwia wywołującemu skonfigurowanie różnych aspektów kontekstu programu rozpoznawania nazw, takich jak ścieżka do bazy aplikacji i wyszukiwania prywatnego.  
  
 `FindAssembliesByName`Metoda wymaga zainicjowania środowiska CLR w procesie w celu wywołania logiki rozpoznawania zestawu. W związku z tym należy wywołać [CoInitializeEE —](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (przekazywanie COINITEE_DEFAULT) przed wywołaniem `FindAssembliesByName` , a następnie wykonać wywołanie [CoUninitializeCor —](../hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`Zwraca wskaźnik [IMetaDataImport](imetadataimport-interface.md) do pliku zawierającego manifest zestawu dla nazwy zestawu, która została przeniesiona. Jeśli podana nazwa zestawu nie jest w pełni określona (na przykład jeśli nie zawiera wersji), można zwrócić wiele zestawów.  
  
 `FindAssembliesByName`jest często używany przez kompilator, który próbuje znaleźć przywoływany zestaw w czasie kompilacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport — Interfejs](imetadataassemblyimport-interface.md)
