---
title: Assembly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 7ee6cddefd5955ee76510ffeb23335f05460657b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
Określa, że atrybut znajdujący się na początku pliku źródłowego dotyczy całego zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Wiele atrybutów odnoszą się do pojedynczego elementu programistycznego, takiego jak klasa lub właściwość. Zastosuj takiego atrybutu dołączając bloku atrybutów w nawiasy (`< >`), bezpośrednio do instrukcji deklaracji.  
  
 Jeśli atrybut dotyczy nie tylko do następującego elementu, ale do całego zestawu, umieść bloku attribute na początku pliku źródłowego i określenie atrybutu o `Assembly` — słowo kluczowe. Jeśli ma to zastosowanie do bieżącego zestawu modułu, użyj [modułu](../../../visual-basic/language-reference/modifiers/module-keyword.md) — słowo kluczowe.  
  
 Można również zastosować atrybut do zestawu w pliku AssemblyInfo.vb w takim przypadku nie trzeba w pliku głównym kodu źródłowego przy użyciu bloku atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 [Moduł \<— słowo kluczowe >](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)

