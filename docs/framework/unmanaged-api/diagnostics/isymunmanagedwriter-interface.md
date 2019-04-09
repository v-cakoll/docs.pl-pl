---
title: ISymUnmanagedWriter — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ac95cd5b79a2e1762fa9adf29d4d7926ab4ab7a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150585"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter — Interfejs
Reprezentuje edytor symboli i zapewnia metody do definiowania dokumentów, punktów sekwencji, leksykalne zakresy i zmienne.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Abort — Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Zamyka moduł zapisujący symboli nie poświęcając symbole do magazynu symboli.|  
|[Close — Metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Zamyka moduł zapisujący symbol po zatwierdzeniu symbole do magazynu symboli.|  
|[CloseMethod, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Zamyka bieżącą metodę. Po zamknięciu metody żadnych więcej symboli można zdefiniować w nim.|  
|[CloseNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Zamyka otwarty ostatnio przestrzeni nazw.|  
|[CloseScope, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Zamyka bieżący zakresie leksykalnym.|  
|[DefineConstant, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Definiuje nazwę wartości stałej.|  
|[DefineDocument, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Definiuje dokumentu źródłowego.|  
|[DefineField, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Definiuje pojedynczej zmiennej, która nie znajduje się w metody.|  
|[DefineGlobalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Definiuje jednej zmiennej globalnej.|  
|[DefineLocalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.|  
|[DefineParameter, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Definiuje pojedynczy parametr w bieżącej metodzie.|  
|[DefineSequencePoints, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Definiuje grupę punktów sekwencji w bieżącej metodzie.|  
|[GetDebugInfo, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Zwraca informacje niezbędne do kompilatora zapisać wpis katalogu debugowania w przenośnych nagłówka pliku wykonywalnego (PE).|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Ustawia interfejsu nadajnika metadanych, z którym ten moduł zapisujący zostanie skojarzona i ustawia nazwę pliku wyjściowego, do którego symbole debugowania zostaną zapisane.|  
|[Initialize2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Ustawia interfejsu nadajnika metadanych, z którym ten moduł zapisujący zostanie skojarzona, ustawia nazwę pliku wyjściowego, do którego symbole debugowania zostaną zapisane i ustawia ostatecznej lokalizacji pliku bazy danych (PDB) programu.|  
|[OpenMethod, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Zostanie otwarty metody, w której symbol informacje są emitowane.|  
|[OpenNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Zostanie otwarty nowy obszar nazw.|  
|[OpenScope, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Zostanie otwarty nowy zakres leksykalne w bieżącej metodzie.|  
|[RemapToken, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Powiadamia moduł zapisujący symboli, czy token metadanych ma został ponownie mapowany jako metadane zostały wyemitowane.|  
|[SetMethodSourceRange, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Określa wartość true, początek i koniec okresu metody w pliku źródłowym.|  
|[SetScopeRange, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Definiuje zakres przesunięcia dla określonego zakresu leksykalne.|  
|[SetSymAttribute, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Określa atrybut niestandardowy na podstawie jego nazwy.|  
|[SetUserEntryPoint, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Określa metodę zdefiniowanych przez użytkownika, który jest punktem wejścia dla tego modułu.|  
|[UsingNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Określa, że dany w pełni kwalifikowanej nazwy obszaru nazw jest używany w zakresie leksykalnym aktualnie otwarte.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
