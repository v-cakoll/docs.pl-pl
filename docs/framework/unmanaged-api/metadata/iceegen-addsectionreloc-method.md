---
title: ICeeGen::AddSectionReloc — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176113"
---
# <a name="iceegenaddsectionreloc-method"></a>ICeeGen::AddSectionReloc — Metoda
Dodaje instrukcję .reloc do podstawy kodu.  
  
 Ta metoda jest przestarzała i nie powinna być używana.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `section`  
 [w] Sekcja kodu w pamięci, do której należy dodać instrukcję .reloc.  
  
 `offset`  
 [w] Przesunięcie sekcji.  
  
 `relativeTo`  
 [w] Sekcja, do `offset` której się odnosi.  
  
 `relocType`  
 [w] Jedna z wartości [CeeSectionRelocType,](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) wskazująca rodzaj instrukcji .reloc, aby dodać.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICeeGen — Interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
