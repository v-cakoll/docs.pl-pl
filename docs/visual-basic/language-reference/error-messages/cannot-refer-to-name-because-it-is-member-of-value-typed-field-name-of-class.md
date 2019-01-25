---
title: Nie można odwołać się &#39; &lt;nazwa&gt; &#39; , ponieważ jest to składowa pola &#39; &lt;nazwa&gt; &#39; klasy &#39; &lt;classname&gt; &#39;mającego &#39;System.MarshalByRefObject&#39; jako klasę bazową
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: a6298c3e0f5102397d5cc3f237a186598c6b5ecc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739300"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Nie można odwołać się &#39; &lt;nazwa&gt; &#39; , ponieważ jest to składowa pola &#39; &lt;nazwa&gt; &#39; klasy &#39; &lt;classname&gt; &#39;mającego &#39;System.MarshalByRefObject&#39; jako klasę bazową
`System.MarshalByRefObject` Klasa umożliwia aplikacji, które obsługują zdalny dostęp do obiektów poza granice domeny aplikacji. Typy musi dziedziczyć `MarshalByRejectObject` klasy, gdy typ jest używany poza granice domeny aplikacji. Nie można skopiować stan obiektu, ponieważ elementy członkowskie obiektu nie są użyteczne spoza domeny aplikacji, w którym zostały utworzone.  
  
 **Identyfikator błędu:** BC30310  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdzanie odwołania, aby upewnić się, że przywoływanego elementu członkowskiego jest nieprawidłowy.  
  
2.  Kwalifikuj jawnie elementu członkowskiego z `Me` — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.MarshalByRefObject>
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
