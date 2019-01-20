---
title: Standardowe typy danych (niezarządzana dokumentacja interfejsu API)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0d3a9039c6dc5d72ca740d6eaaf8a4d565e2647
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415276"
---
# <a name="common-data-types-unmanaged-api-reference"></a>Standardowe typy danych (niezarządzana dokumentacja interfejsu API)
W tym temacie przedstawiono typy proste dane używane przez niezarządzanych interfejsów API programu .NET Framework, które są definiowane przez C/C++ `typedef` instrukcji. Te typy danych są zazwyczaj aliasy dla języka C/C++ pierwotne typy danych. Zazwyczaj są nieprzezroczyste; wartości z tych typów danych oznacza to są zwracane przez konkretną funkcję lub metodę, aby może być przekazywany do innych funkcji lub metody bez żadnych modyfikacji.  
  
|Typ danych|Definicja|Zdefiniowane w|Opis|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|Identyfikator domeny aplikacji.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|Identyfikator zestawu.|  
|ClassID|`typedef UINT_PTR ClassID;`|corprof.h|Identyfikator klasy zarządzanej.|
|CLRDATA_ENUM|`typedef ULONG64 CLRDATA_ADDRESS;`|Nie jest dostępna|Adres pamięci 64-bitowych.|
|CONNID|`typedef DWORD CONNID;`|cordebug.h, mscoree.h|Identyfikator połączenia dla wątku, który jest podłączony do wystąpienia programu Microsoft SQL Server.|  
|Identyfikator kontekstu|`typedef UINT_PTR ContextID;`|corprof.h|Identyfikator kontekstu skojarzonego z określonym wątków zarządzanych.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Dojście nieprzezroczyste reprezentujący informacji na temat ramki określonego stosu.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Nieprzezroczystego obsługiwać odwołujący się do ramki stosu. Jest on prawidłowy tylko podczas wywołania zwrotnego, do którego jest przekazywany.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Adres w pamięci.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|Stan kontynuacji.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|Wartość rejestru procesora CPU.|
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|Identyfikator funkcji lub metody.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Uchwyt kolekcji wyrzucania elementów.|  
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Token metadanych (wiersz w tabeli metadanych).|  
|ModuleID|`typedef UINT_PTR ModuleID;`|corprof.h|Identyfikator modułu zestawu.|  
|ObjectID|`typedef UINT_PTR ObjectID;`|corprof.h|Identyfikator obiektu.|  
|ProcessId|`typedef UINT_PTR ProcessID;`|corprof.h|Identyfikator procesu zarządzanego.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Identyfikator funkcji w trybie JIT.|  
|IDENTYFIKATOR ZADANIA:|`typedef UINT64 TASKID;`|cordebug.h, mscoree.h|Identyfikator [iclrtask —](../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia.|  
|ThreadID|`typedef UINT_PTR ThreadID;`|corprof.h|Identyfikator wątków zarządzanych.|  
  
## <a name="see-also"></a>Zobacz też  
- [Niezarządzane interfejsy API — informacje](../../../docs/framework/unmanaged-api/index.md)
