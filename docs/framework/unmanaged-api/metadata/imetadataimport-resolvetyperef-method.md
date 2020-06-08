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
ms.openlocfilehash: f55af87e21b48430807166cb03e1d41271e830a1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503446"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef — Metoda
Rozwiązuje <xref:System.Type> odwołanie reprezentowane przez określony token elementu TypeRef.  
  
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
 podczas Identyfikator IID interfejsu do zwrócenia `ppIScope` . Zwykle IID_IMetaDataImport.  
  
 `ppIScope`  
 określoną Interfejs do zakresu modułu, w którym jest zdefiniowany typ, do którego istnieje odwołanie.  
  
 `ptd`  
 określoną Wskaźnik do tokenu TypeDef, który reprezentuje przywoływany typ.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Nie należy używać tej metody w przypadku ładowania wielu domen aplikacji. Metoda nie uwzględnia granic domeny aplikacji. Jeśli wiele wersji zestawu jest załadowanych i zawierają ten sam typ z tą samą przestrzenią nazw, metoda zwraca zakres modułu pierwszego znalezionego typu.  
  
 `ResolveTypeRef`Metoda wyszukuje definicję typu w innych modułach. Jeśli zostanie znaleziona definicja typu, `ResolveTypeRef` zwraca interfejs do tego zakresu modułu, a także token typedef dla tego typu.  
  
 Jeśli odwołanie do typu, które ma zostać rozpoznane, ma zakres rozwiązań elementu AssemblyRef, `ResolveTypeRef` Metoda wyszukuje dopasowanie tylko w zakresach metadanych, które zostały już otwarte z wywołaniami metody [IMetaDataDispenser:: OpenScope —](imetadatadispenser-openscope-method.md) lub [IMetaDataDispenser:: OpenScopeOnMemory —](imetadatadispenser-openscopeonmemory-method.md) . Wynika to z faktu, że program `ResolveTypeRef` nie może ustalić tylko zakresu elementu AssemblyRef, gdzie na dysku lub w pamięci podręcznej zestawów globalnych jest przechowywany zestaw.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
