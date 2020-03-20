---
title: StrongNameFreeBuffer — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: 50e3cc6e677de45be9256a2a818ebd6ed7d8b843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176919"
---
# <a name="strongnamefreebuffer-function"></a>StrongNameFreeBuffer — Funkcja
Zwalnia pamięć, która została przydzielona przy poprzednim wywołaniu funkcji silnej nazwy, takiej jak [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)lub [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).  
  
 Ta funkcja została przestarzała. Zamiast tego należy użyć metody [ICLRStrongName::StrongNameFreeBuffer.](../hosting/iclrstrongname-strongnamefreebuffer-method.md)  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbMemory`  
 [w] Wskaźnik do pamięci, aby zwolnić.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h (Nazwa siła)-h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameFreeBuffer, metoda](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
