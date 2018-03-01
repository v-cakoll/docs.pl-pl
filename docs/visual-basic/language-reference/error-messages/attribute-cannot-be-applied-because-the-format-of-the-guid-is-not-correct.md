---
title: "&#39; &lt;atrybutu&gt;&#39; nie można zastosować, ponieważ format identyfikatora GUID &#39;&lt; Liczba&gt;&#39; jest niepoprawny"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ead07d12064dbe18a1e23d4d1343b1efba1b533
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39; &lt;atrybutu&gt;&#39; nie można zastosować, ponieważ format identyfikatora GUID &#39;&lt; Liczba&gt;&#39; jest niepoprawny
A `COMClassAttribute` bloku attribute określa globalnie unikatowy identyfikator (GUID), który jest niezgodny ze odpowiedni format identyfikatora GUID. `COMClassAttribute`używa identyfikatorów GUID do unikatowego identyfikowania klasy, interfejsu i tworzenia zdarzeń.  
  
 Identyfikator GUID składa się z 16 bajtów, które pierwszych osiem są numeryczne i ostatnich ośmiu binarnego. Jest generowany przez narzędzia firmy Microsoft, takich jak uuidgen.exe, a jest musi być unikatowy w miejsce i czas.  
  
 **Identyfikator błędu:** BC32500  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ prawidłowy identyfikator GUID lub identyfikatory GUID niezbędne do identyfikowania obiektów COM.  
  
2.  Przedstawić do ciągów GUID `COMClassAttribute` bloku attribute zostały prawidłowo skopiowane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Guid>  
[Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)

