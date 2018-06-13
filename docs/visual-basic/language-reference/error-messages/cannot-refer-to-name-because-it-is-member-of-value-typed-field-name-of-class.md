---
title: Nie można odwołać się do &#39; &lt;nazwa&gt; &#39; , ponieważ jest elementem członkowskim pola &#39; &lt;nazwa&gt; &#39; klasy &#39; &lt;classname&gt; &#39;mającego &#39;System.MarshalByRefObject&#39; jako klasa podstawowa
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: f44d33c9d51148e6bbcfbf5db4dbc115101df1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586350"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Nie można odwołać się do &#39; &lt;nazwa&gt; &#39; , ponieważ jest elementem członkowskim pola &#39; &lt;nazwa&gt; &#39; klasy &#39; &lt;classname&gt; &#39;mającego &#39;System.MarshalByRefObject&#39; jako klasa podstawowa
`System.MarshalByRefObject` Klasa umożliwia aplikacji, które obsługują zdalny dostęp do obiektów poza granice domeny aplikacji. Typy musi dziedziczyć z `MarshalByRejectObject` klasy, gdy typ jest używany przez granice domeny aplikacji. Nie można skopiować stan obiektu, ponieważ w elementach członkowskich obiektu nie są użyteczne spoza domeny aplikacji, w którym zostały utworzone.  
  
 **Identyfikator błędu:** BC30310  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź odwołania do upewnij się, że element członkowski jest określana jest prawidłowy.  
  
2.  Jawnie zakwalifikować element członkowski o `Me` — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.MarshalByRefObject>  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
