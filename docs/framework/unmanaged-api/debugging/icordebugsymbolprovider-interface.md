---
title: Interfejs ICorDebugSymbolProvider
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e9f475ee3c46b8abb94ce7f804cc8b4a8054ec2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423211"
---
# <a name="icordebugsymbolprovider-interface"></a>Interfejs ICorDebugSymbolProvider
Udostępnia metody, które mogą służyć do pobierania informacji o symbolach debugowania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAssemblyImageBytes, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|Odczytuje dane z zestawu scalonych podany wirtualny adres względny (RVA) w zestawie scalone.|  
|[GetAssemblyImageMetadata, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Zwraca metadane z zestawu scalone.|  
|[GetCodeRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|Pobiera adres początkowy — metoda i rozmiar podany wirtualny adres względny (RVA) w metodzie.|  
|[GetInstanceFieldSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|Pobiera wystąpienie symboli pola, które odpowiadają podpis elementu typespec.|  
|[GetMergedAssemblyRecords, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Pobiera rekordy symboli scalone zestawy.|  
|[GetMethodLocalSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Pobiera symbole lokalne metody podany wirtualny adres względny (RVA) tej metody.|  
|[GetMethodParameterSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|Pobiera symbole parametru metody podany wirtualny adres względny (RVA) tej metody.|  
|[GetMethodProps, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|Zwraca informacje o właściwości metody, takie jak token metadanych oraz informacje o jego parametrów ogólnych — metoda podany wirtualny adres względny (RVA) w tej metody.|  
|[GetObjectSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|Zwraca rozmiar obiektu dla obiektu, w oparciu o jego sygnatura elementu typespec.|  
|[GetStaticFieldSymbols, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|Pobiera symbole statycznego pola, które odpowiadają podpis elementu typespec.|  
|[GetTypeProps, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|Zwraca informacje dotyczące typu właściwości, takie jak liczba podpisu jego parametry ogólne, podany wirtualny adres względny (RVA) w vtable.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs jest tylko dostępne z platformą .NET Native. W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
