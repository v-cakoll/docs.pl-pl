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
ms.openlocfilehash: 058aa4891d05147756290affd60ea5fb260c33ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262955"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a>Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego "\<assembly1 >" z powodu pośredniego odwołania do tego zestawu z zestawu "\<assembly2 >"
Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego "\<assembly1 >" z powodu pośredniego odwołania do tego zestawu z zestawu "\<assembly2 >". Rozważ zmianę właściwości "Embed Interop Types" na jednym z zestawów.  
  
 Dodano odwołanie do zestawu (assembly1), który ma `Embed Interop Types` właściwością `True`. To powoduje, że kompilator, aby osadzić typu międzyoperacyjnego informacje z tego zestawu. Jednak kompilator nie można osadzić typu międzyoperacyjnego informacje z tego zestawu, ponieważ także innego zestawu, że masz przywoływane (zależność assembly2) odwołuje się do tego zestawu (assembly1) i ma `Embed Interop Types` właściwością `False`.  
  
> [!NOTE]
>  Ustawienie `Embed Interop Types` właściwość odwołanie do zestawu `True` jest odpowiednikiem odwołanie do zestawu przy użyciu `/link` opcję kompilatora wiersza polecenia.  
  
 **Identyfikator błędu:** BC40059  
  
### <a name="to-address-this-warning"></a>Aby rozwiązać tego ostrzeżenia  
  
-   Aby osadzić typu międzyoperacyjnego informacje dla obu zestawów, należy ustawić `Embed Interop Types` właściwość wszystkie odwołania do assembly1 do `True`.  
  
-   Aby usunąć to ostrzeżenie, można ustawić `Embed Interop Types` właściwość assembly1 do `False`. W tym przypadku typu międzyoperacyjnego informacje są udostępniane przez podstawowego zestawu międzyoperacyjnego (PIA).  
  
## <a name="see-also"></a>Zobacz także
- [/ Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
