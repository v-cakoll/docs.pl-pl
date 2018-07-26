---
title: 'Porada: generowanie zestawów międzyoperacyjnych z bibliotek typów'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62d9213e58aaabd0b4001d5c6a7fd6fd375eba2e
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874861"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Porada: generowanie zestawów międzyoperacyjnych z bibliotek typów
[Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) jest narzędziem wiersza polecenia, który konwertuje klasy coclass i interfejsy zawarte w bibliotece typów modelu COM w metadanych. To narzędzie automatycznie tworzy zestaw międzyoperacyjny i przestrzeni nazw, aby uzyskać informacje o typie. Po udostępnieniu metadanych klas zarządzanych klientów można tworzenia wystąpień tego typu COM i wywołać jego metody tak, jakby był to wystąpienie programu .NET. Tlbimp.exe konwertuje metadanych całej biblioteki typów na raz i nie można wygenerować informacji o typie dla podzbioru typów zdefiniowanych w bibliotece typów.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Do generowania zestawu międzyoperacyjnego z biblioteki typów  
  
1.  Użyj następującego polecenia:  
  
     **tlbimp** \< *pliku biblioteki typów*>  
  
     Dodawanie **/out:** przełącznika tworzy zestaw międzyoperacyjny nazwą zmieniony, takich jak LOANLib.dll. Zmienianie nazwy zestawu międzyoperacyjnego może pomóc odróżnić go od oryginalnego DLL modelu COM i uniemożliwić problemy, które mogą wystąpić o takich samych nazwach.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie generuje zestaw Loanlib.dll na `Loanlib` przestrzeni nazw.  
  
```  
tlbimp Loanlib.tlb  
```  
  
 Następujące polecenie generuje zestaw międzyoperacyjny nazwą zmienionego (LOANLib.dll).  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie biblioteki typów jako zestawu](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [Udostępnianie składników COM programowi .NET Framework](../../../docs/framework/interop/exposing-com-components.md)
