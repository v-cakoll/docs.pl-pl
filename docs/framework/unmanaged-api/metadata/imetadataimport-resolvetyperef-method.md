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
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431474"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef — Metoda
Rozwiązuje odwołanie <xref:System.Type> reprezentowane przez określony token elementu TypeRef.  
  
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
 podczas Identyfikator IID interfejsu do zwrócenia w `ppIScope`. Zwykle IID_IMetaDataImport.  
  
 `ppIScope`  
 określoną Interfejs do zakresu modułu, w którym jest zdefiniowany typ, do którego istnieje odwołanie.  
  
 `ptd`  
 określoną Wskaźnik do tokenu TypeDef, który reprezentuje przywoływany typ.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Nie należy używać tej metody w przypadku ładowania wielu domen aplikacji. Metoda nie uwzględnia granic domeny aplikacji. Jeśli wiele wersji zestawu jest załadowanych i zawierają ten sam typ z tą samą przestrzenią nazw, metoda zwraca zakres modułu pierwszego znalezionego typu.  
  
 Metoda `ResolveTypeRef` wyszukuje definicję typu w innych modułach. Jeśli zostanie znaleziona definicja typu, `ResolveTypeRef` zwraca interfejs do tego zakresu modułu, a także token TypeDef dla tego typu.  
  
 Jeśli odwołanie do typu, które ma zostać rozpoznane, ma zakres rozwiązań elementu AssemblyRef, Metoda `ResolveTypeRef` wyszukuje dopasowanie tylko w zakresach metadanych, które zostały już otwarte z wywołaniami metody [IMetaDataDispenser:: OpenScope —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) lub [IMetaDataDispenser:: OpenScopeOnMemory —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) . Wynika to z faktu, że `ResolveTypeRef` nie może określać tylko elementu AssemblyRef zakresu, w którym znajduje się na dysku lub w globalnej pamięci podręcznej zestawów, który jest przechowywany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
