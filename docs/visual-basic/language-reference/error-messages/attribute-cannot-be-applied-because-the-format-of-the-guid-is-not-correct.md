---
title: '&#39;&lt;atrybut&gt; &#39; nie można zastosować, ponieważ format identyfikatora GUID &#39; &lt;numer&gt; &#39; jest nieprawidłowy'
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 85b8c9dcccbb307d8a744e33a5f1d4b1775fda04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623668"
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;atrybut&gt; &#39; nie można zastosować, ponieważ format identyfikatora GUID &#39; &lt;numer&gt; &#39; jest nieprawidłowy
A `COMClassAttribute` bloku attribute określa unikatowy identyfikator globalny (GUID), który jest niezgodny ze odpowiedni format identyfikatora GUID. `COMClassAttribute` używa identyfikatorów GUID do unikatowego identyfikowania tej klasy, interfejsu i zdarzenie tworzenia.  
  
 Identyfikator GUID składa się z 16-bajtowy, z których pierwszych osiem to liczbowe, a ostatnie 8 to: binary. Ona jest generowany przez narzędzia firmy Microsoft, takie jak uuidgen.exe i jest musi być unikatowy w miejsce i czas.  
  
 **Identyfikator błędu:** BC32500  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ prawidłowy identyfikator GUID lub identyfikatory GUID niezbędne do identyfikowania obiektów COM.  
  
2.  Upewnij się, wyświetlone dla ciągów GUID `COMClassAttribute` bloku attribute zostały prawidłowo skopiowane.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Guid>
- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)

