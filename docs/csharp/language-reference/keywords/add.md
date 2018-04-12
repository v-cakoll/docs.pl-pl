---
title: add (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cab77ad5a990cf85075455e347a4b1c02645af37
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="add-c-reference"></a>add (odwołanie w C#)
`add` Kontekstowe słowo kluczowe jest używane do definiowania akcesor zdarzenie niestandardowe, które jest wywoływane, gdy kod klienta subskrybuje Twojej [zdarzeń](../../../csharp/language-reference/keywords/event.md). Jeśli podasz niestandardowego `add` dostępu, należy również podać [Usuń](../../../csharp/language-reference/keywords/remove.md) metody dostępu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono zdarzenie, które ma niestandardowy `add` i [Usuń](../../../csharp/language-reference/keywords/remove.md) metody dostępu. Na przykład pełna, zobacz [porady: Implementowanie interfejsu zdarzenia](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 Zwykle nie trzeba podać własne niestandardowych metod dostępu zdarzeń. Metody dostępu, które są automatycznie generowane przez kompilator przy deklarowaniu zdarzenia są wystarczające dla większości scenariuszy.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)
