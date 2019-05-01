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
ms.openlocfilehash: 819fa9cf1bd25e9426fb1e75925a269fcf7a71cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801996"
---
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
Określa, że atrybut znajdujący się na początku pliku źródłowego dotyczy całego zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Wiele atrybutów odnoszą się do pojedynczego elementu programistycznego, takiego jak klasa lub właściwość. Stosowanie takiego atrybutu, dołączając bloku atrybutów w nawiasach kątowych (`< >`), bezpośrednio do instrukcji deklaracji.  
  
 Jeśli atrybut dotyczy nie tylko do następującego elementu, ale aby cały zespół, umieść bloku attribute na początku pliku źródłowego i określenie atrybutu o `Assembly` — słowo kluczowe. Jeśli ma zastosowanie do bieżącego zestawu modułu, należy użyć [modułu](../../../visual-basic/language-reference/modifiers/module-keyword.md) — słowo kluczowe.  
  
 Można również zastosować atrybut do zestawu w pliku AssemblyInfo.vb, w którym to przypadku nie trzeba użyć bloku atrybutów w pliku głównym kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz także

- [Module \<słowo kluczowe>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)
