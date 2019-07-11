---
title: IMetaDataImport::FindField — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1baee71b5b8575f51eb54fbc8a037a5dddd24500
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782523"
---
# <a name="imetadataimportfindfield-method"></a>IMetaDataImport::FindField — Metoda
Pobiera wskaźnik do FieldDef tokenu dla pola, który jest ujęty w określonym <xref:System.Type> i ma określoną sygnaturą nazwy i metadane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] Token element TypeDef dla klasy lub interfejsu, który otacza pole wyszukiwania. Jeśli ta wartość jest `mdTokenNil`, wyszukiwanie jest wykonywane dla zmiennej globalnej.  
  
 `szName`  
 [in] Nazwa pola do wyszukania.  
  
 `pvSigBlob`  
 [in] Wskaźnik do podpisu metadanych binarne pola.  
  
 `cbSigBlob`  
 [in] Rozmiar w bajtach `pvSigBlob`.  
  
 `pmb`  
 [out] Wskaźnik do zgodnego tokenu FieldDef.  
  
## <a name="remarks"></a>Uwagi  
 Określ pola przy użyciu jego otaczającej klasy lub interfejsu (`td`), jego nazwę (`szName`) i opcjonalnie jeho signatura (`pvSigBlob`).  
  
 Podpis jest przekazywany do `FindField` musi zostać wygenerowane w bieżącym zakresie ponieważ podpisy są powiązane z określonego zakresu. Podpis można osadzić token, który identyfikuje typ otaczający klasy lub wartości. (Token jest to indeks w lokalnej tabeli TypeDef). Nie można tworzenia sygnatury czasu wykonywania poza kontekstem bieżącego zakresu i używać tego podpisu jako dane wejściowe `FindField`.  
  
 `FindField` Umożliwia znalezienie tylko pola, które zostały zdefiniowane bezpośrednio klasę lub interfejs; nie odnajdzie odziedziczonego pola.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
