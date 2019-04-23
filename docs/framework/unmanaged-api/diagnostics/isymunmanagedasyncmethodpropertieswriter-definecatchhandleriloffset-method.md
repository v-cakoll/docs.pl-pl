---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 923c85a9dff11753a338fcfd3673d3590fca607a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196752"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda
Ustawia IL przesunięcie obsługi catch generowanych przez kompilator, który otacza metody asynchronicznej.  
  
 Przesunięcie IL wygenerowanego catch jest używany przez debuger do obsługi catch, tak jakby był on niebędący kodem użytkownika, mimo że może wystąpić w metodzie kodu użytkownika. W szczególności jest używany w odpowiedzi na **CatchHandlerFound** zdarzenie wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedAsyncMethodPropertiesWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
