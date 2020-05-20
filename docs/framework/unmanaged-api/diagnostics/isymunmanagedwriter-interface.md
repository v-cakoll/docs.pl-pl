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
ms.openlocfilehash: 8f0bbd26bde562df5482d167c9d2775e01426f55
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610057"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter — Interfejs
Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Abort — Metoda](isymunmanagedwriter-abort-method.md)|Zamyka moduł zapisujący symboli bez przekazywania symboli do magazynu symboli.|  
|[Close — Metoda](isymunmanagedwriter-close-method.md)|Zamyka moduł zapisujący symboli po zatwierdzeniu symboli do magazynu symboli.|  
|[CloseMethod, metoda](isymunmanagedwriter-closemethod-method.md)|Zamyka bieżącą metodę. Po zamknięciu metody nie można definiować więcej symboli.|  
|[CloseNamespace, metoda](isymunmanagedwriter-closenamespace-method.md)|Zamyka ostatnio otwartą przestrzeń nazw.|  
|[CloseScope, metoda](isymunmanagedwriter-closescope-method.md)|Zamyka bieżący zakres leksykalny.|  
|[DefineConstant, metoda](isymunmanagedwriter-defineconstant-method.md)|Definiuje nazwę wartości stałej.|  
|[DefineDocument, metoda](isymunmanagedwriter-definedocument-method.md)|Definiuje dokument źródłowy.|  
|[DefineField — Metoda](isymunmanagedwriter-definefield-method.md)|Definiuje pojedynczą zmienną, która nie znajduje się w metodzie.|  
|[DefineGlobalVariable, metoda](isymunmanagedwriter-defineglobalvariable-method.md)|Definiuje pojedynczą zmienną globalną.|  
|[DefineLocalVariable, metoda](isymunmanagedwriter-definelocalvariable-method.md)|Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.|  
|[DefineParameter, metoda](isymunmanagedwriter-defineparameter-method.md)|Definiuje pojedynczy parametr w bieżącej metodzie.|  
|[DefineSequencePoints, metoda](isymunmanagedwriter-definesequencepoints-method.md)|Definiuje grupę punktów sekwencji w bieżącej metodzie.|  
|[GetDebugInfo, metoda](isymunmanagedwriter-getdebuginfo-method.md)|Zwraca informacje niezbędne do zapisania przez kompilator wpisu katalogu debugowania w nagłówku przenośnego pliku wykonywalnego (PE).|  
|[Initialize — Metoda](isymunmanagedwriter-initialize-method.md)|Ustawia interfejs emitujący metadane, z którym jest skojarzony ten składnik zapisywania i ustawia nazwę pliku wyjściowego, do którego będą zapisywane symbole debugowania.|  
|[Initialize2, metoda](isymunmanagedwriter-initialize2-method.md)|Ustawia interfejs emitujący metadane, z którym zostanie skojarzony ten składnik zapisywania, ustawia nazwę pliku wyjściowego, do którego będą zapisywane symbole debugowania, i ustawia ostateczną lokalizację pliku bazy danych programu (PDB).|  
|[OpenMethod, metoda](isymunmanagedwriter-openmethod-method.md)|Otwiera metodę, do której są emitowane informacje o symbolach.|  
|[OpenNamespace, metoda](isymunmanagedwriter-opennamespace-method.md)|Otwiera nową przestrzeń nazw.|  
|[OpenScope — Metoda](isymunmanagedwriter-openscope-method.md)|Otwiera nowy zakres leksykalny w bieżącej metodzie.|  
|[RemapToken, metoda](isymunmanagedwriter-remaptoken-method.md)|Powiadamia moduł zapisujący symboli o tym, że token metadanych został ponownie zmapowany w miarę emitowania metadanych.|  
|[SetMethodSourceRange, metoda](isymunmanagedwriter-setmethodsourcerange-method.md)|Określa wartość rzeczywistą początkową i końcową metody w pliku źródłowym.|  
|[SetScopeRange, metoda](isymunmanagedwriter-setscoperange-method.md)|Definiuje zakres przesunięć dla określonego zakresu leksykalnego.|  
|[SetSymAttribute, metoda](isymunmanagedwriter-setsymattribute-method.md)|Definiuje atrybut niestandardowy na podstawie jego nazwy.|  
|[SetUserEntryPoint, metoda](isymunmanagedwriter-setuserentrypoint-method.md)|Określa metodę zdefiniowaną przez użytkownika, która jest punktem wejścia dla tego modułu.|  
|[UsingNamespace, metoda](isymunmanagedwriter-usingnamespace-method.md)|Określa, że dana w pełni kwalifikowana nazwa przestrzeni nazw jest używana w aktualnie otwartym zakresie leksykalnym.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 — Interfejs](isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 — Interfejs](isymunmanagedwriter3-interface.md)
