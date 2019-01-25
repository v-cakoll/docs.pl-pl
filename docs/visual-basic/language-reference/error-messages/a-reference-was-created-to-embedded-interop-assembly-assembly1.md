---
title: Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego &#39; &lt;assembly1&gt; &#39; z powodu pośredniego odwołania do tego zestawu z zestawu &#39; &lt;assembly2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: fe04742e0a3be5e1d19ab4017e55f2293988a671
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560025"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a>Utworzono odwołanie do osadzonego zestawu międzyoperacyjnego &#39; &lt;assembly1&gt; &#39; z powodu pośredniego odwołania do tego zestawu z zestawu &#39; &lt;assembly2&gt;&#39;
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
