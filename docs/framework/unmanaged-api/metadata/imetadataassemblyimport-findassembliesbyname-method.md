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
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177799"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName — Metoda
Pobiera tablicę zestawów z `szAssemblyName` określonym parametrem, przy użyciu standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego (CLR) do rozpoznawania odwołań.  
  
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
 [w] Katalog główny, w którym ma być wyszukiwany dany zestaw. Jeśli ta wartość `null`jest `FindAssembliesByName` ustawiona na , będzie wyglądać tylko w globalnej pamięci podręcznej zestawów dla zestawu.  
  
 `szPrivateBin`  
 [w] Lista podkatalogów rozdzielanych średnikami (na przykład "bin;bin2"), w katalogu głównym, w którym ma być wyszukiwana zestaw. Katalogi te są badane oprócz tych określonych w domyślnych reguł sondowania.  
  
 `szAssemblyName`  
 [w] Nazwa zestawu do znalezienia. Format tego ciągu jest zdefiniowany na <xref:System.Reflection.AssemblyName>stronie odwołania do klasy dla programu .  
  
 `ppIUnk`  
 [w] Tablica typu [IUnknown,](/cpp/atl/iunknown) w `IMetadataAssemblyImport` którym można umieścić wskaźniki interfejsu.  
  
 `cMax`  
 [na zewnątrz] Maksymalna liczba wskaźników interfejsu, które `ppIUnk`można umieścić w pliku .  
  
 `pcAssemblies`  
 [na zewnątrz] Zwracana liczba wskaźników interfejsu. Oznacza to, że liczba wskaźników interfejsu `ppIUnk`faktycznie umieszczone w .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych zestawów.|  
  
## <a name="remarks"></a>Uwagi  
 Biorąc pod uwagę `FindAssembliesByName` nazwę zestawu, metoda znajduje zestaw, postępujący zgodnie ze standardowymi regułami rozpoznawania odwołań do zestawu. (Aby uzyskać więcej informacji, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umożliwia wywołującemu skonfigurowanie różnych aspektów kontekstu rozpoznawania nazw zestawu, takich jak baza aplikacji i prywatna ścieżka wyszukiwania.  
  
 Metoda `FindAssembliesByName` wymaga CLR do zainicjowania w procesie w celu wywołania logiki rozpoznawania zestawu. W związku z tym należy wywołać [CoInitializeEEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) `FindAssembliesByName`(przekazywanie COINITEE_DEFAULT) przed wywołaniem , a następnie wykonaj połączenie [z CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`zwraca wskaźnik [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) do pliku zawierającego manifest zestawu dla nazwy zestawu, który jest przekazywany. Jeśli dana nazwa zestawu nie jest w pełni określona (na przykład, jeśli nie zawiera wersji), może zostać zwróconych wiele zestawów.  
  
 `FindAssembliesByName`jest powszechnie używany przez kompilator, który próbuje znaleźć zestaw, do którego istnieje odwołanie w czasie kompilacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
