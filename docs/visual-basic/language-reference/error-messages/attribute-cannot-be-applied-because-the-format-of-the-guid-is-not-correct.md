---
title: '&#39;&lt;atrybut&gt; &#39; nie można zastosować, ponieważ format identyfikatora GUID &#39; &lt;numer&gt; &#39; jest nieprawidłowy'
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 93b208b2119942f939a3af223c2f562c6097f7a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;atrybut&gt; &#39; nie można zastosować, ponieważ format identyfikatora GUID &#39; &lt;numer&gt; &#39; jest nieprawidłowy
A `COMClassAttribute` bloku attribute określa globalnie unikatowy identyfikator (GUID), który jest niezgodny ze odpowiedni format identyfikatora GUID. `COMClassAttribute` używa identyfikatorów GUID do unikatowego identyfikowania klasy, interfejsu i tworzenia zdarzeń.  
  
 Identyfikator GUID składa się z 16 bajtów, które pierwszych osiem są numeryczne i ostatnich ośmiu binarnego. Jest generowany przez narzędzia firmy Microsoft, takich jak uuidgen.exe, a jest musi być unikatowy w miejsce i czas.  
  
 **Identyfikator błędu:** BC32500  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ prawidłowy identyfikator GUID lub identyfikatory GUID niezbędne do identyfikowania obiektów COM.  
  
2.  Przedstawić do ciągów GUID `COMClassAttribute` bloku attribute zostały prawidłowo skopiowane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Guid>  
[Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)

