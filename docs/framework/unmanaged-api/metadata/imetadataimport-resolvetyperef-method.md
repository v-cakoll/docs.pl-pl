---
title: IMetaDataImport::ResolveTypeRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f323e91e60c9735a51e955eaab6673ca167f294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951877"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef — Metoda
<xref:System.Type> Rozwiązuje odwołanie reprezentowane przez określony token elementu TypeRef.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tr`  
 podczas Token metadanych elementu TypeRef, który ma zwracać informacje o typie, do którego się odwołuje.  
  
 `riid`  
 podczas Identyfikator IID interfejsu do zwrócenia `ppIScope`. Zwykle jest to IID_IMetaDataImport.  
  
 `ppIScope`  
 określoną Interfejs do zakresu modułu, w którym jest zdefiniowany typ, do którego istnieje odwołanie.  
  
 `ptd`  
 określoną Wskaźnik do tokenu TypeDef, który reprezentuje przywoływany typ.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Nie należy używać tej metody w przypadku ładowania wielu domen aplikacji. Metoda nie uwzględnia granic domeny aplikacji. Jeśli wiele wersji zestawu jest załadowanych i zawierają ten sam typ z tą samą przestrzenią nazw, metoda zwraca zakres modułu pierwszego znalezionego typu.  
  
 `ResolveTypeRef` Metoda wyszukuje definicję typu w innych modułach. Jeśli zostanie znaleziona definicja typu, `ResolveTypeRef` zwraca interfejs do tego zakresu modułu, a także token typedef dla tego typu.  
  
 Jeśli odwołanie do typu, które ma zostać rozpoznane, ma zakres rozwiązań elementu AssemblyRef `ResolveTypeRef` , Metoda wyszukuje dopasowanie tylko w zakresach metadanych, które zostały już otwarte z wywołaniami metody [IMetaDataDispenser:: OpenScope —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) lub [ IMetaDataDispenser:: OpenScopeOnMemory —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) , metoda. Wynika to z `ResolveTypeRef` faktu, że program nie może ustalić tylko zakresu elementu AssemblyRef, gdzie na dysku lub w pamięci podręcznej zestawów globalnych jest przechowywany zestaw.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** Cor. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
