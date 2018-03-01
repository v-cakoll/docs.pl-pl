---
title: "IMetaDataImport::ResolveTypeRef — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64a783297b27c9d1400670eecb7dfe4cb69c2b96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef — Metoda
Usuwa <xref:System.Type> odwołanie reprezentowany przez określony token TypeRef.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tr`  
 [in] Token TypeRef metadanych do zwracania informacji typu występującego w odwołaniu do.  
  
 `riid`  
 [in] Uzyskanie identyfikatora IID interfejsu do zwrócenia w `ppIScope`. Zazwyczaj powinien to być IID_IMetaDataImport.  
  
 `ppIScope`  
 [out] Interfejs do zakresu modułu, w którym jest zdefiniowany typ, do którego istnieje odwołanie.  
  
 `ptd`  
 [out] Wskaźnik do TypeDef token, który reprezentuje typ do którego istnieje odwołanie.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Nie należy używać tej metody, jeśli są ładowane wielu domen aplikacji. Metoda nie przestrzega granice domeny aplikacji. Jeśli załadowano wiele wersji zestawu zawierają ten sam typ z tego samego obszaru nazw, metoda zwraca zakres modułu pierwszego typu, który odnajdzie.  
  
 `ResolveTypeRef` Metody wyszukiwania dla definicji typu w innych modułach. Jeśli zostanie znaleziony definicji typu, `ResolveTypeRef` zwraca interfejs do tego zakresu modułu, a także TypeDef token dla typu.  
  
 Jeśli odniesienie typu, które mają zostać rozwiązane, ma zakres rozpoznawania elementu AssemblyRef, `ResolveTypeRef` metoda szuka dopasowanie tylko w zakresach metadanych, które już zostały otwarte z wywołań albo [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)metody lub [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metody. Jest to spowodowane `ResolveTypeRef` nie można określić z tylko zakresu elementu AssemblyRef na dysku lub w pamięci podręcznej GAC zestawu przechowywania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
