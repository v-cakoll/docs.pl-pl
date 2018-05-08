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
ms.openlocfilehash: a6c7bf332d829a440fe216756f7a23ec1277e6c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName — Metoda
Pobiera tablicę zestawy z określonym `szAssemblyName` parametr, przy użyciu standardowych zasad stosowanych przez środowisko uruchomieniowe języka wspólnego (CLR) do rozpoznawania odwołań.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `szAppBase`  
 [in] Katalog główny wyszukiwania dla danego zestawu. Jeśli ta wartość jest równa `null`, `FindAssembliesByName` będzie szukać tylko w pamięci podręcznej GAC zestawu.  
  
 `szPrivateBin`  
 [in] Lista Rozdzielana średnikami podkatalogi (na przykład "bin; pojemnik 2"), w obszarze katalogu głównego, w których będą poszukiwane zestawu. Te katalogi są sondowany oprócz tych określonych w domyślnym sondowanie zasad.  
  
 `szAssemblyName`  
 [in] Nazwa zestawu można znaleźć. Format ten ciąg jest zdefiniowany w odwołaniu klasy dla <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] Tablica typu <<!--zzxref:IUnknown --> `IUnknown`> w której chcesz umieścić `IMetadataAssemblyImport` wskaźniki interfejsu.  
  
 `cMax`  
 [out] Maksymalna liczba wskaźniki interfejsu, które można umieścić w `ppIUnk`.  
  
 `pcAssemblies`  
 [out] Zwrócono liczbę wskaźniki interfejsu. Oznacza to, że liczba wskaźniki interfejsu faktycznie umieszczonych w `ppIUnk`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` zwrócona pomyślnie.|  
|`S_FALSE`|Nie ma żadnych zestawów.|  
  
## <a name="remarks"></a>Uwagi  
 Podana nazwa zestawu `FindAssembliesByName` metoda znajdzie zestawu wykonując standardowych zasad rozpoznawania odwołań do zestawu. (Aby uzyskać więcej informacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` umożliwia obiekt wywołujący, aby skonfigurować różne aspekty kontekst rozpoznawania zestawu, takie jak ścieżka wyszukiwania podstawowego i prywatnych aplikacji.  
  
 `FindAssembliesByName` Metoda wymaga środowiska CLR do zainicjowania procesu w celu wywołania logiki rozpoznawania zestawu. W związku z tym należy wywołać [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (przekazywanie COINITEE_DEFAULT) przed wywołaniem `FindAssembliesByName`, a następnie postępuj zgodnie z wywołaniem do [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` Zwraca [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) wskaźnika do pliku zawierającego manifest zestawu dla nazwy zestawu, który jest przekazywany w. Jeśli podana nazwa zestawu nie określono pełni (na przykład, jeśli nie ma wersji), może być zwrócony wiele zestawów.  
  
 `FindAssembliesByName` to powszechnie używane przez kompilator, który próbuje odnaleźć przywoływanego zestawu w czasie kompilacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
