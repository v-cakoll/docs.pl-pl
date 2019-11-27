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
ms.openlocfilehash: fc19ee25e903046daef376e4297c8feb3d01ad47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427938"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter — Interfejs
Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Abort, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Zamyka moduł zapisujący symboli bez przekazywania symboli do magazynu symboli.|  
|[Close, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Zamyka moduł zapisujący symboli po zatwierdzeniu symboli do magazynu symboli.|  
|[CloseMethod, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Zamyka bieżącą metodę. Po zamknięciu metody nie można definiować więcej symboli.|  
|[CloseNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Zamyka ostatnio otwartą przestrzeń nazw.|  
|[CloseScope, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Zamyka bieżący zakres leksykalny.|  
|[DefineConstant, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Definiuje nazwę wartości stałej.|  
|[DefineDocument, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Definiuje dokument źródłowy.|  
|[DefineField, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Definiuje pojedynczą zmienną, która nie znajduje się w metodzie.|  
|[DefineGlobalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Definiuje pojedynczą zmienną globalną.|  
|[DefineLocalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.|  
|[DefineParameter, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Definiuje pojedynczy parametr w bieżącej metodzie.|  
|[DefineSequencePoints, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Definiuje grupę punktów sekwencji w bieżącej metodzie.|  
|[GetDebugInfo, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Zwraca informacje niezbędne do zapisania przez kompilator wpisu katalogu debugowania w nagłówku przenośnego pliku wykonywalnego (PE).|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Ustawia interfejs emitujący metadane, z którym jest skojarzony ten składnik zapisywania i ustawia nazwę pliku wyjściowego, do którego będą zapisywane symbole debugowania.|  
|[Initialize2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Ustawia interfejs emitujący metadane, z którym zostanie skojarzony ten składnik zapisywania, ustawia nazwę pliku wyjściowego, do którego będą zapisywane symbole debugowania, i ustawia ostateczną lokalizację pliku bazy danych programu (PDB).|  
|[OpenMethod, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Otwiera metodę, do której są emitowane informacje o symbolach.|  
|[OpenNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Otwiera nową przestrzeń nazw.|  
|[OpenScope, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Otwiera nowy zakres leksykalny w bieżącej metodzie.|  
|[RemapToken, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Powiadamia moduł zapisujący symboli o tym, że token metadanych został ponownie zmapowany w miarę emitowania metadanych.|  
|[SetMethodSourceRange, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Określa wartość rzeczywistą początkową i końcową metody w pliku źródłowym.|  
|[SetScopeRange, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Definiuje zakres przesunięć dla określonego zakresu leksykalnego.|  
|[SetSymAttribute, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Definiuje atrybut niestandardowy na podstawie jego nazwy.|  
|[SetUserEntryPoint, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Określa metodę zdefiniowaną przez użytkownika, która jest punktem wejścia dla tego modułu.|  
|[UsingNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Określa, że dana w pełni kwalifikowana nazwa przestrzeni nazw jest używana w aktualnie otwartym zakresie leksykalnym.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
