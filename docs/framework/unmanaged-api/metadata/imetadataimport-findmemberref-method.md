---
title: IMetaDataImport::FindMemberRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175424"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef — Metoda
Pobiera wskaźnik do tokenu MemberRef dla odwołania elementu członkowskiego, który jest ujęty przez określony <xref:System.Type> i który ma określoną nazwę i podpis metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [w] TypeRef token dla klasy lub interfejsu, który otacza odwołanie do elementu członkowskiego do wyszukiwania. Jeśli ta `mdTokenNil`wartość jest , wyszukiwanie jest wykonywane dla zmiennej globalnej lub odwołania funkcji globalnej.  
  
 `szName`  
 [w] Nazwa odwołania elementu członkowskiego do wyszukania.  
  
 `pvSigBlob`  
 [w] Wskaźnik do podpisu binarnych metadanych odwołania elementu członkowskiego.  
  
 `cbSigBlob`  
 [w] Rozmiar w bajtach . `pvSigBlob`  
  
 `pmr`  
 [na zewnątrz] Wskaźnik do pasującego tokenu MemberRef.  
  
## <a name="remarks"></a>Uwagi  
 Element członkowski można określić za`td`pomocą otaczającej`szName`go klasy lub`pvSigBlob`interfejsu ( ), jego nazwy ( i opcjonalnie jego podpisu ( ).  
  
 Podpis przekazany `FindMemberRef` do musi zostały wygenerowane w bieżącym zakresie, ponieważ podpisy są powiązane z określonym zakresem. Podpis można osadzić token, który identyfikuje otaczającą klasę lub typ wartości. Token jest indeksem do lokalnej tabeli TypeDef. Nie można utworzyć podpisu w czasie wykonywania poza kontekstem bieżącego `FindMemberRef`zakresu i użyć tego podpisu jako danych wejściowych do .  
  
 `FindMemberRef`znajduje tylko odwołania do elementów członkowskich, które zostały zdefiniowane bezpośrednio w klasie lub interfejsie; nie znajduje dziedziczonych odwołań do elementów członkowskich.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
