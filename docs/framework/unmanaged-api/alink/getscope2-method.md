---
title: GetScope2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 40df78cdf99c2e0f53be9664f3f5c6386b6c6f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179396"
---
# <a name="getscope2-method"></a>GetScope2 — Metoda
Pobiera zakres importu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu docelowego.  
  
 `FileToken`  
 Identyfikator pliku, z którego ma być importowany.  
  
 `dwScope`  
 Zakres od zera do zaimportowania.  
  
 `ppImportScope`  
 Odbiera wskaźnik do interfejsu [IMetaDataImport2](../metadata/imetadataimport2-interface.md) dla wskazanego zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda powiedzie się.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h.  
  
## <a name="see-also"></a>Zobacz też

- [IALink2, interfejs](ialink2-interface.md)
- [IALink, interfejs](ialink-interface.md)
- [ALink, interfejs API](index.md)
