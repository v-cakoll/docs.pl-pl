---
title: "ISymUnmanagedWriter — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter
helpviewer_keywords: ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4996f0196df4c2bcf890df6ad972f313403e435
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter — Interfejs
Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Abort, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Zamyka twórcę symbolu bez zatwierdzania symbole w magazynie symboli.|  
|[Close, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Zamyka twórcę symbol po zatwierdzania symbole w magazynie symboli.|  
|[CloseMethod, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Zamyka bieżącej metody. Po zamknięciu metody nie więcej symboli można zdefiniować w niej.|  
|[CloseNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Zamyka otwarty ostatnio przestrzeni nazw.|  
|[CloseScope, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Zamyka leksykalne bieżącego zakresu.|  
|[DefineConstant, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Definiuje nazwę wartości stałej.|  
|[DefineDocument, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Definiuje dokumentu źródłowego.|  
|[DefineField, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Definiuje pojedynczą zmienną, która nie jest w metodzie.|  
|[DefineGlobalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Definiuje pojedynczą zmienną globalnego.|  
|[DefineLocalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|Definiuje pojedynczą zmienną w bieżącym zakresie leksykalne.|  
|[DefineParameter, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Określa pojedynczy parametr w bieżącej metodzie.|  
|[DefineSequencePoints, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Definiuje grupę punkty sekwencji w bieżącej metodzie.|  
|[GetDebugInfo, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Zwraca informacje niezbędne do kompilatora, aby zapisać wpis katalogu debugowania w przenośnych nagłówka pliku wykonywalnego (PE).|  
|[Initialize, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Ustawienie interfejsu nadajnika metadanych, z którą ten moduł zapisujący zostanie skojarzony, a nazwa pliku wyjściowego, na którym zostanie zapisany symbole debugowania.|  
|[Initialize2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Ustawia interfejsu nadajnika metadanych, z którą ten moduł zapisujący zostanie skojarzony, ustawia nazwę pliku wyjściowego, do której zostanie zapisany symbole debugowania, a ustawia ostatecznej lokalizacji pliku programu (PDB) bazy danych.|  
|[OpenMethod, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Zostanie otwarty w którym symbol informacje są emitowane metody.|  
|[OpenNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Zostanie otwarty nowy obszar nazw.|  
|[OpenScope, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Zostanie otwarty nowy zakres leksykalne w bieżącej metodzie.|  
|[RemapToken, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Powiadamia twórcę symbolu, że token metadanych ma przeprowadzono ponowne mapowanie udziałów jak metadanych zostały wyemitowane.|  
|[SetMethodSourceRange, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Określa wartość true, początek i koniec metody w pliku źródłowym.|  
|[SetScopeRange, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Definiuje zakres przesunięcia dla określonego zakresu leksykalne.|  
|[SetSymAttribute, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Definiuje atrybut niestandardowy ustalane na podstawie jego nazwy.|  
|[SetUserEntryPoint, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Określa metodę zdefiniowane przez użytkownika, który jest punkt wejścia dla tego modułu.|  
|[UsingNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Określa, że podana nazwa przestrzeni nazw FQDN jest w użyciu w zakresie leksykalne aktualnie otwarte.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [ISymUnmanagedWriter3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
