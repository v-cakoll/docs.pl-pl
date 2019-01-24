---
title: Wyrażenie zawiera typ &#39; &lt;typename&gt; &#39; który jest typem ograniczonym i nie może być używane do dostępu członków dziedziczonych po elemencie &#39;obiektu&#39; lub &#39;ValueType&#39;
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: d44b9a29f0848508d8cd814e857d9b01819ce7ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535960"
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>Wyrażenie zawiera typ &#39; &lt;typename&gt; &#39; który jest typem ograniczonym i nie może być używane do dostępu członków dziedziczonych po elemencie &#39;obiektu&#39; lub &#39;ValueType&#39;
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
