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
ms.openlocfilehash: f4f099dfaf5ff02edd3958d7eab9354ce727a239
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281805"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Porada: generowanie zestawów międzyoperacyjnych z bibliotek typów
[Importer biblioteki typów (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) jest narzędziem wiersza polecenia, które konwertuje klasy coclass i interfejsy zawarte w bibliotece typów modelu COM na metadane. To narzędzie tworzy zestaw międzyoperacyjny i przestrzeń nazw dla informacji o typie automatycznie. Po udostępnieniu metadanych klasy zarządzani klienci mogą tworzyć wystąpienia typu COM i wywoływać metody, tak jakby były wystąpieniem programu .NET. Tlbimp. exe konwertuje całą bibliotekę typów na metadane jednocześnie i nie może generować informacji o typie dla podzbioru typów zdefiniowanych w bibliotece typów.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Aby wygenerować zestaw międzyoperacyjny z biblioteki typów  
  
1. Użyj następującego polecenia:  
  
     **Tlbimp** \<— *typ biblioteki*>  
  
     Dodanie przełącznika **/out:** powoduje utworzenie zestawu międzyoperacyjnego o zmienionej nazwie, takiej jak LOANLib. dll. Zmiana nazwy zestawu międzyoperacyjnego może pomóc w odróżnieniu od oryginalnej biblioteki DLL modelu COM i zapobiec problemom, które mogą wystąpić w przypadku zduplikowanych nazw.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie generuje zestaw LOANLib. dll w `Loanlib` przestrzeni nazw.  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 Następujące polecenie tworzy zestaw międzyoperacyjny z zmienioną nazwą (LOANLib. dll).  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Zobacz też

- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
- [Udostępnianie składników COM programowi.NET Framework](exposing-com-components.md)
