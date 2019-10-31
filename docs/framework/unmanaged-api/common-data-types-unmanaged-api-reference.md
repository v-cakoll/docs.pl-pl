---
title: Standardowe typy danych (niezarządzana dokumentacja interfejsu API)
ms.date: 03/30/2017
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
ms.openlocfilehash: 86f3886b96d0156ec2f0431369c7a54954cd4cad
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132451"
---
# <a name="common-data-types-unmanaged-api-reference"></a>Standardowe typy danych (niezarządzana dokumentacja interfejsu API)
Ten temat zawiera listę prostych typów danych używanych przez niezarządzane interfejsy API dla .NET Framework zdefiniowanych przez instrukcje C/C++ `typedef`. Te typy danych są zwykle aliasami dla typówC++ danych C/pierwotnych. Zazwyczaj wartości tych typów danych są nieprzezroczyste; oznacza to, że są zwracane przez określoną funkcję lub metodę, aby można je było przekazywać do innych funkcji lub metod bez modyfikacji.  
  
|Typ danych|Definicja|Zdefiniowane w|Opis|  
|---------------|----------------|----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|CorProf. h|Identyfikator domeny aplikacji.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|CorProf. h|Identyfikator zestawu.|  
|Identyfikator ClassID|`typedef UINT_PTR ClassID;`|CorProf. h|Identyfikator klasy zarządzanej.|  
|CLRDATA_ADDRESS|`typedef ULONG64 CLRDATA_ADDRESS;`|ClrData. h|64-bitowy adres pamięci.|
|CLRDATA_ENUM|`typedef ULONG64 CLRDATA_ADDRESS;`|Niedostępne|64-bitowy adres pamięci.|
|Identyfikator połączenia|`typedef DWORD CONNID;`|CorDebug. h, mscoree. h|Identyfikator połączenia dla wątku, który jest połączony z wystąpieniem Microsoft SQL Server.|  
|Identyfikator ContextId|`typedef UINT_PTR ContextID;`|CorProf. h|Identyfikator kontekstu skojarzonego z określonym zarządzanym wątkiem.|  
|COR_PRF_ELT_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|CorProf. h|Nieprzezroczyste dojście, które reprezentuje informacje o określonej ramce stosu.|  
|COR_PRF_FRAME_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|CorProf. h|Nieprzezroczysty uchwyt, który wskazuje ramkę stosu. Jest on prawidłowy tylko w przypadku wywołania zwrotnego, do którego zostało przesłane.|  
|CORDB_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|CorDebug. h|Adres w pamięci.|  
|CORDB_CONTINUE_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|CorDebug. h|Stan kontynuacji.|  
|CORDB_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|CorDebug. h|Wartość rejestru procesora CPU.|
|FunctionID|`typedef UINT_PTR FunctionID;`|CorProf. h|Identyfikator funkcji lub metody.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|CorProf. h|Dojście do wyrzucania elementów bezużytecznych.|  
|mdMethodDef|`typedef mdToken mdMethodDef;`|CorDebug. h|Token definicji metody.|
|mdToken|`typedef UINT32 mdToken;`|CorProf. h|Token metadanych (wiersz w tabeli metadanych).|  
|ModuleID|`typedef UINT_PTR ModuleID;`|CorProf. h|Identyfikator modułu zestawu.|  
|Obiektu|`typedef UINT_PTR ObjectID;`|CorProf. h|Identyfikator obiektu.|  
|PCCOR_SIGNATURE|`typedef SIZE_T PCCOR_SIGNATURE;`|CorDebug. h|Wskaźnik do elementu członkowskiego lub sygnatury metadanych.|
|Identyfikator|`typedef UINT_PTR ProcessID;`|CorProf. h|Identyfikator procesu zarządzanego.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|CorProf. h|Identyfikator funkcji trybie JIT.|  
|SIZE_T|`typedef ULONG_PTR SIZE_T;`|CorSym. h|Wskaźnik do 64-bitowego adresu pamięci.|
|TASKID|`typedef UINT64 TASKID;`|CorDebug. h, mscoree. h|Identyfikator wystąpienia [ICLRTask](./hosting/iclrtask-interface.md) .|  
|ThreadID|`typedef UINT_PTR ThreadID;`|CorProf. h|Identyfikator wątku zarządzanego.|  
  
## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API — informacje](index.md)
