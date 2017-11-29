---
title: "Porada: generowanie zestawów międzyoperacyjnych z bibliotek typów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf56d33a791dd91614d5ae37e3568ef660696af7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Porada: generowanie zestawów międzyoperacyjnych z bibliotek typów
[Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) to narzędzie wiersza polecenia, który konwertuje klasy coclass i interfejsy zawartych w bibliotece typów COM do metadanych. To narzędzie automatycznie tworzy zestaw międzyoperacyjny i przestrzeń nazw dla informacji o typie. Po metadanych klasy jest dostępny, zarządzanych klientów można utworzyć wystąpienia typu COM i wywołanie jego metody, tak jakby był wystąpienia programu .NET. Tlbimp.exe jednocześnie konwertuje biblioteki typów całego metadanych i nie można wygenerować informacji o typie dla podzbioru z typów definiowanych w bibliotece typów.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Do generowania zestawu międzyoperacyjnego z biblioteki typów  
  
1.  Użyj następującego polecenia:  
  
     **tlbimp** \< *pliku biblioteki typów*>  
  
     Dodawanie **/out:** przełącznika tworzy zestaw międzyoperacyjny nazwą zmieniony, takich jak LOANLib.dll. Zmiana nazwy zestawu międzyoperacyjnego umożliwia odróżniający go od oryginalnego pliku DLL COM i uniemożliwić problemów, które mogą wystąpić o takich samych nazwach.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie spowoduje utworzenie zestawu Loanlib.dll w `Loanlib` przestrzeni nazw.  
  
```  
tlbimp Loanlib.dll  
```  
  
 Następujące polecenie spowoduje utworzenie zestawu międzyoperacyjnego o zmienionej nazwie (LOANLib.dll).  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie biblioteki typów jako zestawu](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [Udostępnianie składników modelu COM aplikacji .NET Framework](../../../docs/framework/interop/exposing-com-components.md)
