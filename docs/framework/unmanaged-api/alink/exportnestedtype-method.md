---
title: ExportNestedType — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179411"
---
# <a name="exportnestedtype-method"></a>ExportNestedType — Metoda
Określa typy zagnieżdżone jako możliwe do wyeksportowania. Metoda [ExportType](exporttype-method.md) można również eksportować zagnieżdżone typy, ale ta metoda jest szybsza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu do wyeksportowania.  
  
 `FileToken`  
 Token pliku lub montaż pliku, który definiuje typ, który ma być eksportowany.  
  
 `TypeToken`  
 Typ tokenu typu, który ma być eksportowany.  
  
 `ParentType`  
 Token typu nadrzędnego.  
  
 `pszTypename`  
 W pełni kwalifikowana nazwa typu do wyeksportowania.  
  
 `dwFlags`  
 `ComType`flagi, `tdPublic` takie `tdNested`jak lub . Ta wartość może zostać przekazana do [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Odbiera token dla eksportowanego typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda powiedzie się.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz też

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
