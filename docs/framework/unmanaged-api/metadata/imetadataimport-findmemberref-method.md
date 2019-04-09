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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abbd35fe390cc09951b762a5fd671d2d34a57c6c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177895"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef — Metoda
Pobiera wskaźnik do elementu członkowskiego tokenu MemberRef odwołanie to znaczy ujętego w określonym <xref:System.Type> i ma określoną sygnaturą nazwy i metadane.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Token TypeRef dla klasy lub interfejsu, który zawiera odwołania do składowej do wyszukania. Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane na potrzeby zmienną globalną lub odwołanie do globalnych funkcji.  
  
 `szName`  
 [in] Nazwa odwołania do składowej do wyszukania.  
  
 `pvSigBlob`  
 [in] Wskaźnik do podpisu metadanych binarne odwołania do składowej.  
  
 `cbSigBlob`  
 [in] Rozmiar w bajtach `pvSigBlob`.  
  
 `pmr`  
 [out] Wskaźnik do zgodnego tokenu MemberRef.  
  
## <a name="remarks"></a>Uwagi  
 Określ element członkowski przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwę (`szName`) i opcjonalnie jeho signatura (`pvSigBlob`).  
  
 Podpis jest przekazywany do `FindMemberRef` musi zostać wygenerowane w bieżącym zakresie ponieważ podpisy są powiązane z określonego zakresu. Podpis można osadzić token, który identyfikuje typ otaczający klasy lub wartości. Token jest to indeks w lokalnej tabeli TypeDef. Nie można tworzenia sygnatury czasu wykonywania poza kontekstem bieżącego zakresu i używać tego podpisu jako dane wejściowe `FindMemberRef`.  
  
 `FindMemberRef` Umożliwia znalezienie tylko odwołania do elementu członkowskiego, które zostały zdefiniowane bezpośrednio w klasę lub interfejs; nie odnajdzie odwołania dziedziczonego elementu członkowskiego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
