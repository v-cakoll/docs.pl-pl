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
ms.openlocfilehash: 2f66d34fcfdd8c61dcc92817ec1a928ac5b603fc
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008901"
---
# <a name="iceegenaddsectionreloc-method"></a>ICeeGen::AddSectionReloc — Metoda
Dodaje instrukcję. reloc do bazy kodu.  
  
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
 podczas Sekcja kodu w pamięci, do której ma zostać dodana Instrukcja. reloc.  
  
 `offset`  
 podczas Przesunięcie sekcji.  
  
 `relativeTo`  
 podczas Sekcja, do której `offset` odwołuje się.  
  
 `relocType`  
 podczas Jedna z wartości [CeeSectionRelocType —](ceesectionreloctype-enumeration.md) , wskazując rodzaj instrukcji. reloc, która ma zostać dodana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICeeGen — Interfejs](iceegen-interface.md)
