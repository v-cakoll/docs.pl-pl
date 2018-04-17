---
title: 'Porady: odwołania do typów .NET z modelu COM'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ac4308230f29067f358a45fd7f882abe6e41b96
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-reference-net-types-from-com"></a>Porady: odwołania do typów .NET z modelu COM
Z punktu widzenia kodu klienta i serwera różnice między COM i .NET Framework są przede wszystkim niewidoczne. Microsoft Visual Basic klientów można wyświetlić obiektu .NET. w przeglądarce obiektów, który udostępnia metody obiektu i składni, właściwości oraz polach dokładnie tak, jakby była innego obiektu COM.  
  
 Importowanie biblioteki typów jest nieco trudniejsze dla klientów C++, mimo że Eksportowanie metadanych do biblioteki typów COM za pomocą tych samych narzędzi. Aby odwołać elementy członkowskie programu .NET obiektu z niezarządzanego klienta C++, odwołania pliku TLB (realizowane z Tlbexp.exe) z **#import** dyrektywy. Podczas odwoływania się do biblioteki typów, z C++, należy określić **raw_interfaces_only —** opcji lub zaimportować definicje w bibliotece klasy podstawowej Mscorlib.tlb.  
  
### <a name="to-import-a-library"></a>Aby zaimportować bibliotekę  
  
-   Określ **raw_interfaces_only —** opcji **#import** dyrektywy. Na przykład:  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     —lub—  
  
-   Include — dyrektywa #import dla Mscorlib.tlb. Na przykład:  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)  
 [Rejestrowanie zestawów do użycia z modelem COM](registering-assemblies-with-com.md)  
 [Wywołanie obiektu .NET.](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))  
 [Wdrażanie aplikacji na potrzeby dostępu modelu COM](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))
