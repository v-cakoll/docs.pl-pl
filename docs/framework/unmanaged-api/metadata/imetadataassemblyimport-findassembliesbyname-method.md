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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b388dae0f109ff366f83c92de99b00b80bcc01a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108722"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName — Metoda
Pobiera tablicę elementów zestawów z określonym `szAssemblyName` parametru, przy użyciu standardowych zasad stosowanych przez środowisko uruchomieniowe języka wspólnego (CLR) do rozpoznawania odwołań.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Katalog główny, w których należy szukać w danym zestawie. Jeśli ta wartość jest równa `null`, `FindAssembliesByName` będzie szukać tylko w globalnej pamięci podręcznej zestawów.  
  
 `szPrivateBin`  
 [in] Lista Rozdzielana średnikami (na przykład "bin; bin2"), zestawu podkatalogów w katalogu głównym, w których należy szukać zestawu. Te katalogi są sondowany oprócz tych określonych w domyślnych sondowania zasad.  
  
 `szAssemblyName`  
 [in] Nazwa zestawu, aby znaleźć. Format ten ciąg jest zdefiniowany w stronie dokumentacji klasy <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] Tablica typu [IUnknown](/cpp/atl/iunknown) w której chcesz umieścić `IMetadataAssemblyImport` wskaźniki interfejsu.  
  
 `cMax`  
 [out] Maksymalna liczba wskaźniki interfejsu, które mogą być umieszczane w `ppIUnk`.  
  
 `pcAssemblies`  
 [out] Zwrócono liczbę wskaźniki interfejsu. Oznacza to, że numer wskaźniki interfejsu faktycznie umieszczonych w `ppIUnk`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` pomyślnie zwrócił.|  
|`S_FALSE`|Nie ma żadnych zestawów.|  
  
## <a name="remarks"></a>Uwagi  
 Podana nazwa zestawu, `FindAssembliesByName` metoda znajdzie zestawu, wykonując standardowe reguły rozpoznawania odwołań do zestawów. (Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umożliwia obiektowi wywołującemu skonfigurować różne aspekty kontekstu mechanizm rozpoznawania zestawów, takich jak ścieżki wyszukiwania podstawowego i prywatne aplikacji.  
  
 `FindAssembliesByName` Metoda wymaga środowiska CLR do zainicjowania procesu w celu wywołania logiki rozpoznawania zestawu. W związku z tym, należy wywołać [coinitializeee —](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (przekazywanie COINITEE_DEFAULT) przed wywołaniem `FindAssembliesByName`, a następnie postępuj zgodnie z wywołaniem [couninitializecor —](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` Zwraca [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wskaźnika do pliku zawierającego manifest zestawu dla nazwy zestawu, który jest przekazywany w. Jeśli nazwa danego zestawu nie jest w pełni określona (na przykład, jeśli nie ma wersji), może zostać zwrócona wiele zestawów.  
  
 `FindAssembliesByName` najczęściej jest używana przez kompilator, który próbuje odnaleźć przywoływanego zestawu w czasie kompilacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
