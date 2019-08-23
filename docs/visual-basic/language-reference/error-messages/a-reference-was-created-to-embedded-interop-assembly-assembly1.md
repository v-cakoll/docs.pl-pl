---
title: Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego „<assembly1>" z powodu pośredniego odwołania do tego zestawu z zestawu „<assembly2>".
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: 0f7a136abb0e63e4b139b87c8f18ae3fcb99dbf9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947754"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a>Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego '\<assembly1 >' z powodu pośredniego odwołania do tego zestawu z zestawu '\<assembly2 >'
Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego '\<assembly1 >' z powodu pośredniego odwołania do tego zestawu z zestawu '\<assembly2 >'. Rozważ zmianę właściwości 'Embed Interop Types' na jednym z zestawów.  
  
 Dodano odwołanie do zestawu (assembly1), który ma `Embed Interop Types` Właściwość ustawioną na. `True` Powoduje to, że kompilator osadzi informacje o typie międzyoperacyjnym z tego zestawu. Jednak kompilator nie może osadzić informacji o typie międzyoperacyjnym z tego zestawu, ponieważ inny zestaw, do którego istnieje odwołanie (Assembly2) również odwołuje się do tego `Embed Interop Types` zestawu (assembly1 `False`) i ma właściwość ustawioną na.  
  
> [!NOTE]
> Ustawienie właściwości w odwołaniu do `True` zestawu jest równoważne odwołującemu się do zestawu przy użyciu `/link` opcji kompilatora wiersza polecenia. `Embed Interop Types`  
  
 **Identyfikator błędu:** BC40059  
  
### <a name="to-address-this-warning"></a>Aby rozwiązać ten komunikat ostrzegawczy  
  
- Aby osadzić informacje o typie międzyoperacyjnym dla obu zestawów `Embed Interop Types` , należy ustawić właściwość na wszystkie odwołania `True`do assembly1.  
  
- Aby usunąć ostrzeżenie, można ustawić `Embed Interop Types` Właściwość assembly1 na. `False` W takim przypadku informacje o typie międzyoperacyjnym są udostępniane przez podstawowy zestaw międzyoperacyjny (PIA).  
  
## <a name="see-also"></a>Zobacz także

- [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
