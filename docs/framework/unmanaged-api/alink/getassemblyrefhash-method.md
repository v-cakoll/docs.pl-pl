---
title: GetAssemblyRefHash — Metoda
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d19eebaa3aa0ebb6f9807f0cf277b7ed6183c148
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777192"
---
# <a name="getassemblyrefhash-method"></a>GetAssemblyRefHash — Metoda
Pobiera obiekt BLOB mieszania dla danego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `FileToken`  
 Identyfikator zestawu, do którego odwołuje się skrót.  
  
 `ppvHash`  
 Odbiera wynikowy obiekt BLOB.  
  
 `pcbHash`  
 Odbiera rozmiar, w bajtach, obiektu BLOB mieszania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
