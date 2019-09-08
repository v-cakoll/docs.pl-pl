---
title: ExportTypeForwarder — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ae4ddd07a2a3d3ab9b5d024eceb43329db96915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787510"
---
# <a name="exporttypeforwarder-method"></a>ExportTypeForwarder — Metoda
Dodaje usługę przesyłania dalej typu do tabeli typów danego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `tkAssemblyRef`  
 Odwołanie do zestawu, do którego odwołuje się usługa przesyłania dalej typu.  
  
 `pszTypename`  
 W pełni kwalifikowana nazwa typu do eksportowania.  
  
 `dwFlags`  
 `ComType`flagi takie jak `tdPublic` lub `tdNested`. Ta wartość może zostać przeniesiona do [metody DefineExportedType —](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Odbiera token wyeksportowanego typu. Jest to konieczne tylko w przypadku emitowania typów zagnieżdżonych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
