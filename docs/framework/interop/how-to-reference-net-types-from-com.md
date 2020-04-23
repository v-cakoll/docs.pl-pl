---
title: 'Porady: odwołania do typów .NET z modelu COM'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
ms.openlocfilehash: 0223cb25b933cc84af49aa86d90259fdf1fd3efc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124172"
---
# <a name="how-to-reference-net-types-from-com"></a>Porady: odwołania do typów .NET z modelu COM
Z punktu widzenia kodu klienta i serwera różnice między modelem COM i .NET Framework są bardzo niewidoczne. Klienci programu Microsoft Visual Basic mogą wyświetlać obiekt .NET w przeglądarce obiektów, która udostępnia metody obiektu i składnię, właściwości i pola dokładnie tak, jakby były dowolnym innym obiektem COM.  
  
 Proces importowania biblioteki typów jest nieco bardziej skomplikowany dla klientów C++, chociaż te same narzędzia są używane do eksportowania metadanych do biblioteki typów COM. Aby odwołać się do elementów członkowskich obiektu platformy .NET z niezarządzanego klienta C++, odwołuje się do pliku TLB (utworzonego za pomocą Tlbexp. exe) z dyrektywą **#import** . W przypadku odwoływania się do biblioteki typów z C++ należy określić opcję **raw_interfaces_only** lub zaimportować definicje w bibliotece klas bazowych, mscorlib. tlb.  
  
### <a name="to-import-a-library"></a>Aby zaimportować bibliotekę  
  
- W dyrektywie **#import** określ opcję **raw_interfaces_only** . Przykład:  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     — lub —  
  
- Uwzględnij #import dyrektywę dla biblioteki mscorlib. tlb. Przykład:  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)
- [Rejestrowanie zestawów do użycia z modelem COM](registering-assemblies-with-com.md)
- [Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Wdrażanie aplikacji na potrzeby dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
