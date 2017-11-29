---
title: "Standardowe typy danych (niezarządzana dokumentacja interfejsu API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03350825b3de4515a0d30e8644f34df71efa25db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="common-data-types-unmanaged-api-reference"></a>Standardowe typy danych (niezarządzana dokumentacja interfejsu API)
Ten temat zawiera listę typów proste danych używany przez niezarządzane interfejsy API programu .NET Framework, które są definiowane przez C/C++ `typedef` instrukcje. Te typy danych są zazwyczaj aliasów dla typów pierwotnych danych C/C++. Zazwyczaj wartości te typy danych są nieprzezroczyste; oznacza to, że są zwracane przez określonej funkcji lub metody, dzięki czemu mogą być przekazywane do innych funkcji lub metody bez żadnych modyfikacji.  
  
|Typ danych|Definicja|Zdefiniowany w|Opis|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|Identyfikator domeny aplikacji.|  
|Właściwość AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|Identyfikator zestawu.|  
|Identyfikator klasy|`typedef UINT_PTR ClassID;`|corprof.h|Identyfikator klasy zarządzanej.|  
|CONNID|`typedef DWORD CONNID;`|cordebug.h, mscoree.h|Identyfikator połączenia dla wątku, który jest podłączony do wystąpienia programu Microsoft SQL Server.|  
|Identyfikator kontekstu|`typedef UINT_PTR ContextID;`|corprof.h|Identyfikator kontekstu skojarzonego z konkretnym wątkiem zarządzanych.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Nieprzezroczystego uchwyt reprezentujący informacji na temat ramka stosu określonego.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Nieprzezroczyste obsługi się do ramki stosu. Jest on prawidłowy tylko w trakcie wywołania zwrotnego, do którego jest przekazywany.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Adres w pamięci.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|Stan kontynuacji.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|Wartość rejestru procesora CPU.|  
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|Identyfikator metody lub funkcji.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Uchwyt kolekcji pamięci.|  
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Token metadanych (wiersz w tabeli metadanych).|  
|ModuleID|`typedef UINT_PTR ModuleID;`|corprof.h|Identyfikator modułu zestawu.|  
|Identyfikator obiektu|`typedef UINT_PTR ObjectID;`|corprof.h|Identyfikator obiektu.|  
|Identyfikator procesu|`typedef UINT_PTR ProcessID;`|corprof.h|Identyfikator procesu zarządzanego.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Identyfikator funkcji skompilowanych w trybie JIT.|  
|TASKID|`typedef UINT64 TASKID;`|cordebug.h, mscoree.h|Identyfikator [ICLRTask](../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia.|  
|Identyfikator wątku|`typedef UINT_PTR ThreadID;`|corprof.h|Identyfikator zarządzanego wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Niezarządzany wykaz interfejsów API](../../../docs/framework/unmanaged-api/index.md)
