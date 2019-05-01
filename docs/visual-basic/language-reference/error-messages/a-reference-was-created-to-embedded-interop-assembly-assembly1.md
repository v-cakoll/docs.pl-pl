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
ms.openlocfilehash: c0b4f56e3d1613486dd1198976557831ce657e1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774871"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a>Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego "\<assembly1 >" z powodu pośredniego odwołania do tego zestawu z zestawu "\<assembly2 >"
Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego "\<assembly1 >" z powodu pośredniego odwołania do tego zestawu z zestawu "\<assembly2 >". Rozważ zmianę właściwości "Embed Interop Types" na jednym z zestawów.  
  
 Dodano odwołanie do zestawu (assembly1), który ma `Embed Interop Types` właściwością `True`. To powoduje, że kompilator, aby osadzić typu międzyoperacyjnego informacje z tego zestawu. Jednak kompilator nie można osadzić typu międzyoperacyjnego informacje z tego zestawu, ponieważ także innego zestawu, że masz przywoływane (zależność assembly2) odwołuje się do tego zestawu (assembly1) i ma `Embed Interop Types` właściwością `False`.  
  
> [!NOTE]
>  Ustawienie `Embed Interop Types` właściwość odwołanie do zestawu `True` jest odpowiednikiem odwołanie do zestawu przy użyciu `/link` opcję kompilatora wiersza polecenia.  
  
 **Identyfikator błędu:** BC40059  
  
### <a name="to-address-this-warning"></a>Aby rozwiązać tego ostrzeżenia  
  
- Aby osadzić typu międzyoperacyjnego informacje dla obu zestawów, należy ustawić `Embed Interop Types` właściwość wszystkie odwołania do assembly1 do `True`.  
  
- Aby usunąć to ostrzeżenie, można ustawić `Embed Interop Types` właściwość assembly1 do `False`. W tym przypadku typu międzyoperacyjnego informacje są udostępniane przez podstawowego zestawu międzyoperacyjnego (PIA).  
  
## <a name="see-also"></a>Zobacz także

- [/ Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)
- [Współdziałanie z kodem niezarządzanym](../../../framework/interop/index.md)
