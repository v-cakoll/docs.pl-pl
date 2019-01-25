---
title: ICorDebugSymbolProvider, interfejs
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b588ec9dffcc4e759b40c7c472f48ab325167943
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660882"
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider, interfejs
Udostępnia metody, które mogą służyć do pobierania informacji dotyczących symboli debugowania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAssemblyImageBytes, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|Odczytuje dane z zestawu scalonych podane względnych adresów wirtualnych (RVA) w zestawie scalone.|  
|[GetAssemblyImageMetadata, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Zwraca metadane z zestawu scalonych.|  
|[GetCodeRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|Pobiera adres początkowy metody i biorąc względnych adresów wirtualnych (RVA) w metodzie.|  
|[GetInstanceFieldSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|Pobiera wystąpienie symboli pola, które odpowiadają podpisu elementu typespec.|  
|[GetMergedAssemblyRecords, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Pobiera rekordy symboli dla wszystkich zestawów scalone.|  
|[GetMethodLocalSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Pobiera symbole lokalne metody podany wirtualny adres względny (RVA) tej metody.|  
|[GetMethodParameterSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|Pobiera symbole parametru metody podany wirtualny adres względny (RVA) tej metody.|  
|[GetMethodProps, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|Zwraca informacje o właściwości metody, takie jak metody token metadanych oraz informacje o jego parametrów ogólnych, biorąc pod uwagę względnych adresów wirtualnych (RVA) w tej metodzie.|  
|[GetObjectSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|Zwraca rozmiar obiektu dla obiektu, w oparciu o jego podpisu elementu typespec.|  
|[GetStaticFieldSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|Pobiera symbole pole statyczne, które odpowiadają podpisu elementu typespec.|  
|[GetTypeProps, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|Zwraca informacje o właściwościach typu, takie jak liczba podpisu parametrami rodzajowymi, rozpoczynając od podanej względnych adresów wirtualnych (RVA) w vtable.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs jest tylko dostępne z architekturą .NET Native. W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
