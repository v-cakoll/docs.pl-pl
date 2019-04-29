---
title: 'Instrukcje: Odwołania do typów .NET z modelu COM'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e033ba4b3b98367452b355363058adc7f1a5887
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643026"
---
# <a name="how-to-reference-net-types-from-com"></a>Instrukcje: Odwołania do typów .NET z modelu COM
Z punktu widzenia kodu klienta i serwera różnice w modelu COM i .NET Framework są niewidoczne w dużej mierze. Klienci programu Microsoft Visual Basic można wyświetlić obiektu platformy .NET w przeglądarce obiektów, który udostępnia metody obiektu i składnię, właściwości i pola, dokładnie tak jak w przypadku dowolnego obiektu COM.  
  
 Proces importowania biblioteki typów jest nieco bardziej skomplikowanego dla klientów w języku C++, mimo że Eksportowanie metadanych do biblioteki typów COM za pomocą tych samych narzędzi. Aby odwołać elementach członkowskich obiektu .NET z niezarządzanego klienta języka C++, odwołaj się do TLB pliku (utworzone za pomocą Tlbexp.exe) za pomocą **#import** dyrektywy. Podczas odwoływania się do biblioteki typów z C++, należy określić **raw_interfaces_only —** opcję lub zaimportować definicje w bibliotece klasy bazowej Mscorlib.tlb.  
  
### <a name="to-import-a-library"></a>Aby zaimportować bibliotekę  
  
- Określ **raw_interfaces_only —** opcji **#import** dyrektywy. Na przykład:  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     —lub—  
  
- #Import — dyrektywa zawierają Mscorlib.tlb. Na przykład:  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)
- [Rejestrowanie zestawów do użycia z modelem COM](registering-assemblies-with-com.md)
- [Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [Wdrażanie aplikacji dla dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
