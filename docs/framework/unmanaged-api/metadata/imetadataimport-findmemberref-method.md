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
ms.openlocfilehash: c3736d604b7e77028a2b99d462d88ae207df926c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448026"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef — Metoda
Pobiera wskaźnik do elementu członkowskiego tokenu MemberRef oznacza to odwołanie ujęty w określonym <xref:System.Type> z określoną sygnaturą nazwy i metadanych.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [in] Token TypeRef dla klasy lub interfejsu, który umieszcza odwołanie do elementu członkowskiego do wyszukania. Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane na potrzeby zmiennej globalnej lub odwołanie do funkcji globalnej.  
  
 `szName`  
 [in] Nazwa odwołania do elementu członkowskiego do wyszukania.  
  
 `pvSigBlob`  
 [in] Wskaźnik do sygnatury binarne metadanych odwołania do elementu członkowskiego.  
  
 `cbSigBlob`  
 [in] Wyrażony w bajtach rozmiar `pvSigBlob`.  
  
 `pmr`  
 [out] Wskaźnik do dopasowania tokenu MemberRef.  
  
## <a name="remarks"></a>Uwagi  
 Określ element członkowski za pomocą jego otaczającej klasy lub interfejsu (`td`), jego nazwa (`szName`) i opcjonalnie jego podpis (`pvSigBlob`).  
  
 Podpis przekazany do `FindMemberRef` musi został wygenerowany w bieżącym zakresie, ponieważ podpisy są powiązane z określonego zakresu. Podpis osadzić token, który identyfikuje typ otaczający klasy lub wartości. Token jest indeks do lokalnej tabeli TypeDef. Nie kompilacji podpisu środowiska wykonawczego poza kontekstem bieżącego zakresu i używają tego podpisu jako dane wejściowe `FindMemberRef`.  
  
 `FindMemberRef` Wyszukuje tylko odwołania do elementu członkowskiego zdefiniowane bezpośrednio w klasy lub interfejsu; dziedziczony element członkowski odwołania nie zostanie znaleziona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
