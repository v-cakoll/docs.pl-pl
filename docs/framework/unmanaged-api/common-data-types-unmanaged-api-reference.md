---
title: Standardowe typy danych (niezarządzana dokumentacja interfejsu API)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b56840ce68caa3eed50773668c64e2622a646ddf
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892078"
---
# <a name="common-data-types-unmanaged-api-reference"></a>Standardowe typy danych (niezarządzana dokumentacja interfejsu API)
W tym temacie wymieniono proste typy danych używane przez niezarządzane interfejsy API dla .NET Framework, które są zdefiniowane przezC++ `typedef` instrukcje C/. Te typy danych są zwykle aliasami dla typówC++ danych C/pierwotnych. Zazwyczaj wartości tych typów danych są nieprzezroczyste; oznacza to, że są zwracane przez określoną funkcję lub metodę, aby można je było przekazywać do innych funkcji lub metod bez modyfikacji.  
  
|Typ danych|Definicja|Zdefiniowane w|Opis|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|Identyfikator domeny aplikacji.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|Identyfikator zestawu.|  
|Identyfikator ClassID|`typedef UINT_PTR ClassID;`|corprof.h|Identyfikator klasy zarządzanej.|  
|CLRDATA_ADDRESS|`typedef ULONG64 CLRDATA_ADDRESS;`|clrdata.h|64-bitowy adres pamięci.|
|CLRDATA_ENUM|`typedef ULONG64 CLRDATA_ADDRESS;`|Niedostępne|64-bitowy adres pamięci.|
|IDENTYFIKATOR POŁĄCZENIA|`typedef DWORD CONNID;`|CorDebug. h, mscoree. h|Identyfikator połączenia dla wątku, który jest połączony z wystąpieniem Microsoft SQL Server.|  
|Identyfikator ContextId|`typedef UINT_PTR ContextID;`|corprof.h|Identyfikator kontekstu skojarzonego z określonym zarządzanym wątkiem.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Nieprzezroczyste dojście, które reprezentuje informacje o określonej ramce stosu.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Nieprzezroczysty uchwyt, który wskazuje ramkę stosu. Jest on prawidłowy tylko w przypadku wywołania zwrotnego, do którego zostało przesłane.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Adres w pamięci.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|Stan kontynuacji.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|Wartość rejestru procesora CPU.|
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|Identyfikator funkcji lub metody.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Dojście do wyrzucania elementów bezużytecznych.|  
|mdMethodDef|`typedef mdToken mdMethodDef;`|cordebug.h|Token definicji metody.|
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Token metadanych (wiersz w tabeli metadanych).|  
|ModuleID|`typedef UINT_PTR ModuleID;`|corprof.h|Identyfikator modułu zestawu.|  
|Obiektu|`typedef UINT_PTR ObjectID;`|corprof.h|Identyfikator obiektu.|  
|PCCOR_SIGNATURE|`typedef SIZE_T PCCOR_SIGNATURE;`|cordebug.h|Wskaźnik do elementu członkowskiego lub sygnatury metadanych.|
|ProcessId|`typedef UINT_PTR ProcessID;`|corprof.h|Identyfikator procesu zarządzanego.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Identyfikator funkcji trybie JIT.|  
|SIZE_T|`typedef ULONG_PTR SIZE_T;`|CorSym. h|Wskaźnik do 64-bitowego adresu pamięci.|
|TASKID|`typedef UINT64 TASKID;`|CorDebug. h, mscoree. h|Identyfikator wystąpienia [ICLRTask](../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .|  
|ThreadID|`typedef UINT_PTR ThreadID;`|corprof.h|Identyfikator wątku zarządzanego.|  
  
## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API — informacje](../../../docs/framework/unmanaged-api/index.md)
