---
title: "Porady: odwołania do typów .NET z modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b452dd686286ba0ddf648ee532e67a0c121f66eb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
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
 [Udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Rejestrowanie zestawów do użycia z modelem COM](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Wywołanie obiektu .NET.](http://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [Wdrażanie aplikacji na potrzeby dostępu modelu COM](http://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce)
