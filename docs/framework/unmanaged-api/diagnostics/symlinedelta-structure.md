---
title: SYMLINEDELTA — Struktura
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609303"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA — Struktura
Zawiera informacje do obsługi symboli dotyczące metod, które zostały przeniesione w wyniku edycji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`mdMethod`|Token metadanych metody.|  
|`delta`|Liczba wierszy, które zostały przeniesione przez metodę.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl  
  
## <a name="see-also"></a>Zobacz także

- [Struktury magazynu symboli diagnostycznych](diagnostics-symbol-store-structures.md)
