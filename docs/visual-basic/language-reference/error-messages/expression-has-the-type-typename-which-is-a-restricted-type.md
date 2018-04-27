---
title: Wyrażenie zawiera typ &#39; &lt;typename&gt; &#39; który jest typem ograniczonym i nie można uzyskać dostępu do członków dziedziczonych po elemencie &#39;obiektu&#39; lub &#39;ValueType&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab4e48c93a6a3c645bf9b5cc6c536d418022ae86
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>Wyrażenie zawiera typ &#39; &lt;typename&gt; &#39; który jest typem ograniczonym i nie można uzyskać dostępu do członków dziedziczonych po elemencie &#39;obiektu&#39; lub &#39;ValueType&#39;
Wyrażenie obliczane do typu, który nie może zostać opakowany przez środowisko uruchomieniowe języka wspólnego (CLR), ale uzyskuje dostęp do elementu członkowskiego, który wymaga opakowania.  
  
 *Konwersja boxing* odwołuje się do przetwarzania, które są niezbędne do przekonwertowania typu na `Object` lub czasem do <xref:System.ValueType>. Środowisko uruchomieniowe języka wspólnego nie polu na przykład niektóre typy struktur <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, i <xref:System.TypedReference>.  
  
 To wyrażenie odwołuje się do typie ograniczonym do wywołania metody dziedziczone z <xref:System.Object> lub <xref:System.ValueType>, takich jak <xref:System.Object.GetHashCode%2A> lub <xref:System.Object.ToString%2A>. Aby uzyskać dostęp do tej metody, Visual Basic próbował konwersji pakującej niejawne, która powoduje występowanie tego błędu.  
  
 **Identyfikator błędu:** BC31393  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Znajdź wyrażenie cytowane typ zwracanej wartości.  
  
2.  Znajdź część instrukcji, która podejmuje próbę wywołania metody odziedziczone <xref:System.Object> lub <xref:System.ValueType>.  
  
3.  Napisz ponownie instrukcję, aby uniknąć wywołania metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
