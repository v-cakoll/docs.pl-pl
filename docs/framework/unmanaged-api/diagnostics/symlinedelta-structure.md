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
ms.openlocfilehash: a1e83e4b8cb6603029f3b42b1a3b9ba4810c9039
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438014"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA — Struktura
Provides information to the symbol handler about methods that were moved as a result of edits.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`mdMethod`|The method's metadata token.|  
|`delta`|The number of lines the method was moved.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl  
  
## <a name="see-also"></a>Zobacz także

- [Struktury magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
