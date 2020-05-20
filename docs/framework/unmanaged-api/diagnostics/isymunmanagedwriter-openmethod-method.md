---
title: ISymUnmanagedWriter::OpenMethod — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: d2d16ab0a29fadd3a64d906a64fc46c422e01c45
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610044"
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod — Metoda
Otwiera metodę, do której są emitowane informacje o symbolach. Dana metoda jest bieżącą metodą dla wywołań definiujących punkty sekwencji, parametry i zakresy leksykalne. Istnieje niejawny zakres leksykalny wokół całej metody. Ponowne otwarcie wcześniej zamkniętej metody powoduje wymazanie wszystkich wcześniej zdefiniowanych symboli dla tej metody. W danym momencie może istnieć tylko jedna metoda Open.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a>Parametry  
 `method`  
 podczas Token metadanych dla metody, która ma zostać otwarta.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter — Interfejs](isymunmanagedwriter-interface.md)
- [CloseMethod, metoda](isymunmanagedwriter-closemethod-method.md)
- [OpenMethod2, metoda](isymunmanagedwriter3-openmethod2-method.md)
