---
title: Wyrażenie zawiera typ „<typename>”, który jest typem ograniczonym i nie można go używać do uzyskiwania dostępu do członków dziedziczonych po elemencie „Object” lub „ValueType”.
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 6d2edadc323994f7f25394321fb1aff18f7154c5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824276"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a>Wyrażenie zawiera typ "\<typename >" który jest typem ograniczonym i nie może być używane do dostępu członków dziedziczonych po elemencie "Object" lub "ValueType"
Wyrażenie obliczane do typu, który nie może zostać opakowany przez środowisko uruchomieniowe języka wspólnego (CLR), ale uzyskuje dostęp do składowej, która wymaga opakowania.  
  
 *Konwersja boxing* odnosi się do przetwarzania niezbędne w celu konwersji typu do `Object` lub, czasami <xref:System.ValueType>. Środowisko uruchomieniowe języka wspólnego nie polu na przykład niektóre typy struktury <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, i <xref:System.TypedReference>.  
  
 To wyrażenie podejmują próbę użycia w typie ograniczonym do wywołania metody dziedziczone z <xref:System.Object> lub <xref:System.ValueType>, takich jak <xref:System.Object.GetHashCode%2A> lub <xref:System.Object.ToString%2A>. Aby uzyskać dostęp do tej metody, Visual Basic została podjęta próba konwersji niejawnej konwersji boxing, która powoduje występowanie tego błędu.  
  
 **Identyfikator błędu:** BC31393  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Znajdź wyrażenie obliczane do typu wspominane.  
  
2.  Znajdź część instrukcji, który próbuje wywołać metodę odziedziczone <xref:System.Object> lub <xref:System.ValueType>.  
  
3.  Napisz ponownie instrukcję, aby uniknąć wywołania metody.  
  
## <a name="see-also"></a>Zobacz także

- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
